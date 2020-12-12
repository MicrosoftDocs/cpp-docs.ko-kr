---
description: '자세한 정보: 다른 .NET 언어와의 상호 운용성 (c + +/CLI)'
title: 다른 .NET 언어와의 상호 운용성(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- C++, indexers
- indexers, consuming C#
- as C# keyword [C++]
- is C# keyword [C++]
- lock statement
- lock C# keyword [C++]
ms.assetid: a5902cf8-a14d-4559-aefb-c178615d45bb
ms.openlocfilehash: 51cead7fcc7dedc05f0225facf10fe70a3d606fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316611"
---
# <a name="interoperability-with-other-net-languages-ccli"></a>다른 .NET 언어와의 상호 운용성(C++/CLI)

이 단원의 항목에서는를 사용 하거나 c # 또는 Visual Basic로 작성 된 어셈블리에 기능을 제공 하는 Visual C++에서 어셈블리를 만드는 방법을 보여 줍니다.

## <a name="consume-a-c-indexer"></a><a name="consume_indexer"></a> C # 인덱서 사용

Visual C++에 인덱서가 없습니다. 인덱싱된 속성이 있습니다. C # 인덱서를 사용 하려면 인덱싱된 속성인 것 처럼 인덱서에 액세스 합니다.

인덱서에 대 한 자세한 내용은 다음을 참조 하세요.

- [인덱서](/dotnet/csharp/programming-guide/indexers/index)

### <a name="example"></a>예제

다음 c # 프로그램은 인덱서를 정의 합니다.

```csharp
// consume_cs_indexers.cs
// compile with: /target:library
using System;
public class IndexerClass {
   private int [] myArray = new int[100];
   public int this [int index] {   // Indexer declaration
      get {
         // Check the index limits.
         if (index < 0 || index >= 100)
            return 0;
         else
            return myArray[index];
      }
      set {
         if (!(index < 0 || index >= 100))
            myArray[index] = value;
      }
   }
}
/*
// code to consume the indexer
public class MainClass {
   public static void Main() {
      IndexerClass b = new IndexerClass();

      // Call indexer to initialize elements 3 and 5
      b[3] = 256;
      b[5] = 1024;
      for (int i = 0 ; i <= 10 ; i++)
         Console.WriteLine("Element #{0} = {1}", i, b[i]);
   }
}
*/
```

### <a name="example"></a>예제

이 Visual C++ 프로그램은 인덱서를 사용 합니다.

```cpp
// consume_cs_indexers_2.cpp
// compile with: /clr
#using "consume_cs_indexers.dll"
using namespace System;

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->default[0] = 21;
   for (int i = 0 ; i <= 10 ; i++)
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);
}
```

```Output
Element #0 = 21
Element #1 = 0
Element #2 = 0
Element #3 = 0
Element #4 = 0
Element #5 = 0
Element #6 = 0
Element #7 = 0
Element #8 = 0
Element #9 = 0
Element #10 = 0
```

## <a name="implement-is-and-as-c-keywords"></a><a name="implement_isas"></a> Is 및 as c # 키워드 구현

이 항목에서는 `is` `as` Visual C++에서 및 c # 키워드의 기능을 구현 하는 방법을 보여 줍니다.

### <a name="example"></a>예제

```cpp
// CS_is_as.cpp
// compile with: /clr
using namespace System;

interface class I {
public:
   void F();
};

ref struct C : public I {
   virtual void F( void ) { }
};

template < class T, class U >
Boolean isinst(U u) {
   return dynamic_cast< T >(u) != nullptr;
}

int main() {
   C ^ c = gcnew C();
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)

   // simulate 'as':
   Object ^ o = "f";
   if ( isinst< String ^ >(o) )
      Console::WriteLine("o is a string");
}
```

```Output
o is a string
```

## <a name="implement-the-lock-c-keyword"></a><a name="implement_locak"></a> Lock c # 키워드 구현

이 항목에서는 Visual C++에서 c # 키워드를 구현 하는 방법을 보여 줍니다 `lock` .

`lock`C + + 지원 라이브러리에서 클래스를 사용할 수도 있습니다. 자세한 내용은 [동기화 (Lock 클래스)](../dotnet/synchronization-lock-class.md) 를 참조 하세요.

### <a name="example"></a>예제

```cpp
// CS_lock_in_CPP.cpp
// compile with: /clr
using namespace System::Threading;
ref class Lock {
   Object^ m_pObject;
public:
   Lock( Object ^ pObject ) : m_pObject( pObject ) {
      Monitor::Enter( m_pObject );
   }
   ~Lock() {
      Monitor::Exit( m_pObject );
   }
};

ref struct LockHelper {
   void DoSomething();
};

void LockHelper::DoSomething() {
   // Note: Reference type with stack allocation semantics to provide
   // deterministic finalization

   Lock lock( this );
   // LockHelper instance is locked
}

int main()
{
   LockHelper lockHelper;
   lockHelper.DoSomething();
   return 0;
}
```

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

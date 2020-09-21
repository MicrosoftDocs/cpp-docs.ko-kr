---
title: 컴파일러 오류 C2039
ms.date: 11/04/2016
f1_keywords:
- C2039
helpviewer_keywords:
- C2039
ms.assetid: f9dfd521-9b36-4454-a69c-d63f45b606bb
ms.openlocfilehash: 6dc79db11f08ce00cdb86e930173c052cd5187ed
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742686"
---
# <a name="compiler-error-c2039"></a>컴파일러 오류 C2039

' identifier1 ': ' identifier2 '의 멤버가 아닙니다.

코드에서를 잘못 호출 하거나 구조체, 클래스 또는 공용 구조체의 멤버를 참조 하는 경우

## <a name="examples"></a>예제

다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039.cpp
struct S {
   int mem0;
} s, *pS = &s;

int main() {
   pS->mem1 = 0;   // C2039 mem1 is not a member
   pS->mem0 = 0;   // OK
}
```

다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039_b.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine( "{0}", DateTime::get_Now());   // C2039
   Console::WriteLine( "{0}", DateTime::Now);   // OK
   Console::WriteLine( "{0}", DateTime::Now::get());   // OK
}
```

다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039_c.cpp
// compile with: /clr /c
ref struct S {
   property int Count {
     int get();
     void set(int i){}
   };
};

int S::get_Count() { return 0; }   // C2039
int S::Count::get() { return 0; }   // OK
```

C2039는 기본 인덱서에 잘못 액세스 하려고 시도 하는 경우에도 발생할 수 있습니다. 다음 샘플에서는 c #으로 작성 된 구성 요소를 정의 합니다.

```
// C2039_d.cs
// compile with: /target:library
// a C# program
[System.Reflection.DefaultMember("Item")]
public class B {
   public int Item {
      get { return 13; }
      set {}
   }
};
```

다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039_e.cpp
// compile with: /clr
using namespace System;
#using "c2039_d.dll"

int main() {
   B ^ b = gcnew B;
   int n = b->default;   // C2039
   // try the following line instead
   // int n = b->Item;
   Console::WriteLine(n);
}
```

제네릭을 사용 하는 경우에도 C2039이 발생할 수 있습니다. 다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039_f.cpp
// compile with: /clr
interface class I {};

ref struct R : public I {
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f3();   // C2039
   safe_cast<R^>(t)->f3();   // OK
}

int main() {
   f(gcnew R());
}
```

C2039는 관리 되거나 관리 되지 않는 리소스를 해제 하려고 할 때 발생할 수 있습니다. 자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요.

다음 샘플에서는 C2039를 생성 합니다.

```cpp
// C2039_g.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   ((IDisposable ^)stateTimer)->Dispose();   // C2039

   stateTimer->~Timer();   // OK
}
```

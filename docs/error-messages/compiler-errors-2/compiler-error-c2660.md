---
title: 컴파일러 오류 C2660
ms.date: 11/04/2016
f1_keywords:
- C2660
helpviewer_keywords:
- C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
ms.openlocfilehash: 179cdc6379fd26f5acd436d5ca6cacc08df8dce3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743245"
---
# <a name="compiler-error-c2660"></a>컴파일러 오류 C2660

' function ': 함수는 숫자 매개 변수를 사용 하지 않습니다.

함수는 잘못 된 개수의 매개 변수를 사용 하 여 호출 됩니다.

C2660는 동일한 이름의 MFC 멤버 함수가 아닌 Windows API 함수를 실수로 호출 하는 경우에 발생할 수 있습니다. 이 문제를 해결 하려면 다음을 수행 합니다.

- 멤버 함수 호출의 형식을 따르도록 함수 호출을 조정 합니다.

- 범위 확인 연산자 ()를 사용 `::` 하 여 컴파일러가 전역 이름 공간에서 함수 이름을 검색 하도록 지시할 수 있습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2660를 생성 합니다.

```cpp
// C2660.cpp
void func( int, int ) {}

int main() {
   func( 1 );   // C2660 func( int ) not declared
   func( 1, 0 );   // OK
}
```

C2660는 관리 되는 형식의 Dispose 메서드를 직접 호출 하려고 하는 경우에도 발생할 수 있습니다. 자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)를 참조 하세요. 다음 샘플에서는 C2660를 생성 합니다.

```cpp
// C2660_a.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   stateTimer->Dispose();   // C2660
   stateTimer->~Timer();   // OK
}
```

파생 클래스가 함수를 숨기면 C2660이 발생 합니다.

```cpp
// C2660b.cpp
// C2660 expected
#include <stdio.h>

class f {
public:
   void bar() {
      printf_s("in f::bar\n");
    }
};

class f2 : public f {
public:
   void bar(int i){printf("in f2::bar\n");}
   // Uncomment the following line to resolve.
   // using f::bar;   // - using declaration added
   // or
   // void bar(){__super::bar();}
};

int main() {
   f2 fObject;
   fObject.bar();
}
```

인덱싱된 속성을 잘못 호출 하는 경우 C2660이 발생할 수 있습니다.

```cpp
// C2660c.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(1.9) {}
   property double MyProp[] {
      double get(int i) {
         return d;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   System::Console::WriteLine(MyX->MyProp(1));   // C2660
   System::Console::WriteLine(MyX->MyProp[1]);   // OK
}
```

인덱싱된 속성을 잘못 호출 하는 경우 C2660이 발생할 수 있습니다.

```cpp
// C2660d.cpp
// compile with: /clr
ref class A{
public:
   property int default[int,int] {
      int get(int a, int b) {
         return a + b;
      }
   }
};

int main() {
   A^ a = gcnew A;
   int x = a[3][5];   // C2660
   int x2 = a[3,5];   // OK
}
```

템플릿 클래스에서 new 연산자를 정의 하는 경우 C2660이 발생할 수 있지만 new 연산자는 바깥쪽 형식이 아닌 다른 형식의 개체를 만듭니다.

```cpp
// C2660e.cpp
// compile with: /c
#include <malloc.h>

template <class T> class CA {
private:
    static T** line;
   void* operator new (size_t, int i) {
      return 0;
   }
   void operator delete(void* pMem, int i) {
      free(pMem);
   }

public:
   CA () { new (1) T(); }   // C2660
   // try the following line instead
   // CA () { new (1) CA<int>(); }
};

typedef CA <int> int_CA;

void AAA() {
   int_CA  list;
}
```

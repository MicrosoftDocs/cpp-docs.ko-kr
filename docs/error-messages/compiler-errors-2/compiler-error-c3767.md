---
description: '자세한 정보: 컴파일러 오류 C3767'
title: 컴파일러 오류 C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: 6d8780dde6ba6d831b1e47c174ef3609086c46ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291846"
---
# <a name="compiler-error-c3767"></a>컴파일러 오류 C3767

' function ' 후보 함수에 액세스할 수 없습니다.

클래스에 정의 된 friend 함수는 전역 네임 스페이스 범위에서 정의 되 고 선언 된 것 처럼 처리 되지 않습니다. 그러나 인수 종속 조회를 통해 찾을 수 있습니다.

C3767은 주요 변경 내용으로 인해 발생할 수도 있습니다. 이제 네이티브 형식이 **/clr** 컴파일에서 기본적으로 private입니다. 자세한 내용은 [형식 표시 유형](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3767를 생성 합니다.

```cpp
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

다음 샘플에서는 C3767를 생성 합니다.

```cpp
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

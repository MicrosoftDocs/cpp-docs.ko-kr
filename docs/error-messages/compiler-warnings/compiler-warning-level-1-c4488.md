---
title: 컴파일러 경고 (수준 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c3d176d034e679f3cca145ccb2fc77cc7fa64f3d
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965566"
---
# <a name="compiler-warning-level-1-c4488"></a>컴파일러 경고 (수준 1) C4488

' function ': 인터페이스 메서드 ' interface_method '을 (를) 구현 하려면 ' keyword ' 키워드가 필요 합니다.

클래스는 직접 상속 되는 인터페이스의 모든 멤버를 구현 해야 합니다. 구현 된 멤버는 공용 액세스 가능성을 가져야 하며 가상으로 표시 되어야 합니다.

## <a name="example"></a>예제

C4488는 구현 된 멤버가 public이 아닌 경우에 발생할 수 있습니다. 다음 샘플에서는 C4488를 생성 합니다.

```cpp
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>예제

구현 된 멤버가 virtual로 표시 되지 않은 경우 C4488이 발생할 수 있습니다. 다음 샘플에서는 C4488를 생성 합니다.

```cpp
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```
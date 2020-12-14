---
description: '자세한 정보: 컴파일러 오류 C3797'
title: 컴파일러 오류 C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 581dae7ba2649d72fc2670b99c9255b3ee9f7838
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244864"
---
# <a name="compiler-error-c3797"></a>컴파일러 오류 C3797

' override ': 이벤트 선언에는 재정의 지정자를 사용할 수 없습니다. 대신 이벤트 추가/제거/발생 메서드에 배치 해야 합니다.

다른 trivial 이벤트를 사용 하 여 trivial 이벤트 (명시적으로 정의 된 접근자 메서드가 없는 이벤트)를 재정의할 수 없습니다. 재정의 하는 이벤트는 접근자 함수를 사용 하 여 해당 동작을 정의 해야 합니다.

자세한 내용은 [이벤트](../../extensions/event-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3797를 생성 합니다.

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```

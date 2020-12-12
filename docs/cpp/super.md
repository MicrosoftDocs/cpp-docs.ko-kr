---
description: 다음에 대해 자세히 알아보세요. `__super`
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: 30f2733abbd4599deabfa989d72b099c929cb050
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178136"
---
# `__super`

**Microsoft 전용**

재정의하는 함수에 대한 기본 클래스 구현을 호출하고 있음을 명시적으로 나타낼 수 있도록 합니다.

## <a name="syntax"></a>구문

```
__super::member_function();
```

## <a name="remarks"></a>설명

액세스할 수 있는 모든 기본 클래스 메서드가 오버로드 확인 단계에서 고려되고 가장 일치하는 함수가 호출되는 함수입니다.

**`__super`** 멤버 함수의 본문 내에만 표시 될 수 있습니다.

**`__super`** using 선언과 함께 사용할 수 없습니다. 자세한 내용은 [선언 사용](../cpp/using-declaration.md) 을 참조 하세요.

코드를 삽입 하는 [특성](../windows/attributes/attributes-alphabetical-reference.md) 의 도입으로, 코드에는 이름이 몰라도 호출할 메서드를 포함 하는 기본 클래스를 하나 이상 포함할 수 있습니다.

## <a name="example"></a>예제

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)

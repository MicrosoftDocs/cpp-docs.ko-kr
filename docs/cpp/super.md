---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: 778ed2d80aa926c7282073a99898a6aa355a3379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602620"
---
# <a name="super"></a>__super

**Microsoft 전용**

재정의하는 함수에 대한 기본 클래스 구현을 호출하고 있음을 명시적으로 나타낼 수 있도록 합니다.

## <a name="syntax"></a>구문

```
__super::member_function();
```

## <a name="remarks"></a>설명

액세스할 수 있는 모든 기본 클래스 메서드가 오버로드 확인 단계에서 고려되고 가장 일치하는 함수가 호출되는 함수입니다.

**__super** 멤버 함수의 본문 내 에서만 사용할 수 있습니다.

**__super** 을 사용 하 여 사용할 수 없습니다. 선언 합니다. 참조 [선언을 사용 하 여](../cpp/using-declaration.md) 자세한 내용은 합니다.

되면서 [특성](../windows/cpp-attributes-reference.md) 코드를 삽입 하는, 코드는 호출 하려는 메서드를 포함 하는 이름이 해당 모를 수 있습니다 하나 이상의 기본 클래스가 포함 될 수 있습니다.

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

## <a name="see-also"></a>참고자료

[키워드](../cpp/keywords-cpp.md)
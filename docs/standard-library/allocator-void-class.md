---
title: allocator&lt;void&gt; 클래스
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204933"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 클래스

형식에 대 한 클래스 템플릿 할당자의 특수화 **`void`** 로,이 컨텍스트에서 적합 한 형식을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>설명

클래스는 형식에 대 한 클래스 템플릿 [할당자](allocator-class.md) 를 명시적으로 특수화 **`void`** 합니다. 생성자와 대입 연산자는 클래스 템플릿과 동일 하 게 동작 하지만 다음 유형만 정의 합니다.

- [const_pointer](allocator-class.md#const_pointer).

- [포인터](allocator-class.md#pointer).

- [value_type](allocator-class.md#value_type).

- 다시 [바인딩](allocator-class.md#rebind)중첩 된 클래스 템플릿입니다.

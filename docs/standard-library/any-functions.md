---
description: '자세히 알아보기: &lt; 모든 &gt; 함수'
title: '&lt;any &gt; 함수'
ms.date: 04/04/2019
f1_keywords:
- any/std::any_cast
- any/std::make_any
- any/std::swap
ms.openlocfilehash: 03f699ac5c48962bb32a604a885bc0b3c60c8b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163394"
---
# <a name="ltanygt-functions"></a>&lt;any &gt; 함수

## <a name="any_cast"></a><a name="any_cast"></a> any_cast

개체를 any로 만듭니다.

```cpp
template<class T>
    T any_cast(const any& operand);
template<class T>
    T any_cast(any& operand);
template<class T>
    T any_cast(any&& operand);
template<class T>
    const T* any_cast(const any* operand) noexcept;
template<class T>
    T* any_cast(any* operand) noexcept;
```

## <a name="make_any"></a><a name="make_any"></a> make_any

값을 사용 하 고 모든 개체를 만듭니다.

```cpp
template <class T, class... Args>
    any make_any(Args&& ...args);
template <class T, class U, class... Args>
    any make_any(initializer_list<U> il, Args&& ...args);
```

## <a name="swap"></a><a name="swap"></a> 스왑을

두 개체의 요소를 교환 합니다.

```cpp
void swap(any& left, any& right) noexcept;
```

### <a name="parameters"></a>매개 변수

*비어*\
`any` 형식의 개체입니다.

*오른쪽*\
`any` 형식의 개체입니다.

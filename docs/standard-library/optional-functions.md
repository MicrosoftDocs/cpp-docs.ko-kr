---
description: '자세한 정보: &lt; 선택적 &gt; 함수'
title: '&lt;선택적 &gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- optional/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: d48329005b24b96a12a95e1d895319796bd41928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201913"
---
# <a name="ltoptionalgt-functions"></a>&lt;선택적 &gt; 함수

## <a name="make_optional"></a><a name="make_optional"></a> make_optional

개체를 선택적으로 만듭니다.

```cpp
template <class T>
    constexpr optional<see below> make_optional(T&&);
template <class T, class... Args>
    constexpr optional<T> make_optional(Args&&... args);
template <class T, class U, class... Args>
    constexpr optional<T> make_optional(initializer_list<U> il, Args&&... args);
```

## <a name="nullopt"></a><a name="nullopt"></a> nullopt

```cpp
inline constexpr nullopt_t nullopt(unspecified );
```

## <a name="swap"></a><a name="swap"></a> 스왑을

```cpp
template <class T>
    void swap(optional<T>&, optional<T>&) noexcept(see below );
```

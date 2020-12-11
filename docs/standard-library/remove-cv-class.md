---
description: Remove_cv 클래스에 대해 자세히 알아보세요.
title: remove_cv 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_cv
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
ms.openlocfilehash: 2842c250ef46bf4fe1d36e6159bfaaf09b872034
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159689"
---
# <a name="remove_cv-class"></a>remove_cv 클래스

형식에서 비 const/휘발성 형식을 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct remove_cv;

template <class T>
using remove_cv_t = typename remove_cv<T>::type;
```

### <a name="parameters"></a>매개 변수

*트*\
수정할 형식입니다.

## <a name="remarks"></a>설명

의 인스턴스는 `remove_cv<T>` `T1` *t* 가, 또는 형식인 경우 인 수정 된 형식을 보유 합니다 `const T1` `volatile T1` `const volatile T1` . 그렇지 않은 경우에는입니다.

## <a name="example"></a>예제

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_cv_t<const volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_cv_t<const volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_cv_t<const volatile int> == int
```

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)\
[remove_const 클래스](../standard-library/remove-const-class.md)\
[remove_volatile 클래스](../standard-library/remove-volatile-class.md)

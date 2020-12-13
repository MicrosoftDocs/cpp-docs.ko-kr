---
description: '다음에 대 한 자세한 정보: variant_alternative 구조체'
title: variant_alternative 구조체
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant_alternative
helpviewer_keywords:
- variant_alternative struct
ms.openlocfilehash: bbad42afa517c7f6ad46561a85c1b73e71041a57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337852"
---
# <a name="variant_alternative-struct"></a>variant_alternative 구조체

변형 개체를 지원 합니다.

## <a name="syntax"></a>구문

```cpp
template <size_t I, class T>
    struct variant_alternative; // not defined
template <size_t I, class T>
    struct variant_alternative<I, const T>;
template <size_t I, class T>
    struct variant_alternative<I, volatile T>;
template <size_t I, class T>
    struct variant_alternative<I, const volatile T>;
template <size_t I, class T>
    using variant_alternative_t = typename variant_alternative<I, T>::type;
template <size_t I, class... Types>
    struct variant_alternative<I, variant<Types...>>;
```

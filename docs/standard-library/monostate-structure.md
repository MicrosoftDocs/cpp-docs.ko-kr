---
description: '자세히 알아보기: monostate 구조체'
title: monostate 구조체
ms.date: 04/04/2019
f1_keywords:
- variant/std::monostate
helpviewer_keywords:
- monostate struct
ms.openlocfilehash: 93b21f399761970129a495590e0821aa911a0408
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115159"
---
# <a name="monostate-struct"></a>monostate 구조체

Monostate 클래스는 variant 형식의 대체 형식으로 사용 되어 variant 형식의 기본 생성 가능를 만듭니다.

## <a name="syntax"></a>구문

```cpp
struct monostate;

constexpr bool operator<(monostate, monostate) noexcept;
constexpr bool operator>(monostate, monostate) noexcept;
constexpr bool operator<=(monostate, monostate) noexcept;
constexpr bool operator>=(monostate, monostate) noexcept;
constexpr bool operator==(monostate, monostate) noexcept;
constexpr bool operator!=(monostate, monostate) noexcept;
```

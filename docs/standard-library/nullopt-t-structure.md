---
description: '다음에 대 한 자세한 정보: nullopt_t 구조체'
title: nullopt_t 구조체
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 7a597dcc5f15843f125dc7572dc4c5694320f0bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338112"
---
# <a name="nullopt_t-struct"></a>nullopt_t 구조체

`nullopt_t`형식은 [선택적](optional-class.md) 개체에 값이 포함 되지 않음을 나타내는 데 사용 되는 고유 하 고 빈 형식입니다.

형식의 상수는 `nullopt` `nullopt_t` 형식에 `optional` 초기화 되지 않은 상태가 있음을 나타냅니다. 개체를 초기화 `optional` 하거나 개체와 비교 하는 데 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>참고 항목

[\<optional>](optional.md)\
[선택적 클래스](optional-class.md)

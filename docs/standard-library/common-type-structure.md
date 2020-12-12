---
description: '다음에 대 한 자세한 정보: common_type 구조체'
title: common_type 구조체
ms.date: 11/04/2016
f1_keywords:
- chrono/std::common_type
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
ms.openlocfilehash: 09d0460235286cb1a08d2d06d6c5a5cba7500617
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325051"
---
# <a name="common_type-structure"></a>common_type 구조체

[기간](../standard-library/duration-class.md) 및 [time_point](../standard-library/time-point-class.md)인스턴스화에 대 한 클래스 템플릿 [common_type](../standard-library/common-type-class.md) 의 특수화를 설명 합니다.

## <a name="syntax"></a>Syntax

```cpp
template <class Rep1, class Period1,
    class Rep2, class Period2>
struct common_type
<chrono::duration<Rep1, Period1>,
chrono::duration<Rep2, Period2>>;

template <class Clock,
    class Duration1, class Duration2>
struct common_type
<chrono::time_point<Clock, Duration1>,
chrono::time_point<Clock, Duration2>>;
```

## <a name="requirements"></a>요구 사항

**헤더:**\<chrono>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)

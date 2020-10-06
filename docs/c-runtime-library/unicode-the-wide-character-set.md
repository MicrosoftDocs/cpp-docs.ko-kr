---
title: '유니코드: 와이드 문자 집합'
description: Microsoft C 런타임의 유니코드 와이드 문자 집합을 소개 합니다.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 7cd170ae43223f1e8e61d9fc576e49baa2164b23
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765339"
---
# <a name="unicode-the-wide-character-set"></a>유니코드: 와이드 문자 집합

와이드 문자는 2바이트 다국어 문자 코드입니다. 전 세계의 현대식 컴퓨팅 환경에서 사용되는 모든 문자(전문 기호 및 특수 출판 문자 포함)는 유니코드 지정에 따라 와이드 문자로 표현될 수 있습니다. Microsoft를 포함하는 대규모 컨소시엄을 통해 개발 및 유지되고 있는 유니코드 표준은 이제 널리 인정된 표준입니다.

와이드 문자는 형식입니다 **`wchar_t`** . 와이드 문자열은 배열로 표시 됩니다 **`wchar_t[]`** . 포인터를 사용 하 여 배열을 가리킵니다 `wchar_t*` .

문자를 접두사로 하 여 와이드 문자로 ASCII 문자를 나타낼 수 있습니다 `L` . 예를 들어 `L'\0'` 는 종료 와이드 (16 비트) null 문자입니다.

문자 앞에 문자를 접두사로 하 여 ASCII 문자열 리터럴을 와이드 문자열 리터럴로 나타낼 수 있습니다 `L` . 예들 들어 `L"Hello"`입니다.

일반적으로 와이드 문자는 멀티 바이트 문자 보다 메모리 공간을 더 많이 사용 합니다. 그러나 와이드 문자를 처리 하는 것이 더 빠릅니다. 멀티 바이트 인코딩의 한 번에 하나의 로캘로 표현할 수 있습니다. 전 세계의 모든 문자 집합은 유니코드 표현으로 동시에 표시 됩니다.

## <a name="see-also"></a>참조

[국제화](../c-runtime-library/internationalization.md)\
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)

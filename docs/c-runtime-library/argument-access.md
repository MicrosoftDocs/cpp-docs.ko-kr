---
title: 인수 액세스
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470410"
---
# <a name="argument-access"></a>인수 액세스

**va_arg**, **va_end** 및 **va_start** 매크로는 인수의 수가 가변적인 경우 함수 인수에 대한 액세스를 제공합니다. 이러한 매크로는 ANSI/ISO C 호환성에 대해 \<stdarg.h>에 정의되며, UNIX 시스템 V와의 호환성에 대해 \<varargs.h>에 정의됩니다.

## <a name="argument-access-macros"></a>인수 액세스 매크로

|매크로|사용|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|목록에서 인수 검색|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|포인터 다시 설정|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|포인터를 인수 목록의 시작 부분으로 설정|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)

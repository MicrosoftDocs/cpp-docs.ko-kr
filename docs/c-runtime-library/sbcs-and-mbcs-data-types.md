---
title: SBCS 및 MBCS 데이터 형식
description: Microsoft C 런타임에 단일 및 멀티 바이트 문자를 표시 하는 방법입니다.
ms.topic: conceptual
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 27d32ffd079cdc82ab8a799df9d9ec778b546a3b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590253"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 및 MBCS 데이터 형식

단일 멀티 바이트 문자 또는 1 바이트의 멀티 바이트 문자만 처리 하는 모든 Microsoft MBCS 런타임 라이브러리 루틴에는 **`unsigned int`** 인수가 필요 합니다. 여기서 0x00 <= 문자 값 <= 0xffff 및 0x00 <= 바이트 값 <= 0xff). 문자열 컨텍스트에서 멀티 바이트 바이트 또는 문자를 처리 하는 MBCS 루틴은 멀티 바이트 문자열을 포인터로 표현 해야 **`unsigned char`** 합니다.

> [!CAUTION]
> 멀티 바이트 문자의 각 바이트는 8 비트로 표현 될 수 있습니다 **`char`** . 그러나 값이 0x7F 보다 큰 형식의 SBCS 또는 MBCS 싱글바이트 문자 **`char`** 는 음수입니다. 이러한 문자가 또는로 직접 변환 되는 경우 **`int`** **`long`** 결과는 컴파일러에 의해 부호 확장 되므로 예기치 않은 결과를 생성할 수 있습니다.

멀티 바이트 문자의 바이트를 8 비트로 표현 하는 것이 가장 좋습니다 **`unsigned char`** . 또는 음수 결과를 방지 하려면 형식의 단일 바이트 문자를로 변환 하기 전에 해당 문자를로 변환 **`char`** **`unsigned char`** **`int`** **`long`** 합니다.

일부 SBCS 문자열 처리 함수는 (부호 있는) **`char`** <strong>\*</strong> 매개 변수를 사용 하므로 **_MBCS** 정의 될 때 형식 불일치 컴파일러 경고가 발생 합니다. 이 경고를 피하기 위한 세 가지 방법이 유용성 순서대로 나열됩니다.

1. TCHAR.H에 형식이 안전한 인라인 함수를 사용합니다. 이것은 기본적인 동작입니다.

1. 명령줄에서 **_MB_MAP_DIRECT**를 정의하여 TCHAR.H에 직접 매크로를 사용합니다. 이렇게 하는 경우 형식을 수동으로 일치시켜야 합니다. 이는 속도가 가장 빠른 방법 이지만 형식이 안전 하지 않습니다.

1. TCHAR.H에 형식이 안전한 정적 링크 라이브러리 함수를 사용합니다. 이렇게 하려면 명령줄에서 **_NO_INLINING** 상수를 정의합니다. 이는 속도가 가장 느린 방법이지만 형식은 가장 안전합니다.

## <a name="see-also"></a>참고 항목

[국제화](../c-runtime-library/internationalization.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>

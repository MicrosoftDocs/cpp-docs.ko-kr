---
description: '자세히 알아보기: 하드웨어 예외'
title: 하드웨어 예외
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 3fccda4f23aa260f737f81e877d2ea9d673ebafe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268719"
---
# <a name="hardware-exceptions"></a>하드웨어 예외

운영 체제에서 인식하는 대부분의 표준 예외는 하드웨어 정의 예외입니다. Windows는 몇몇 하위 수준의 소프트웨어 예외를 인식하지만 이러한 예외는 보통 운영 체제에서 잘 처리됩니다.

Windows는 다른 프로세서의 하드웨어 오류를 이 섹션의 예외 코드로 매핑합니다. 경우에 따라 프로세서는 이들 예외의 하위 집합만 생성할 수 있습니다. Windows는 예외에 대한 정보를 전처리하고 적절한 예외 코드를 발급합니다.

Windows에서 인식하는 하드웨어 예외는 다음 표에 요약되어 있습니다.

|예외 코드|예외 원인|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|액세스할 수 없는 메모리 위치를 읽거나 씁니다.|
|STATUS_BREAKPOINT|하드웨어 정의 중단점이 발생합니다. 디버거에서만 사용됩니다.|
|STATUS_DATATYPE_MISALIGNMENT|올바르게 정렬되지 않은 주소에 있는 데이터를 읽거나 씁니다. 예를 들어, 16비트 엔티티는 2바이트 경계에 정렬되어야 합니다. Intel 80 *x* 86 프로세서에는 적용 되지 않습니다.|
|STATUS_FLOAT_DIVIDE_BY_ZERO|부동 소수점 형식을 0.0으로 나눕니다.|
|STATUS_FLOAT_OVERFLOW|부동 소수점 형식의 최대 양의 지수를 초과합니다.|
|STATUS_FLOAT_UNDERFLOW|부동 소수점 형식의 최저 음의 지수 크기를 초과합니다.|
|STATUS_FLOATING_RESEVERED_OPERAND|예약된 부동 소수점 형식(잘못된 형식 사용)을 사용합니다.|
|STATUS_ILLEGAL_INSTRUCTION|프로세서에서 정의하지 않은 명령 코드를 실행합니다.|
|STATUS_PRIVILEGED_INSTRUCTION|현재 시스템 모드에서 실행될 수 없는 명령을 실행합니다.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|정수 형식을 0으로 나눕니다.|
|STATUS_INTEGER_OVERFLOW|정수 범위를 초과하는 연산을 시도합니다.|
|STATUS_SINGLE_STEP|단일 단계 모드에서 하나의 명령을 실행합니다. 디버거에서만 사용됩니다.|

앞의 표에 나온 예외 목록의 대부분은 디버거, 운영 체제 또는 다른 하위 수준 코드에서 처리됩니다. 정수 및 부동 소수점 오류를 제외하고 사용자 코드로 이러한 오류를 처리해서는 안 됩니다. 따라서 일반적으로 예외 처리 필터를 사용하여 예외를 무시하도록 하십시오(0으로 계산). 그러지 않으면 하위 수준 메커니즘이 적절하게 응답하지 않을 수 있습니다. 그러나 [종료 처리기를 작성](../cpp/writing-a-termination-handler.md)하 여 이러한 하위 수준 오류의 잠재적 영향에 대해 적절 한 예방 조치를 취할 수 있습니다.

## <a name="see-also"></a>참고 항목

[예외 처리기 작성](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

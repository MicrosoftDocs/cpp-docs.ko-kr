---
title: 날짜 형식 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe80a16f0085e37feaf7c80611fa303f1d3bf1ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425771"
---
# <a name="date-type"></a>날짜 형식

날짜 형식에는 8 바이트 부동 소수점 숫자를 사용 하 여 구현 됩니다. 일은 1899 년 12 월 30 일 0 시간으로 자정부터 정수 증분으로 표시 됩니다. 시간 값은 숫자의 소수 부분의 절대값으로 표현 됩니다. 다음 표에서 날짜 형식 숫자 동등한 함께 여러 날짜를 보여 줍니다.

|날짜 및 시간|표현|
|-------------------|--------------------|
|1899 년 12 월 30 일 자정|0.00|
|1 1900 년 1 월 자정|2.00|
|4 1900 년 1 월 자정|5.00|
|4 1900 년 1 월 오전 6 시|5.25|
|1900 년 1 월 4 정오|5.50|
|4 1900 년 1 월 오후 9 시|5.875|

날짜 날짜 형식 뿐 `COleDateTime` 클래스를 나타내는 날짜 및 시간으로 클래식 수 있습니다. `COleDateTime` 클래스 다른 일반 날짜 형식 변환을 포함 하는 날짜 값을 조작 하기 위한 여러 메서드가 포함 되어 있습니다.

Automation에서 이러한 날짜 및 시간 형식으로 작업 하는 경우 다음 사항은 유의 해야 합니다.

- 로컬 시간에 지정 된 날짜 다른 표준 시간대의 날짜를 사용 하 여 작업 하는 경우 동기화를 수동으로 수행 해야 합니다.

- 날짜 형식 일광 절약 시간제는 고려 되지 않습니다.

- 날짜 타임 라인 0 보다 작은 날짜 값에 대 한 연속 되지 않은 (하기 전에 복제본이 30 1899 년 12 월). 소수 부분이 처리 됩니다 하는 동안 서명 하는 대로 날짜 값의 정수 부분 처리 되기 때문에 이것이으로 서명 되지 않은 합니다. 즉, 날짜 값의 소수 부분은 항상 전체 논리적 날짜에 추가 하는 동안 양수 또는 음수는 날짜 값의 정수 부분을 수 있습니다. 다음 표에서 몇 가지 예를 보여 줍니다.

|날짜 및 시간|표현|
|-------------------|--------------------|
|1899 년 12 월 27 일 자정|-3.00|
|1899 년 12 월 28 정오|-2.50|
|1899 년 12 월 28 일 자정|-2.00|
|1899 년 12 월 29 일 자정|-1.00|
|1899 년 12 월 30 일 오후 6 시|-0.75|
|1899 년 12 월 30 정오|-0.50|
|1899 년 12 월 30 일 오전 6 시|-0.25|
|1899 년 12 월 30 일 자정|0.00|
|1899 년 12 월 30 일 오전 6 시|0.25|
|1899 년 12 월 30 정오|0.50|
|1899 년 12 월 30 일 오후 6 시|0.75|
|1899 년 12 월 31 일 자정|1.00|
|1 1900 년 1 월 자정|2.00|
|1900 년 1 월 1 정오|2.50|
|2 1900 년 1 월 자정|3.00|

> [!CAUTION]
>  6:00 AM은 항상 소수 자릿수 값 0.25 인지에 관계 없이 일을 나타내는 정수 양수 (1899 년 12 월 30 일) 후 표현 또는 1899 년 12 월 30 일) (이전 음수 이면 간단한 부동 지점 비교는 잘못 정렬 하기 때문에 note 모든 날짜 오전 6:로 1899 년 12 월 30 일 이전의 날짜를 나타내는 *나중에* 는 같은 날 오전 7 시를 나타내는 날짜 보다 합니다.

날짜와 관련 된 문제에 대 한 자세한 정보 및 `COleDateTime` 형식에서 찾을 수 있습니다 [COleDateTime 클래스](../atl-mfc-shared/reference/coledatetime-class.md) 하 고 [날짜 및 시간: 자동화 지원](../atl-mfc-shared/date-and-time-automation-support.md)합니다.

## <a name="see-also"></a>참고 항목

[날짜 및 시간](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime 클래스](../atl-mfc-shared/reference/coledatetime-class.md)


---
description: '자세한 정보: 날짜 및 시간'
title: 날짜 및 시간
ms.date: 08/13/2019
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 4a8f2d5c9537f07c5d410361e79bf14a12778bc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167034"
---
# <a name="date-and-time"></a>날짜 및 시간

MFC는 날짜 및 시간을 사용 하는 다양 한 방법을 지원 합니다.

- 자동화 [날짜 데이터 형식](../atl-mfc-shared/date-type.md)에 대 한 지원. 날짜 날짜, 시간 및 날짜/시간 값을 지원 합니다. [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 및 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 클래스는이 기능을 캡슐화 합니다. 자동화 지원을 사용 하 여 [COleVariant](../mfc/reference/colevariant-class.md) 클래스와 함께 작동 합니다.

- 범용 시간 클래스입니다. [CTime](../atl-mfc-shared/reference/ctime-class.md) 및 [ctimespan](../atl-mfc-shared/reference/ctimespan-class.md) 클래스는 표준 시간대에 선언 된 ANSI 표준 시간 라이브러리와 관련 된 대부분의 기능을 캡슐화 합니다.

- 시스템 클록 지원. MFC 버전 3.0에서는 `CTime` Win32 `SYSTEMTIME` 및 데이터 형식에 대 한 지원이에 추가 되었습니다 `FILETIME` .

## <a name="date-and-time-automation-support"></a>날짜 및 시간: 자동화 지원

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 클래스는 날짜 및 시간 정보를 표시 하는 방법을 제공 합니다. 이를 통해 더 세부적인 세분성과 [CTime](../atl-mfc-shared/reference/ctime-class.md) 클래스 보다 큰 범위가 제공 됩니다. [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 클래스는 두 개체 간의 차이와 같이 경과 된 시간을 나타냅니다 `COleDateTime` .

`COleDateTime`및 `COleDateTimeSpan` 클래스는 클래스와 함께 사용 하도록 디자인 되었습니다 `COleVariant` . `COleDateTime` 및 `COleDateTimeSpan` 는 MFC 데이터베이스 프로그래밍 에서도 유용 하지만 날짜 및 시간 값을 조작 하려는 경우 언제 든 지 사용할 수 있습니다. 클래스에는 보다 `COleDateTime` 큰 범위의 값과 클래스 보다 세부적인 세분성이 있지만 `CTime` , 개체 당 보다 많은 저장소가 필요 `CTime` 합니다. 기본 날짜 형식으로 작업 하는 경우 몇 가지 특별 한 고려 사항도 있습니다. 날짜 구현에 대 한 자세한 내용은 [날짜 형식](../atl-mfc-shared/date-type.md)을 참조 하세요.

`COleDateTime` 개체를 사용 하 여 100 년 1 월 1 일에서 9999 년 12 월 31 일 사이의 날짜를 나타낼 수 있습니다. `COleDateTime` 개체는 부동 소수점 값 이며 대략적인 해상도는 1 밀리초입니다. `COleDateTime` 는 [COleDateTime:: OPERATOR DATE](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)의 MFC 설명서에 정의 된 DATE 데이터 형식을 기반으로 합니다. 실제 날짜 구현은 이러한 범위를 벗어납니다. `COleDateTime`구현에서는 이러한 범위를 사용 하 여 클래스 작업을 보다 쉽게 수행할 수 있습니다.

`COleDateTime` 는 율리우스 날짜를 지원 하지 않습니다. 양력은 시간을 다시 100 년 1 월 1 일로 확장 하는 것으로 간주 됩니다.

`COleDateTime` DST (일광 절약 시간)를 무시 합니다. 다음 코드 예제에서는 CRT를 사용 하는 시간 범위를 계산 하는 두 가지 방법과 CRT를 사용 하는 두 가지 방법을 비교 하 여를 사용 `COleDateTime` 합니다.

첫 번째 메서드는 `CTime` 표준 C 형식 구조 및를 사용 하 여 *날짜순* 및 *time2* 라는 두 개의 개체를 각각 4 월 5 일 및 4 월 6로 설정 합니다 `tm` `time_t` . 이 코드에서는 *날짜순* 및 *time2* 와 그 사이의 시간 범위를 표시 합니다.

두 번째 메서드는 및의 두 `COleDateTime` 개체를 만들고 `oletime1` 이를 `oletime2` *날짜순* 및 *time2* 와 동일한 날짜로 설정 합니다. 및에 표시 되 `oletime1` `oletime2` 는 시간 범위입니다.

CRT는 23 시간의 차이를 정확 하 게 계산 합니다. `COleDateTimeSpan` 24 시간의 차이를 계산 합니다.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

### <a name="get-the-current-time"></a>현재 시간을 가져옵니다.

다음 절차에서는 개체를 만들고 `COleDateTime` 현재 시간으로 초기화 하는 방법을 보여 줍니다.

#### <a name="to-get-the-current-time"></a>현재 시간을 가져오려면

1. `COleDateTime` 개체를 만듭니다.

1. `GetCurrentTime`을 호출합니다.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

### <a name="calculate-elapsed-time"></a>경과 된 시간 계산

이 절차에서는 두 개체 간의 차이를 계산 하 `COleDateTime` 고 결과를 가져오는 방법을 보여 줍니다 `COleDateTimeSpan` .

#### <a name="to-calculate-elapsed-time"></a>경과 된 시간 계산

1. 두 `COleDateTime` 개체를 만듭니다.

1. 개체 중 하나 `COleDateTime` 를 현재 시간으로 설정 합니다.

1. 시간이 많이 걸리는 작업을 수행 합니다.

1. 다른 개체를 `COleDateTime` 현재 시간으로 설정 합니다.

1. 두 시간 사이의 차이를 가져옵니다.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

### <a name="format-a-time"></a>시간 형식 지정

#### <a name="to-format-a-time"></a>시간 형식을 지정 하려면

`Format` [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 또는 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 의 멤버 함수를 사용 하 여 시간 또는 경과 시간을 나타내는 문자열을 만듭니다.

   [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/cpp/formatting-time-automation-classes_1.cpp)]

자세한 내용은 클래스 [COleVariant](../mfc/reference/colevariant-class.md)를 참조 하세요.

## <a name="date-and-time-database-support"></a>날짜 및 시간: 데이터베이스 지원

버전 4.0부터 MFC 데이터베이스 프로그래밍은 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 및 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 클래스를 사용 하 여 날짜 및 시간 데이터를 나타냅니다. 자동화에도 사용 되는 이러한 클래스는 [COleVariant](../mfc/reference/colevariant-class.md)클래스에서 파생 됩니다. 이는 [CTime](../atl-mfc-shared/reference/ctime-class.md) 및 [ctimespan](../atl-mfc-shared/reference/ctimespan-class.md)보다 날짜 및 시간 데이터를 관리 하는 데 더 나은 지원을 제공 합니다.

## <a name="date-and-time-systemtime-support"></a>날짜 및 시간: SYSTEMTIME 지원

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 클래스에는 Win32의 시스템 및 파일 시간을 허용 하는 생성자가 있습니다.

Win32 `FILETIME` 구조체는 시간을 64 비트 값으로 나타냅니다. 구조 보다는 내부 저장소에 대 한 보다 편리한 형식이 `SYSTEMTIME` 며, Win32에서 파일 생성 시간을 나타내는 데 사용 되는 형식입니다. SYSTEMTIME 구조체에 대 한 자세한 내용은 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)를 참조 하세요. FILETIME 구조체에 대 한 자세한 내용은 [filetime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[개념과](../mfc/mfc-concepts.md)\
[일반 MFC 항목](../mfc/general-mfc-topics.md)

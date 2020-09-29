---
title: COleDateTime 클래스
description: OLE automation에서 사용 되는 데이터 형식을 캡슐화 하는 MFC COleDateTime 클래스에 대 한 API 참조 `DATE` 입니다.
ms.date: 08/27/2020
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 38c98793e7e1b22d166de8a869c57f510de7b284
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500172"
---
# <a name="coledatetime-class"></a>COleDateTime 클래스

`DATE`OLE 자동화에 사용 되는 데이터 형식을 캡슐화 합니다.

## <a name="syntax"></a>구문

```
class COleDateTime
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDateTime:: COleDateTime](#coledatetime)|`COleDateTime` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDateTime:: Format](#format)|개체의 형식이 지정 된 문자열 표현을 생성 `COleDateTime` 합니다.|
|[COleDateTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|개체의 시간을 데이터 구조체로 가져오려면이 메서드를 호출 `COleDateTime` `DBTIMESTAMP` 합니다.|
|[COleDateTime:: GetAsSystemTime](#getassystemtime)|개체의 시간을 SYSTEMTIME 데이터 구조체로 가져오려면이 메서드를 호출 `COleDateTime` 합니다. [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[COleDateTime:: GetAsUDATE](#getasudate)|이 메서드를 호출 하 여의 시간을 `COleDateTime` `UDATE` 데이터 구조체로 가져옵니다.|
|[COleDateTime:: GetCurrentTime](#getcurrenttime)|`COleDateTime`현재 시간 (정적 멤버 함수)을 나타내는 개체를 만듭니다.|
|[COleDateTime:: GetDay](#getday)|이 `COleDateTime` 개체가 나타내는 일 (1-31)을 반환 합니다.|
|[COleDateTime:: GetDayOfWeek](#getdayofweek)|이 `COleDateTime` 개체가 나타내는 요일 (일요일 = 1)을 반환 합니다.|
|[COleDateTime:: GetDayOfYear](#getdayofyear)|이 개체가 나타내는 연간 일을 반환 합니다 `COleDateTime` (1 월 1 일).|
|[COleDateTime:: Gethour-해당](#gethour)|이 `COleDateTime` 개체가 나타내는 시간 (0-23)을 반환 합니다.|
|[COleDateTime:: GetMinute](#getminute)|이 `COleDateTime` 개체가 나타내는 분 (0-59)을 반환 합니다.|
|[COleDateTime:: GetMonth](#getmonth)|이 개체가 나타내는 월을 반환 합니다 `COleDateTime` (1-12).|
|[COleDateTime:: GetSecond](#getsecond)|이 `COleDateTime` 개체가 나타내는 초 (0-59)를 반환 합니다.|
|[COleDateTime:: GetStatus](#getstatus)|이 개체의 상태 (유효성)를 가져옵니다 `COleDateTime` .|
|[COleDateTime:: GetYear](#getyear)|이 개체가 나타내는 연도를 반환 `COleDateTime` 합니다.|
|[COleDateTime::P arseDateTime](#parsedatetime)|문자열에서 날짜/시간 값을 읽고의 값을 설정 합니다 `COleDateTime` .|
|[COleDateTime:: SetDate](#setdate)|이 개체의 값을 `COleDateTime` 지정 된 날짜 전용 값으로 설정 합니다.|
|[COleDateTime:: SetDateTime](#setdatetime)|이 개체의 값을 `COleDateTime` 지정 된 날짜/시간 값으로 설정 합니다.|
|[COleDateTime:: SetStatus](#setstatus)|이 개체의 상태 (유효성)를 설정 합니다 `COleDateTime` .|
|[COleDateTime:: SetTime](#settime)|이 개체의 값을 `COleDateTime` 지정 된 시간 전용 값으로 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|속성|설명|
|----------|-----------------|
|[COleDateTime:: operator = =, COleDateTime:: operator < 등](#coledatetime_relational_operators)|두 `COleDateTime` 값을 비교 합니다.|
|[COleDateTime:: operator +, COleDateTime:: operator-](#operator_add_-)|값을 더하거나 뺍니다 `COleDateTime` .|
|[COleDateTime:: operator + =, COleDateTime:: operator-=](#operator_add_eq_-_eq)|`COleDateTime`이 개체에서 값을 더하거나 뺍니다 `COleDateTime` .|
|[COleDateTime:: operator =](#operator_eq)|값을 복사 `COleDateTime` 합니다.|
|[COleDateTime:: operator DATE, COleDateTime:: operator Date *](#operator_date)|값을 `COleDateTime` 또는로 변환 `DATE` `DATE*` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|속성|설명|
|----------|-----------------|
|[COleDateTime:: m_dt](#m_dt)|`DATE`이 개체의 내부를 포함 `COleDateTime` 합니다.|
|[COleDateTime:: m_status](#m_status)|이 개체의 상태를 포함 `COleDateTime` 합니다.|

## <a name="remarks"></a>설명

`COleDateTime` 에 기본 클래스가 없습니다.

이는 OLE automation의 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 데이터 형식에 사용할 수 있는 형식 중 하나입니다. `COleDateTime`값은 절대 날짜 및 시간 값을 나타냅니다.

`DATE`형식은 부동 소수점 값으로 구현 됩니다. 일은 자정에 1899 년 12 월 30 일에서 측정 됩니다. 다음 표에서는 일부 날짜와 관련 값을 보여 줍니다.

|Date|값|
|----------|-----------|
|1899 년 12 월 29 일, 자정|-1.0|
|1899 년 12 월 29 일, 6 A. M|-1.25|
|1899 년 12 월 30 일, 자정|0.0|
|1899 년 12 월 31 일, 자정|1.0|
|1900 년 1 월 1 일 오전 6 시|2.25|

> [!CAUTION]
> 위의 표에서 day 값은 1899 년 12 월 30 일 자정 이전에 음수 이지만 시간 값은 그렇지 않습니다. 예를 들어, 6:00 AM은 해당 일을 나타내는 정수가 양수인 지 (12 월 1899 30 일 이후) 또는 음수 (1899 12 월 30 일까 지)에 관계 없이 항상 소수 값 0.25로 표시 됩니다. 즉, 단순한 부동 소수점 비교가 `COleDateTime` 7:00 am을 나타내는 6:00 오전 12/29/1899을 나타내는을 잘못 정렬 **later** 합니다.

클래스는 100 년 1 `COleDateTime` 월 1 일부 터 9999 년 12 월 31 일까 지 날짜를 처리 합니다. 이 `COleDateTime` 클래스는 그레고리오 력 달력을 사용 하며, 율리우스 날짜를 지원 하지 않습니다. `COleDateTime` 일광 절약 시간을 무시 합니다. ( [날짜 및 시간: 자동화 지원](../date-and-time.md)을 참조 하세요.)

> [!NOTE]
> `%y`1900에서 시작 하는 날짜에 대해서만 형식을 사용 하 여 두 자리 연도를 검색할 수 있습니다. `%y`1900 이전 날짜에 형식을 사용 하는 경우 코드에서 어설션 오류를 생성 합니다.

이 형식은 날짜 전용 또는 시간 전용 값을 나타내는 데도 사용 됩니다. 규칙에 따라 날짜 0 (12 월 30 1899 일 12 월 30 일)은 시간 전용 값에 사용 되며 00:00 (자정) 시간은 날짜 전용 값에 사용 됩니다.

`COleDateTime`100 보다 작은 날짜를 사용 하 여 개체를 만드는 경우에는 날짜가 수락 되지만,,,, 및에 대 한 후속 호출에 `GetYear` `GetMonth` `GetDay` `GetHour` `GetMinute` `GetSecond` 실패 하 고-1이 반환 됩니다. 이전에는 두 자리 날짜를 사용할 수 있지만 MFC 4.2 이상에서는 날짜가 100 이상 이어야 합니다.

문제를 방지 하려면 네 자리 날짜를 지정 합니다. 다음은 그 예입니다.

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

값에 대 한 기본 산술 연산은 `COleDateTime` 동반 클래스 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)를 사용 합니다. `COleDateTimeSpan` 값은 시간 간격을 정의 합니다. 이러한 클래스 간의 관계는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 과 [ctimespan](../../atl-mfc-shared/reference/ctimespan-class.md)간의 관계와 비슷합니다.

및 클래스에 대 한 자세한 내용은 `COleDateTime` `COleDateTimeSpan` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 없음. h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a> COleDateTime 관계형 연산자

비교 연산자.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>매개 변수

*date*<br/>
비교할 `COleDateTime` 개체입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 두 피연산자 중 하나가 잘못 된 경우에는가 없는 어설션이 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>예제

, 및 연산자는 **>=** **\<=**, **>** **<** `COleDateTime` 개체가 null로 설정 된 경우에 어설션 합니다.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a> COleDateTime:: COleDateTime

`COleDateTime` 개체를 생성합니다.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>매개 변수

*dateSrc*<br/>
`COleDateTime`새 개체에 복사할 기존 개체 `COleDateTime` 입니다.

*varSrc*<br/>
`VARIANT` `COleVariant` VT_DATE (날짜/시간) 값으로 변환 되 고 새 개체로 복사 될 수 있는 기존 데이터 구조 (개체 일 수 있음) `COleDateTime` 입니다.

*dtSrc*<br/>
`DATE`새 개체에 복사할 날짜/시간 () 값 `COleDateTime` 입니다.

*timeSrc*<br/>
`time_t` `__time64_t` 날짜/시간 값으로 변환 되 고 새 개체로 복사 되는 또는 값입니다 `COleDateTime` .

*systimeSrc*<br/>
`SYSTEMTIME`날짜/시간 값으로 변환 되 고 새 개체로 복사 되는 구조체 `COleDateTime` 입니다.

*filetimeSrc*<br/>
`FILETIME`날짜/시간 값으로 변환 되 고 새 개체로 복사 되는 구조체 `COleDateTime` 입니다. 는 `FILETIME` utc (Universal 협정 time)를 사용 하므로 구조체에서 현지 시간을 전달 하면 결과가 잘못 됩니다. 자세한 내용은 Windows SDK의 [파일 시간](/windows/win32/SysInfo/file-times) 을 참조 하세요.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
새 개체에 복사할 날짜 및 시간 값을 지정 합니다 `COleDateTime` .

*wDosDate*, *wDosTime*<br/>
날짜/시간 값으로 변환 되 고 새 개체로 복사 되는 MS-DOS 날짜 및 시간 값입니다 `COleDateTime` .

*없으면*<br/>
현재 현지 시간을 포함 하는 [Dbtimestamp](/dotnet/api/system.data.oledb.oledbtype) 구조체에 대 한 참조입니다.

### <a name="remarks"></a>설명

이러한 모든 생성자는 `COleDateTime` 지정 된 값으로 초기화 된 새 개체를 만듭니다. 다음 표에서는 각 날짜 및 시간 구성 요소에 대 한 유효한 범위를 보여 줍니다.

|날짜/시간 구성 요소|유효 범위|
|--------------------------|-----------------|
|연도|100-9999|
|month|0 - 12|
|일|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

일 구성 요소에 대 한 실제 상한은 month 및 year 구성 요소에 따라 다릅니다. 자세한 내용은 `SetDate` 또는 멤버 함수를 참조 하세요 `SetDateTime` .

다음은 각 생성자에 대 한 간단한 설명입니다.

- `COleDateTime(`**)** 는 `COleDateTime` 0 (자정, 30 년 12 월 1899)으로 초기화 되는 개체를 생성 합니다.

- `COleDateTime(``dateSrc` **)** `COleDateTime`기존 개체에서 개체를 생성 `COleDateTime` 합니다.

- `COleDateTime(`*varsrc* **)** 개체를 생성 `COleDateTime` 합니다. `VARIANT`구조체 또는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체를 날짜/시간 () 값으로 변환 하려고 `VT_DATE` 합니다. 이 변환에 성공 하면 변환 된 값이 새 개체에 복사 됩니다 `COleDateTime` . 그렇지 않으면 개체의 값 `COleDateTime` 이 0 (자정, 30 년 12 월 1899)으로 설정 되 고 상태가 잘못 된 것으로 설정 됩니다.

- `COleDateTime(``dtSrc` **)** `COleDateTime`값에서 개체를 생성 `DATE` 합니다.

- `COleDateTime(``timeSrc` **)** `COleDateTime`값에서 개체를 생성 `time_t` 합니다.

- `COleDateTime(`*systimeSrc* **)** `COleDateTime` 는 값에서 개체를 생성 `SYSTEMTIME` 합니다.

- `COleDateTime(``filetimeSrc` **)** `COleDateTime`값에서 개체를 생성 `FILETIME` 합니다. . 는 `FILETIME` utc (Universal 협정 time)를 사용 하므로 구조체에서 현지 시간을 전달 하면 결과가 잘못 됩니다. 자세한 내용은 Windows SDK의 [파일 시간](/windows/win32/SysInfo/file-times) 을 참조 하세요.

- `COleDateTime(`,,,, `nYear` `nMonth` `nDay` `nHour` `nMin` , `nSec` **)** `COleDateTime` 는 지정 된 숫자 값에서 개체를 생성 합니다.

- `COleDateTime(``wDosDate`, `wDosTime` **)** 지정 된 `COleDateTime` MS-DOS 날짜 및 시간 값에서 개체를 생성 합니다.

데이터 형식에 대 한 자세한 내용은 `time_t` *런타임 라이브러리 참조*에서 [time](../../c-runtime-library/reference/time-time32-time64.md) 함수를 참조 하세요.

자세한 내용은 Windows SDK [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 및 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조를 참조 하세요.

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

> [!NOTE]
> 매개 변수를 사용 하는 생성자는 `DBTIMESTAMP` OLEDB가 포함 된 경우에만 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a> COleDateTime:: Format

날짜/시간 값의 형식이 지정 된 표현을 만듭니다.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
다음 로캘 플래그 중 하나를 나타냅니다.

- 사용자 지정 사용자 설정 대신 시스템 기본 로캘 설정을 사용 LOCALE_NOUSEROVERRIDE 합니다.

- 구문 분석 중에 날짜 부분을 무시 VAR_TIMEVALUEONLY 합니다.

- 구문 분석 중에는 시간 부분을 무시 VAR_DATEVALUEONLY.

*lcid*<br/>
변환에 사용할 로캘 ID를 나타냅니다. 언어 식별자에 대 한 자세한 내용은 [언어 식별자](/windows/win32/Intl/language-identifiers)를 참조 하세요.

*lpszFormat*<br/>
서식 지정 문자열과 유사한 형식 문자열 `printf` 입니다. 백분율 () 기호가 앞에 오는 각 서식 지정 코드 `%` 는 해당 구성 요소로 대체 됩니다 `COleDateTime` . 서식 문자열의 다른 문자는 변경 되지 않은 상태로 반환 된 문자열에 복사 됩니다. 자세한 내용은 런타임 함수 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)을 참조 하세요. 에 대 한 서식 지정 코드의 값과 의미는 `Format` 다음과 같습니다.

- `%H` 현재 날짜의 시간

- `%M` 현재 시간의 분

- `%S` 현재 분의 초

- `%%` 백분율 기호

*nFormatID*<br/>
형식 컨트롤 문자열에 대 한 리소스 ID입니다.

### <a name="return-value"></a>반환 값

`CString`형식이 지정 된 날짜/시간 값을 포함 하는입니다.

### <a name="remarks"></a>설명

이 개체의 상태가 `COleDateTime` null 이면 반환 값은 빈 문자열입니다. 상태가 잘못 된 경우 문자열 리소스 ATL_IDS_DATETIME_INVALID에 의해 반환 문자열이 지정 됩니다.

이 함수에 대 한 간략 한 설명은 다음과 같습니다.

`Format`( *dwFlags*, *lcid*)<br/>
이 폼은 날짜 및 시간에 언어 사양 (로캘 Id)을 사용 하 여 값의 서식을 지정 합니다. 이 폼은 기본 매개 변수를 사용 하 여 날짜와 시간을 인쇄 합니다 .이 경우 시간 부분이 0 (자정) 이면 날짜만 인쇄 되 고 날짜 부분은 0 (30 년 12 월 1899)이 되 고,이 경우 시간만 인쇄 됩니다. 날짜/시간 값이 0 (자정 12 월 1899 일) 이면 기본 매개 변수를 사용 하는이 형식은 자정을 인쇄 합니다.

`Format`( *lpszFormat*)<br/>
이 폼은에서와 같이 백분율 기호 (%)가 앞에 나오는 특수 서식 지정 코드가 포함 된 서식 문자열을 사용 하 여 값의 서식을 지정 합니다 `printf` . 형식 문자열은 함수에 매개 변수로 전달 됩니다. 서식 지정 코드에 대 한 자세한 내용은 런타임 라이브러리 참조에서 [strftime, wcsftime을](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 참조 하세요.

`Format`( *nFormatID*)<br/>
이 폼은에서와 같이 백분율 기호 (%)가 앞에 나오는 특수 서식 지정 코드가 포함 된 서식 문자열을 사용 하 여 값의 서식을 지정 합니다 `printf` . 형식 문자열은 리소스입니다. 이 문자열 리소스의 ID는 매개 변수로 전달 됩니다. 서식 지정 코드에 대 한 자세한 내용은 *런타임 라이브러리 참조*에서 [strftime, wcsftime을](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> COleDateTime:: GetAsDBTIMESTAMP

개체의 시간을 데이터 구조체로 가져오려면이 메서드를 호출 `COleDateTime` `DBTIMESTAMP` 합니다.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>매개 변수

*없으면*<br/>
[Dbtimestamp](/dotnet/api/system.data.oledb.oledbtype) 구조체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

결과 시간을 참조 된 *타임 스탬프* 구조에 저장 합니다. `DBTIMESTAMP`이 함수에 의해 초기화 되는 데이터 구조의 `fraction` 멤버는 0으로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a> COleDateTime:: GetAsSystemTime

개체의 시간을 데이터 구조체로 가져오려면이 메서드를 호출 `COleDateTime` `SYSTEMTIME` 합니다.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>매개 변수

*sysTime*<br/>
개체에서 변환 된 날짜/시간 값을 받는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 참조 `COleDateTime` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 합니다. 변환이 실패 하는 경우 FALSE이 고, `COleDateTime` 개체가 NULL 이거나 잘못 된 경우입니다.

### <a name="remarks"></a>설명

`GetAsSystemTime` 참조 된 *sysTime* 개체에 결과 시간을 저장 합니다. `SYSTEMTIME`이 함수에 의해 초기화 되는 데이터 구조의 `wMilliseconds` 멤버는 0으로 설정 됩니다.

개체에 저장 된 상태 정보에 대 한 자세한 내용은 `COleDateTime` [GetStatus](#getstatus)를 참조 하세요.

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a> COleDateTime:: GetAsUDATE

개체의 시간을 데이터 구조체로 가져오려면이 메서드를 호출 `COleDateTime` `UDATE` 합니다.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>매개 변수

*uDate*<br/>
`UDATE`개체에서 변환 된 날짜/시간 값을 받는 구조체에 대 한 참조 `COleDateTime` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 합니다. 변환이 실패 하는 경우 FALSE이 고, `COleDateTime` 개체가 NULL 이거나 잘못 된 경우입니다.

### <a name="remarks"></a>설명

`UDATE`구조는 "압축을 푼" 날짜를 나타냅니다.

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a> COleDateTime:: GetCurrentTime

현재 날짜/시간 값을 반환 하려면이 정적 멤버 함수를 호출 합니다.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a> COleDateTime:: GetDay

이 날짜/시간 값으로 표시 되는 월의 일을 가져옵니다.

```
int GetDay() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값으로 표시 되는 월의 일 `COleDateTime` 이거나 `COleDateTime::error` 일을 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 1에서 31 사이입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a> COleDateTime:: GetDayOfWeek

이 날짜/시간 값이 나타내는 요일을 가져옵니다.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값으로 표시 되는 요일 이거나 요일을 `COleDateTime` 가져올 수 `COleDateTime::error` 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 1에서 7 사이입니다. 여기서 1은 일요일, 2 = 월요일 등입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a> COleDateTime:: GetDayOfYear

이 날짜/시간 값이 나타내는 일 (연도 기준)을 가져옵니다.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값으로 표시 되는 연도의 날짜 `COleDateTime` 이거나 `COleDateTime::error` 연도 일을 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 1에서 366 사이입니다. 여기서 1 월 1 일은 1입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a> COleDateTime:: Gethour-해당

이 날짜/시간 값이 나타내는 시간을 가져옵니다.

```
int GetHour() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값이 나타내는 시간 `COleDateTime` 이거나, `COleDateTime::error` 시간을 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 0에서 23 사이입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a> COleDateTime:: GetMinute

이 날짜/시간 값으로 표시 되는 분을 가져옵니다.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값이 나타내는 분 `COleDateTime` 이거나, `COleDateTime::error` 분을 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 0에서 59 사이입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[Gethour-해당](#gethour)의 예제를 참조 하세요.

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a> COleDateTime:: GetMonth

이 날짜/시간 값으로 표시 되는 월을 가져옵니다.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값이 나타내는 월 `COleDateTime` 이거나, `COleDateTime::error` 월을 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 1에서 12 사이입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[Getday](#getday)의 예제를 참조 하세요.

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a> COleDateTime:: GetSecond

이 날짜/시간 값으로 표시 되는 초를 가져옵니다.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값으로 표시 되는 두 번째 이거나, 두 번째를 `COleDateTime` `COleDateTime::error` 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 0에서 59 사이입니다.

> [!NOTE]
> `COleDateTime`클래스는 윤 초를 지원 하지 않습니다.

의 구현에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>예제

[Gethour-해당](#gethour)의 예제를 참조 하세요.

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a> COleDateTime:: GetStatus

지정 된 개체의 상태 (유효성)를 가져옵니다 `COleDateTime` .

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>반환 값

이 값의 상태를 반환 `COleDateTime` 합니다. `GetStatus`기본값을 사용 하 여 생성 된 개체에 대해를 호출 하는 경우 `COleDateTime` 유효한을 반환 합니다. `GetStatus` `COleDateTime` 생성자를 null로 설정 하 여 초기화 된 개체에서를 호출 하면에서 `GetStatus` null이 반환 됩니다.

### <a name="remarks"></a>설명

반환 값은 `DateTimeStatus` 클래스 내에 정의 된 열거형 형식에 의해 정의 됩니다 `COleDateTime` .

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleDateTime::error` 날짜/시간 값의 일부를 가져오는 동안 오류가 발생 했음을 나타냅니다.

- `COleDateTime::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleDateTime` .

- `COleDateTime::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleDateTime` , 해당 값이 잘못 되었을 수 있습니다.

- `COleDateTime::null` 이 `COleDateTime` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

개체의 상태는 `COleDateTime` 다음과 같은 경우 유효 하지 않습니다.

- 해당 값이 `VARIANT` `COleVariant` 날짜/시간 값으로 변환 될 수 없는 또는 값에서 설정 된 경우

- 해당 값이 `time_t` `SYSTEMTIME` `FILETIME` 유효한 날짜/시간 값으로 변환 될 수 없는, 또는 값으로 설정 된 경우

- `SetDateTime`매개 변수 값이 잘못 된로 설정 된 경우

- 산술 할당 작업 중이 개체에 오버플로 또는 언더플로가 발생 한 경우, 즉 `+=` 또는 `-=` 입니다.

- 이 개체에 잘못 된 값이 할당 된 경우

- 이 개체의 상태가를 사용 하 여 명시적으로 잘못 설정 된 경우 `SetStatus` 입니다.

상태를 잘못 된 것으로 설정할 수 있는 작업에 대 한 자세한 내용은 다음 멤버 함수를 참조 하세요.

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [연산자 +,-](#operator_add_-)

- [operator + =,-=](#operator_add_eq_-_eq)

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a> COleDateTime:: GetYear

이 날짜/시간 값으로 표시 되는 연도를 가져옵니다.

```
int GetYear() const throw();
```

### <a name="return-value"></a>반환 값

이 개체의 값이 나타내는 연도 `COleDateTime` 이거나 `COleDateTime::error` 연도를 가져올 수 없는 경우입니다.

### <a name="remarks"></a>설명

유효한 반환 값의 범위는 세기를 포함 하는 100과 9999 사이입니다.

이 개체의 값을 쿼리 하는 다른 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[Getday](#getday)의 예제를 참조 하세요.

## <a name="coledatetimem_dt"></a><a name="m_dt"></a> COleDateTime:: m_dt

`DATE`이 개체의 기본 구조체 `COleDateTime` 입니다.

```
DATE m_dt;
```

### <a name="remarks"></a>설명

> [!CAUTION]
> 이 함수에서 반환 하는 포인터에 의해 액세스 되는 개체의 값을 변경 `DATE` 하면이 개체의 값이 변경 됩니다 `COleDateTime` . 이 개체의 상태는 변경 되지 않습니다 `COleDateTime` .

개체의 구현에 대 한 자세한 내용은 `DATE` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimem_status"></a><a name="m_status"></a> COleDateTime:: m_status

이 개체의 상태를 포함 `COleDateTime` 합니다.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>설명

이 데이터 멤버의 형식은 클래스 내에 정의 된 열거형 형식입니다 `DateTimeStatus` `COleDateTime` . 자세한 내용은 [COleDateTime:: GetStatus](#getstatus)를 참조 하세요.

> [!CAUTION]
> 이 데이터 멤버는 고급 프로그래밍 상황을 위한 것입니다. 인라인 멤버 함수 [GetStatus](#getstatus) 및 [SetStatus](#setstatus)를 사용 해야 합니다. `SetStatus`이 데이터 멤버를 명시적으로 설정 하는 방법에 대 한 자세한 내용은을 참조 하십시오.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a> COleDateTime:: operator =

값을 복사 `COleDateTime` 합니다.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>설명

이러한 오버 로드 된 할당 연산자는 원본 날짜/시간 값을이 개체에 복사 `COleDateTime` 합니다. 이러한 오버 로드 된 각 할당 연산자에 대 한 간략 한 설명은 다음과 같습니다.

- **operator = (** `dateSrc` **)** 피연산자의 값과 상태가이 개체로 복사 됩니다 `COleDateTime` .

- **operator = (** *varsrc* **)** [변형](/windows/win32/api/oaidl/ns-oaidl-variant) 값 (또는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체)을 날짜/시간 (VT_DATE)으로 변환 하는 데 성공 하면 변환 된 값이이 개체에 복사 되 `COleDateTime` 고 상태는 valid로 설정 됩니다. 변환에 성공 하지 못하면이 개체의 값은 0 (자정 12 월 1899, 자정) 및 상태가 잘못 됨으로 설정 됩니다.

- **operator = (** `dtSrc` **)** `DATE` 이 개체에 값이 복사 되 `COleDateTime` 고 해당 상태가 valid로 설정 됩니다.

- **operator = (** `timeSrc` **)** `time_t` 또는 `__time64_t` 값이 변환 되어이 개체로 복사 됩니다 `COleDateTime` . 성공적으로 변환 되 면이 개체의 상태는 valid로 설정 됩니다. 실패 한 경우 잘못 된 것으로 설정 됩니다.

- **연산자 = (** *systimeSrc* **)** [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 값이 변환 되어이 개체로 복사 됩니다 `COleDateTime` . 성공적으로 변환 되 면이 개체의 상태는 valid로 설정 됩니다. 실패 한 경우 잘못 된 것으로 설정 됩니다.

- **operator = (** `uDate` **)** `UDATE` 값이 변환 되어이 개체로 복사 됩니다 `COleDateTime` . 성공적으로 변환 되 면이 개체의 상태는 valid로 설정 됩니다. 실패 한 경우 잘못 된 것으로 설정 됩니다. `UDATE`구조는 "압축을 푼" 날짜를 나타냅니다. 자세한 내용은 [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)함수를 참조 하세요.

- **operator = (** `filetimeSrc` **)** [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 값을 변환 하 여이 개체로 복사 `COleDateTime` 합니다. 성공적으로 변환 되 면이 개체의 상태는 valid로 설정 됩니다. 그렇지 않으면 잘못 된 것으로 설정 됩니다. `FILETIME` utc (Universal 협정 Time)를 사용 하므로 구조에서 UTC 시간을 전달 하는 경우 결과는 UTC 시간에서 현지 시간으로 변환 되 고 variant Time으로 저장 됩니다. 이 동작은 Visual C++ 6.0 및 Visual C++ .NET 2003 s p 2에서와 동일 합니다. 자세한 내용은 Windows SDK의 [파일 시간](/windows/win32/SysInfo/file-times) 을 참조 하세요.

자세한 내용은 Windows SDK의 [변형](/windows/win32/api/oaidl/ns-oaidl-variant) 항목을 참조 하세요.

데이터 형식에 대 한 자세한 내용은 `time_t` *런타임 라이브러리 참조*에서 [time](../../c-runtime-library/reference/time-time32-time64.md) 함수를 참조 하세요.

자세한 내용은 Windows SDK [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 및 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조를 참조 하세요.

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a> COleDateTime:: operator +,-

값을 더하거나 뺍니다 `ColeDateTime` .

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>설명

`COleDateTime` 개체는 절대 시간을 나타냅니다. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) 개체는 상대 시간을 나타냅니다. 처음 두 연산자를 사용 하 여 값에서 값을 더하거나 뺄 수 있습니다 `COleDateTimeSpan` `COleDateTime` . 세 번째 연산자를 사용 하면 값을 `COleDateTime` 산출 하기 위해 다른 값에서 한 값을 뺄 수 있습니다 `COleDateTimeSpan` .

피연산자 중 하나가 null 이면 결과 값의 상태가 `COleDateTime` null입니다.

결과 `COleDateTime` 값이 허용 되는 값의 범위를 벗어나면 해당 값의 상태가 `COleDateTime` 잘못 된 것입니다.

피연산자 중 하나가 유효 하지 않은 경우 다른 피연산자가 null이 아니면 결과 값의 상태가 잘못 된 `COleDateTime` 것입니다.

**+** 및 **-** 연산자는 `COleDateTime` 개체가 null로 설정 된 경우를 어설션 합니다. 예는 [COleDateTime 관계형 연산자](#coledatetime_relational_operators) 를 참조 하세요.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTime:: operator + =,-=

`ColeDateTime`이 개체에서 값을 더하거나 뺍니다 `COleDateTime` .

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>설명

이러한 연산자를 사용 하 여이에서 값을 추가 하 고 뺄 수 있습니다 `COleDateTimeSpan` `COleDateTime` . 피연산자 중 하나가 null 이면 결과 값의 상태가 `COleDateTime` null입니다.

결과 `COleDateTime` 값이 허용 되는 값의 범위를 벗어나면이 값의 상태가 `COleDateTime` 잘못 됨으로 설정 됩니다.

피연산자 중 하나가 유효 하지 않은 경우 다른 피연산자가 null이 아니면 결과 값의 상태가 `COleDateTime` 잘못 된 것입니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

**+=** 및 **-=** 연산자는 `COleDateTime` 개체가 null로 설정 된 경우를 어설션 합니다. 예는 [COleDateTime 관계형 연산자](#coledatetime_relational_operators) 를 참조 하세요.

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a> COleDateTime:: operator DATE

값을로 변환 `ColeDateTime` `DATE` 합니다.

```
operator DATE() const throw();
```

### <a name="remarks"></a>설명

이 연산자는 `DATE` 이 개체에서 값이 복사 되는 개체를 반환 `COleDateTime` 합니다. 개체의 구현에 대 한 자세한 내용은 `DATE` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

`DATE`연산자는 `COleDateTime` 개체가 null로 설정 된 경우를 어설션 합니다. 예는 [COleDateTime 관계형 연산자](#coledatetime_relational_operators) 를 참조 하세요.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a> COleDateTime::P arseDateTime

문자열을 구문 분석 하 여 날짜/시간 값을 읽습니다.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>매개 변수

*lpszDate*<br/>
구문 분석할 null로 끝나는 문자열에 대 한 포인터입니다. 자세한 내용은 설명을 참조하세요.

*dwFlags*<br/>
로캘 설정 및 구문 분석에 대 한 플래그를 나타냅니다. 다음 플래그 중 하나 이상입니다.

- 사용자 지정 사용자 설정이 아닌 시스템 기본 로캘 설정을 사용 LOCALE_NOUSEROVERRIDE 합니다.

- 구문 분석 중에 날짜 부분을 무시 VAR_TIMEVALUEONLY 합니다.

- 구문 분석 중에는 시간 부분을 무시 VAR_DATEVALUEONLY.

*lcid*<br/>
변환에 사용할 로캘 ID를 나타냅니다.

### <a name="return-value"></a>반환 값

문자열이 날짜/시간 값으로 성공적으로 변환 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

문자열이 날짜/시간 값으로 성공적으로 변환 되 면이 개체의 값은 `COleDateTime` 해당 값으로 설정 되 고 상태는 valid로 설정 됩니다.

> [!NOTE]
> 연도 값은 100에서 9999 사이 여야 합니다.

*LpszDate* 매개 변수는 다양 한 형식을 사용할 수 있습니다. 예를 들어 다음 문자열에는 허용 되는 날짜/시간 형식이 포함 되어 있습니다.

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

로캘 ID는 문자열 형식을 날짜/시간 값으로 변환할 수 있는지 여부에도 영향을 줍니다.

VAR_DATEVALUEONLY 경우 시간 값은 시간 0 또는 자정으로 설정 됩니다. VAR_TIMEVALUEONLY의 경우 날짜 값은 날짜 0으로 설정 됩니다. 즉, 30 년 12 월 1899입니다.

문자열을 날짜/시간 값으로 변환할 수 없거나 숫자 오버플로가 발생 한 경우에는이 개체의 상태가 잘못 된 것입니다 `COleDateTime` .

값의 범위 및 구현에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimesetdate"></a><a name="setdate"></a> COleDateTime:: SetDate

이 개체의 날짜를 설정 합니다 `COleDateTime` .

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>매개 변수

*n 년*\
이 개체에 복사할 연도를 나타냅니다 `COleDateTime` .

*nMonth*\
이 개체에 복사할 월을 나타냅니다 `COleDateTime` .

*nDay*\
이 개체에 복사할 날짜를 나타냅니다 `COleDateTime` .

### <a name="return-value"></a>반환 값

이 개체의 값이 `COleDateTime` 성공적으로 설정 되었으면 0이 고, 그렇지 않으면 1입니다. 이 반환 값은 `DateTimeStatus` 열거 형식을 기반으로 합니다. 자세한 내용은 [SetStatus](#setstatus) 구성원 함수를 참조 하세요.

### <a name="remarks"></a>설명

날짜는 지정 된 값으로 설정 됩니다. 시간은 시간 0, 자정로 설정 됩니다.

매개 변수 값에 대 한 범위는 다음 표를 참조 하세요.

|매개 변수|Bounds|
|---------------|------------|
|*nYear*|100-9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

해당 월의 날짜가 오버플로 되 면 다음 달의 올바른 날짜로 변환 되 고 그에 따라 월 및/또는 연도가 증가 합니다. Day 값이 0 이면 이전 달의 마지막 날짜를 나타냅니다. 동작은와 동일 합니다 `SystemTimeToVariantTime` .

매개 변수로 지정 된 날짜 값이 잘못 된 경우이 개체의 상태는로 설정 됩니다 `COleDateTime::invalid` . [GetStatus](#getstatus) 를 사용 하 여 값의 유효성을 검사 해야 하 `DATE` 고 [m_dt](#m_dt) 값이 수정 되지 않은 상태로 유지 되는 것으로 가정해 서는 안 됩니다.

날짜 값의 몇 가지 예는 다음과 같습니다.

|*nYear*|*nMonth*|*nDay*|값|
|-------------|--------------|------------|-----------|
|2000|2|29|29 2 월 2000|
|1776|7|4|4 7 월 1776|
|1925|4|35|35 4 월 1925 (잘못 된 날짜)|
|10000|1|1|1 1 월 1만 (잘못 된 날짜)|

날짜와 시간을 모두 설정 하려면 [COleDateTime:: SetDateTime](#setdatetime)을 참조 하세요.

이 개체의 값을 쿼리 하는 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a> COleDateTime:: SetDateTime

이 개체의 날짜와 시간을 설정 합니다 `COleDateTime` .

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>매개 변수

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
이 개체에 복사할 날짜 및 시간 구성 요소를 지정 `COleDateTime` 합니다.

### <a name="return-value"></a>반환 값

이 개체의 값이 `COleDateTime` 성공적으로 설정 되었으면 0이 고, 그렇지 않으면 1입니다. 이 반환 값은 `DateTimeStatus` 열거 형식을 기반으로 합니다. 자세한 내용은 [SetStatus](#setstatus) 구성원 함수를 참조 하세요.

### <a name="remarks"></a>설명

매개 변수 값에 대 한 범위는 다음 표를 참조 하세요.

|매개 변수|Bounds|
|---------------|------------|
|*nYear*|100-9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

해당 월의 날짜가 오버플로 되 면 다음 달의 올바른 날짜로 변환 되 고 그에 따라 월 및/또는 연도가 증가 합니다. Day 값이 0 이면 이전 달의 마지막 날짜를 나타냅니다. 동작은 [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)와 동일 합니다.

매개 변수로 지정 된 날짜 또는 시간 값이 잘못 된 경우이 개체의 상태가 잘못 됨으로 설정 되 고이 개체의 값이 변경 되지 않습니다.

시간 값의 몇 가지 예는 다음과 같습니다.

|*nHour*|*nMin*|*nSec*|값|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|올바르지 않음|
|9|60|0|올바르지 않음|

날짜 값의 몇 가지 예는 다음과 같습니다.

|*nYear*|*nMonth*|*nDay*|값|
|-------------|--------------|------------|-----------|
|1995|4|15|15 4 월 1995|
|1789|7|14|17 7 월 1789|
|1925|2|30|올바르지 않음|
|10000|1|1|올바르지 않음|

날짜만 설정 하려면 [COleDateTime:: SetDate](#setdate)를 참조 하세요. 시간만 설정 하려면 [COleDateTime:: SetTime](#settime)를 참조 하세요.

이 개체의 값을 쿼리 하는 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[GetStatus](#getstatus)의 예제를 참조 하세요.

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a> COleDateTime:: SetStatus

이 개체의 상태를 설정 합니다 `COleDateTime` .

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>매개 변수

*status*<br/>
이 개체의 새 상태 값 `COleDateTime` 입니다.

### <a name="remarks"></a>설명

*상태* 매개 변수 값은 `DateTimeStatus` 클래스 내에서 정의 되는 열거 된 형식에 의해 정의 됩니다 `COleDateTime` . 자세한 내용은 [COleDateTime:: GetStatus](#getstatus) 를 참조 하세요.

> [!CAUTION]
> 이 함수는 고급 프로그래밍 상황을 위한 것입니다. 이 함수는이 개체의 데이터를 변경 하지 않습니다. 상태를 **null** 또는 **잘못**된 것으로 설정 하는 데 주로 사용 됩니다. 대입 연산자 ([operator =](#operator_eq)) 및 [setdatetime](#setdatetime) 은 원본 값을 기준으로 개체의 상태를 설정 합니다.

### <a name="example"></a>예제

[GetStatus](#getstatus)의 예제를 참조 하세요.

## <a name="coledatetimesettime"></a><a name="settime"></a> COleDateTime:: SetTime

이 개체의 시간을 설정 `COleDateTime` 합니다.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>매개 변수

*Nhour*, *nhour*, *nSec*<br/>
이 개체에 복사할 시간 구성 요소를 지정 `COleDateTime` 합니다.

### <a name="return-value"></a>반환 값

이 개체의 값이 `COleDateTime` 성공적으로 설정 되었으면 0이 고, 그렇지 않으면 1입니다. 이 반환 값은 `DateTimeStatus` 열거 형식을 기반으로 합니다. 자세한 내용은 [SetStatus](#setstatus) 구성원 함수를 참조 하세요.

### <a name="remarks"></a>설명

시간이 지정 된 값으로 설정 됩니다. 날짜는 날짜 0으로 설정 되며,이는 30 년 12 월 1899입니다.

매개 변수 값에 대 한 범위는 다음 표를 참조 하세요.

|매개 변수|Bounds|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

매개 변수로 지정 된 시간 값이 유효 하지 않으면이 개체의 상태가 잘못 됨으로 설정 되 고이 개체의 값이 변경 되지 않습니다.

시간 값의 몇 가지 예는 다음과 같습니다.

|*nHour*|*nMin*|*nSec*|값|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|올바르지 않음|
|9|60|0|올바르지 않음|

날짜와 시간을 모두 설정 하려면 [COleDateTime:: SetDateTime](#setdatetime)을 참조 하세요.

이 개체의 값을 쿼리 하는 멤버 함수에 대 한 자세한 내용은 `COleDateTime` 다음 멤버 함수를 참조 하세요.

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour-해당](#gethour)

- [Getminute-해당](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

값의 범위에 대 한 자세한 내용은 `COleDateTime` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[SetDate](#setdate)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[COleVariant 클래스](../../mfc/reference/colevariant-class.md)<br/>
[CTime 클래스](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 클래스](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)

---
description: '자세히 알아보기: CTime 클래스'
title: CTime 클래스
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: 3768423a4d3bf873e9161b846e21fda4beffdc9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166605"
---
# <a name="ctime-class"></a>CTime 클래스

절대 시간과 날짜를 나타냅니다.

## <a name="syntax"></a>구문

```
class CTime
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CTime:: CTime](#ctime)|`CTime`여러 가지 방법으로 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTime::Format](#format)|`CTime`로컬 표준 시간대를 기준으로 개체를 형식이 지정 된 문자열로 변환 합니다.|
|[CTime::FormatGmt](#formatgmt)|`CTime`UTC를 기준으로 개체를 형식이 지정 된 문자열로 변환 합니다.|
|[CTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|개체에 저장 된 시간 정보를 `CTime` Win32 호환 DBTIMESTAMP 구조체로 변환 합니다.|
|[CTime::GetAsSystemTime](#getassystemtime)|개체에 저장 된 시간 정보를 `CTime` Win32 호환 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체로 변환 합니다.|
|[CTime:: GetCurrentTime](#getcurrenttime)|`CTime`현재 시간 (정적 멤버 함수)을 나타내는 개체를 만듭니다.|
|[CTime::GetDay](#getday)|개체에 의해 표시 되는 일을 반환 합니다 `CTime` .|
|[CTime:: GetDayOfWeek](#getdayofweek)|개체가 나타내는 요일을 반환 합니다 `CTime` .|
|[CTime:: GetGmtTm](#getgmttm)|`CTime`UTC를 기준으로 개체를 구성 요소로 분할 합니다.|
|[CTime:: Gethour-해당](#gethour)|개체가 나타내는 시간을 반환 합니다 `CTime` .|
|[CTime::GetLocalTm](#getlocaltm)|`CTime`로컬 표준 시간대를 기준으로 개체를 구성 요소로 분할 합니다.|
|[CTime::GetMinute](#getminute)|개체가 나타내는 분을 반환 합니다 `CTime` .|
|[CTime:: GetMonth](#getmonth)|개체가 나타내는 월을 반환 `CTime` 합니다.|
|[CTime:: GetSecond](#getsecond)|개체가 나타내는 두 번째를 반환 합니다 `CTime` .|
|[CTime:: GetTime](#gettime)|지정 된 개체에 대 한 **__time64_t** 값을 반환 `CTime` 합니다.|
|[CTime:: GetYear](#getyear)|개체가 나타내는 연도를 반환 합니다 `CTime` .|
|[CTime::Serialize64](#serialize64)|보관 파일에서 데이터를 직렬화 합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[operator +-](#operator_add_-)|이러한 연산자는 및 개체를 추가 하 고 뺍니다 `CTimeSpan` `CTime` .|
|[operator + =,-=](#operator_add_eq_-_eq)|이러한 연산자는 개체를 추가 하 고 `CTimeSpan` 이 개체에서 뺍니다 `CTime` .|
|[연산자 =](#operator_eq)|할당 연산자입니다.|
|[operator ==, < , etc.](#ctime_comparison_operators)|비교 연산자.|

## <a name="remarks"></a>설명

`CTime` 에 기본 클래스가 없습니다.

`CTime` 값은 UTC (협정 세계시)를 기반으로 하며 협정 세계시 (그리니치 표준시, GMT)와 동일 합니다. 표준 시간대를 결정 하는 방법에 대 한 자세한 내용은 [시간 관리](../../c-runtime-library/time-management.md) 를 참조 하세요.

개체를 만들 때 매개 변수를 0으로 설정 하 여 표준 시간이 적용 되 고 있음을 나타내거나 0 보다 큰 값으로 설정 하 여 일광 절약 시간이 적용 되 고 있음을 나타내거나 0 보다 작은 값으로 설정 하 여 `CTime` `nDST` C 런타임 라이브러리 코드가 표준 시간 또는 일광 절약 시간이 적용 되는지 여부를 계산 하도록 합니다. `tm_isdst`는 필수 필드입니다. 설정 하지 않으면 해당 값이 정의 되지 않고 [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) 의 반환 값을 예측할 수 없습니다. `timeptr`가 [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md) 또는 [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)에 대한 이전 호출에서 반환된 tm 구조를 가리키면 `tm_isdst`필드에 올바른 값이 포함됩니다.

동반 클래스인 [Ctimespan](../../atl-mfc-shared/reference/ctimespan-class.md)은 시간 간격을 나타냅니다.

`CTime`및 `CTimeSpan` 클래스는 파생을 위해 디자인 되지 않았습니다. 가상 함수가 없으므로 및 개체의 크기는 `CTime` `CTimeSpan` 정확히 8 바이트입니다. 대부분의 멤버 함수는 인라인 함수입니다.

> [!NOTE]
> 상한 날짜 제한은 12/31/3000입니다. 한도는 오전 1/1/1970 12:00:00 시 GMT입니다.

사용에 대 한 자세한 내용은 `CTime` Run-Time 라이브러리 참조에서 [날짜 및 시간](../../atl-mfc-shared/date-and-time.md)및 [시간 관리](../../c-runtime-library/time-management.md) 문서를 참조 하세요.

> [!NOTE]
> `CTime`구조가 mfc 7.1에서 mfc 8.0로 변경 되었습니다. `CTime`Mfc 8.0 이상 버전에서 **연산자 <<** 를 사용 하 여 구조체를 serialize 하는 경우 이전 버전의 mfc에서는 결과 파일을 읽을 수 없습니다.

## <a name="requirements"></a>요구 사항

**헤더:** 고 지 시간. h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a> CTime 비교 연산자

비교 연산자.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>매개 변수

*time*<br/>
비교할 `CTime` 개체입니다.

### <a name="return-value"></a>반환 값

이러한 연산자는 두 개의 절대 시간을 비교 하 고 조건이 true 이면 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a> CTime:: CTime

`CTime`지정 된 시간을 사용 하 여 초기화 된 새 개체를 만듭니다.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>매개 변수

*timeSrc*<br/>
`CTime`이미 존재 하는 개체를 나타냅니다.

*time*<br/>
`__time64_t`시간 값입니다 .이 값은 1970 UTC 이후의 시간 (초)입니다. 이는 현지 시간으로 조정 됩니다. 예를 들어 뉴욕에 있는 경우 `CTime` 0의 매개 변수를 전달 하 여 개체를 만들면 [CTime:: GetMonth](#getmonth) 는 12를 반환 합니다.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
새 개체에 복사할 날짜 및 시간 값을 나타냅니다 `CTime` .

*nDST*<br/>
일광 절약 시간이 적용 되는지 여부를 나타냅니다. 다음 세 가지 값 중 하나를 사용할 수 있습니다.

- *Ndst* 를 0standard time으로 설정 합니다.

- *0Daylight* 가 0daylight 절약 시간 보다 큰 값으로 설정 되어 있습니다.

- *Ndst* 는 기본값 0 보다 작은 값으로 설정 됩니다. 표준 시간 또는 일광 절약 시간이 적용 되는지 여부를 자동으로 계산 합니다.

*wDosDate*, *wDosTime*<br/>
날짜/시간 값으로 변환 되 고 새 개체로 복사 되는 MS-DOS 날짜 및 시간 값입니다 `CTime` .

*세인트*<br/>
날짜/시간 값으로 변환되고 새 `CTime`개체로 복사되는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체입니다.

*ft*<br/>
날짜/시간 값으로 변환되고 새 `CTime` 개체로 복사 되는 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조체입니다.

*dbts*<br/>
현재 현지 시간을 포함 하는 DBTIMESTAMP 구조체에 대 한 참조입니다.

### <a name="remarks"></a>설명

각 생성자에 대 한 설명은 다음과 같습니다.

- `CTime();` 초기화 되지 않은 `CTime` 개체를 생성 합니다. 이 생성자를 사용 하 여 `CTime` 개체 배열을 정의할 수 있습니다. 를 사용 하기 전에 유효한 시간으로 이러한 배열을 초기화 해야 합니다.

- `CTime( const CTime& );``CTime`다른 값에서 개체를 생성 `CTime` 합니다.

- `CTime( __time64_t );``CTime` **__Time64_t** 형식에서 개체를 생성 합니다. 이 생성자는 UTC 시간이 필요 하며 결과를 저장 하기 전에 결과를 현지 시간으로 변환 합니다.

- `CTime( int, int, ...);``CTime`각 구성 요소를 다음 범위로 제한 하는 로컬 시간 구성 요소에서 개체를 생성 합니다.

   |구성 요소|범위|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   이 생성자는 UTC로의 적절 한 변환을 수행 합니다. 하나 이상의 시간 구성 요소가 범위를 벗어난 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다. 를 호출 하기 전에 인수의 유효성을 검사 해야 합니다. 이 생성자에는 현지 시간이 필요 합니다.

- `CTime( WORD, WORD );` 지정 된 `CTime` MS-DOS 날짜 및 시간 값에서 개체를 생성 합니다. 이 생성자에는 현지 시간이 필요 합니다.

- `CTime( const SYSTEMTIME& );``CTime`구조체에서 개체를 생성 `SYSTEMTIME` 합니다. 이 생성자에는 현지 시간이 필요 합니다.

- `CTime( const FILETIME& );``CTime`구조체에서 개체를 생성 `FILETIME` 합니다. 초기화는 직접 사용 하지 않을 가능성이 높습니다 `CTime FILETIME` . 개체를 사용 하 여 파일을 조작 하는 경우는 `CFile` `CFile::GetStatus` 구조체를 `CTime` 사용 하 여 초기화 된 개체를 통해 파일 타임 스탬프를 검색 합니다 `FILETIME` . 이 생성자는 UTC를 기준으로 시간을 가정 하 고 결과를 저장 하기 전에 값을 현지 시간으로 자동으로 변환 합니다.

   > [!NOTE]
   > 매개 변수를 사용 하는 생성자는 `DBTIMESTAMP` OLEDB가 포함 된 경우에만 사용할 수 있습니다.

자세한 내용은 Windows SDK [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 및 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조를 참조 하세요. 또한 Windows SDK의 [MS-DOS 날짜 및 시간](/windows/win32/SysInfo/ms-dos-date-and-time) 항목을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a> CTime:: Format

이 멤버 함수를 호출 하 여 날짜-시간 값의 형식이 지정 된 표현을 만듭니다.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
서식 지정 문자열과 유사한 형식 문자열 `printf` 입니다. 백분율 () 기호가 앞에 나오는 서식 지정 코드 `%` 는 해당 구성 요소로 대체 됩니다 `CTime` . 서식 문자열의 다른 문자는 변경 되지 않은 상태로 반환 된 문자열에 복사 됩니다. 형식 지정 코드 목록은 런타임 함수 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 을 참조 하세요.

*nFormatID*<br/>
이 형식을 식별 하는 문자열의 ID입니다.

### <a name="return-value"></a>반환 값

형식이 지정 된 시간을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

이 개체의 상태가 `CTime` null 이면 반환 값은 빈 문자열입니다.

이 메서드는 형식으로 지정 된 날짜/시간 값이 1970 년 1 월 1 일 자정에서 12 월 3000 31 일 까지의 UTC (협정 세계시) 범위에 속하지 않는 경우 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a> CTime:: FormatGmt

이 개체에 해당 하는 형식이 지정 된 문자열을 생성 `CTime` 합니다.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
서식 지정 문자열과 유사한 형식 지정 문자열을 지정 합니다 `printf` . 자세한 내용은 런타임 함수 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 을 참조 하세요.

*nFormatID*<br/>
이 형식을 식별 하는 문자열의 ID입니다.

### <a name="return-value"></a>반환 값

형식이 지정 된 시간을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

시간 값은 변환 되지 않으므로 UTC를 반영 합니다.

이 메서드는 형식으로 지정 된 날짜/시간 값이 1970 년 1 월 1 일 자정에서 12 월 3000 31 일 까지의 UTC (협정 세계시) 범위에 속하지 않는 경우 예외를 throw 합니다.

### <a name="example"></a>예제

[CTime:: Format](#format)의 예제를 참조 하세요.

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> CTime:: GetAsDBTIMESTAMP

개체에 저장 된 시간 정보를 `CTime` Win32 호환 DBTIMESTAMP 구조체로 변환 하려면이 멤버 함수를 호출 합니다.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>매개 변수

*dbts*<br/>
현재 현지 시간을 포함 하는 DBTIMESTAMP 구조체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

결과 시간을 참조 되는 *dbts* 구조체에 저장 합니다. `DBTIMESTAMP`이 함수에 의해 초기화 되는 데이터 구조의 `fraction` 멤버는 0으로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a> CTime:: GetAsSystemTime

개체에 저장 된 시간 정보를 `CTime` Win32 호환 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체로 변환 하려면이 멤버 함수를 호출 합니다.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>매개 변수

*timeDest*<br/>
개체의 변환 된 날짜/시간 값을 보유 하는 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 참조입니다 `CTime` .

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

`GetAsSystemTime` 결과 시간을 참조 된 *Timedest* 구조에 저장 합니다. `SYSTEMTIME`이 함수에 의해 초기화 되는 데이터 구조의 `wMilliseconds` 멤버는 0으로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a> CTime:: GetCurrentTime

`CTime`현재 시간을 나타내는 개체를 반환 합니다.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>설명

현재 시스템 날짜 및 시간을 UTC (협정 세계시)로 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a> CTime:: GetDay

개체에 의해 표시 되는 일을 반환 합니다 `CTime` .

```
int GetDay() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 1에서 31 사이의 날짜를 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a> CTime:: GetDayOfWeek

개체가 나타내는 요일을 반환 합니다 `CTime` .

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 요일을 반환 합니다. 1 = 일요일, 2 = 월요일, 7 = 토요일

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a> CTime:: GetGmtTm

이 개체에 포함 된 시간의 분해를 포함 하는 **struct tm** 을 가져옵니다 `CTime` .

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*ptm*<br/>
는 시간 데이터를 수신 하는 버퍼를 가리킵니다. 이 포인터가 NULL 이면 예외가 throw 됩니다.

### <a name="return-value"></a>반환 값

포함 파일 시간 .H에 정의 된 대로 채워진 **struct tm** 에 대 한 포인터입니다. 구조 레이아웃에 대해서는 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 을 참조 하세요.

### <a name="remarks"></a>설명

`GetGmtTm` UTC를 반환 합니다.

*ptm* 은 NULL 일 수 없습니다. 정적으로 할당 된 내부 버퍼를 사용 해야 함을 나타내기 위해 *ptm* 이 NULL 일 수 있는 이전 동작으로 되돌리려면 _SECURE_ATL를 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a> CTime:: Gethour-해당

개체가 나타내는 시간을 반환 합니다 `CTime` .

```
int GetHour() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 0에서 23 사이의 시간을 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a> CTime:: GetLocalTm

이 개체에 포함 된 시간의 분해를 포함 하는 **struct tm** 을 가져옵니다 `CTime` .

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>매개 변수

*ptm*<br/>
는 시간 데이터를 수신 하는 버퍼를 가리킵니다. 이 포인터가 NULL 이면 예외가 throw 됩니다.

### <a name="return-value"></a>반환 값

포함 파일 시간 .H에 정의 된 대로 채워진 **struct tm** 에 대 한 포인터입니다. 구조 레이아웃에 대해서는 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 을 참조 하세요.

### <a name="remarks"></a>설명

`GetLocalTm` 현지 시간을 반환 합니다.

*ptm* 은 NULL 일 수 없습니다. 정적으로 할당 된 내부 버퍼를 사용 해야 함을 나타내기 위해 *ptm* 이 NULL 일 수 있는 이전 동작으로 되돌리려면 _SECURE_ATL를 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a> CTime:: GetMinute

개체가 나타내는 분을 반환 합니다 `CTime` .

```
int GetMinute() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 0에서 59 사이의 분을 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[Gethour-해당](#gethour)의 예제를 참조 하세요.

## <a name="ctimegetmonth"></a><a name="getmonth"></a> CTime:: GetMonth

개체가 나타내는 월을 반환 `CTime` 합니다.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 1부터 12 까지의 시간 (1 = 1 월)을 기준으로 월을 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[Getday](#getday)의 예제를 참조 하세요.

## <a name="ctimegetsecond"></a><a name="getsecond"></a> CTime:: GetSecond

개체가 나타내는 두 번째를 반환 합니다 `CTime` .

```
int GetSecond() const throw();
```

### <a name="return-value"></a>반환 값

현지 시간을 기준으로 0에서 59 사이의 두 번째를 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[Gethour-해당](#gethour)의 예제를 참조 하세요.

## <a name="ctimegettime"></a><a name="gettime"></a> CTime:: GetTime

지정 된 개체에 대 한 **__time64_t** 값을 반환 `CTime` 합니다.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>반환 값

`GetTime` 는 현재 `CTime` 개체와 1970 년 1 월 1 일 사이의 시간 (초)을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a> CTime:: GetYear

개체가 나타내는 연도를 반환 합니다 `CTime` .

```
int GetYear();
```

### <a name="return-value"></a>반환 값

1970 년 1 월 1 일부 터 2038 (포함) 사이의 현지 시간을 기준으로 연도를 반환 합니다.

### <a name="remarks"></a>설명

이 함수 `GetLocalTm` 는 정적으로 할당 된 내부 버퍼를 사용 하는를 호출 합니다. 다른 멤버 함수에 대 한 호출로 인해이 버퍼의 데이터를 덮어씁니다 `CTime` .

### <a name="example"></a>예제

[Getday](#getday)의 예제를 참조 하세요.

## <a name="ctimeoperator-"></a><a name="operator_eq"></a> CTime:: operator =

할당 연산자입니다.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>매개 변수

*time*<br/>
새 날짜/시간 값입니다.

### <a name="return-value"></a>반환 값

업데이트 된 `CTime` 개체입니다.

### <a name="remarks"></a>설명

이 오버 로드 된 할당 연산자는 소스 시간을이 개체에 복사 `CTime` 합니다. 개체의 내부 시간 저장소는 `CTime` 표준 시간대에 독립적입니다. 할당 하는 동안 표준 시간대 변환은 필요 하지 않습니다.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a> CTime:: operator +,-

이러한 연산자는 및 개체를 추가 하 고 뺍니다 `CTimeSpan` `CTime` .

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>매개 변수

*timeSpan*<br/>
`CTimeSpan`추가 하거나 뺄 개체입니다.

*time*<br/>
`CTime`뺄 개체입니다.

### <a name="return-value"></a>반환 값

`CTime` `CTimeSpan` 작업의 결과를 나타내는 또는 개체입니다.

### <a name="remarks"></a>설명

`CTime` 개체는 절대 시간을 나타내고 `CTimeSpan` 개체는 상대 시간을 나타냅니다. 처음 두 연산자를 사용 하면 개체를 개체에 추가 하 고 개체에서 뺄 수 있습니다 `CTimeSpan` `CTime` . 세 번째 연산자를 사용 하면 한 `CTime` 개체를 다른 개체에서 빼서 개체를 생성할 수 있습니다 `CTimeSpan` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a> CTime:: operator + =,-=

이러한 연산자는 개체를 추가 하 고 `CTimeSpan` 이 개체에서 뺍니다 `CTime` .

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
`CTimeSpan`추가 하거나 뺄 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 `CTime` 개체입니다.

### <a name="remarks"></a>설명

이러한 연산자를 사용 하 여 개체를 `CTimeSpan` 이 개체에 추가 하 고이 개체에서 뺄 수 있습니다 `CTime` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a> CTime:: Serialize64

> [!NOTE]
> 이 메서드는 MFC 프로젝트 에서만 사용할 수 있습니다.

멤버 변수와 연결 된 데이터를 보관 파일에서 또는 그 반대로 serialize 합니다.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
`CArchive`업데이트 하려는 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 `CArchive` 개체입니다.

## <a name="see-also"></a>참고 항목

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan 클래스](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)

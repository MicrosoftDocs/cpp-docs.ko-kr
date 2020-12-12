---
description: '다음에 대 한 자세한 정보: CFileTime 클래스'
title: CFileTime 클래스
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: 95b46c188be60da787612a30ebff161a4ecf5966
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166852"
---
# <a name="cfiletime-class"></a>CFileTime 클래스

이 클래스는 파일과 연결 된 날짜 및 시간 값을 관리 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFileTime:: CFileTime](#cfiletime)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFileTime:: GetCurrentTime](#getcurrenttime)|현재 시스템 날짜 및 시간을 나타내는 개체를 검색 하려면이 정적 함수를 호출 `CFileTime` 합니다.|
|[CFileTime:: GetTime](#gettime)|개체에서 시간을 검색 하려면이 메서드를 호출 `CFileTime` 합니다.|
|[CFileTime:: LocalToUTC](#localtoutc)|UTC (협정 세계시)를 기준으로 로컬 파일 시간을 파일 시간으로 변환 하려면이 메서드를 호출 합니다.|
|[CFileTime:: SetTime](#settime)|개체에 저장 된 날짜 및 시간을 설정 하려면이 메서드를 호출 `CFileTime` 합니다.|
|[CFileTime:: UTCToLocal](#utctolocal)|UTC (협정 세계시)를 기준으로 시간을 로컬 파일 시간으로 변환 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CFileTime:: operator-](#operator_-)|이 연산자는 또는 개체에서 빼기를 수행 하는 데 사용 됩니다 `CFileTime` `CFileTimeSpan` .|
|[CFileTime:: operator! =](#operator_neq)|이 연산자는 두 `CFileTime` 개체가 같지 않은지 비교 합니다.|
|[CFileTime:: operator +](#operator_add)|이 연산자는 `CFileTimeSpan` 개체에 대해 더하기를 수행하는 데 사용됩니다.|
|[CFileTime:: operator + =](#operator_add_eq)|이 연산자는 `CFileTimeSpan` 개체에 대해 더하기를 수행하고 결과를 현재 개체에 할당하는 데 사용됩니다.|
|[CFileTime:: operator &lt;](#operator_lt)|이 연산자는 두 `CFileTime` 개체를 비교하여 더 작은 값을 확인합니다.|
|[CFileTime:: operator &lt;=](#operator_lt_eq)|이 연산자는 두 `CFileTime` 개체를 비교하여 더 작거나 같은 값을 확인합니다.|
|[CFileTime:: operator =](#operator_eq)|할당 연산자입니다.|
|[CFileTime:: operator-=](#operator_-_eq)|이 연산자는 개체에 대해 빼기를 수행 하 `CFileTimeSpan` 고 결과를 현재 개체에 할당 하는 데 사용 됩니다.|
|[CFileTime:: operator = =](#operator_eq_eq)|이 연산자는 두 `CFileTime` 개체가 같은지 비교합니다.|
|[CFileTime:: operator &gt;](#operator_gt)|이 연산자는 두 `CFileTime` 개체를 비교하여 더 큰 값을 확인합니다.|
|[CFileTime:: operator &gt;=](#operator_gt_eq)|이 연산자는 두 `CFileTime` 개체를 비교하여 더 크거나 같은 값을 확인합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[CFileTime::D ay](#day)|1 일을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|
|[CFileTime:: Hour](#hour)|1 시간을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|
|[CFileTime:: 밀리초](#millisecond)|1 밀리초를 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|
|[CFileTime:: Minute](#minute)|1 분을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|
|[CFileTime:: Second](#second)|1 초를 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|
|[CFileTime:: Week](#week)|1 주를 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.|

## <a name="remarks"></a>설명

이 클래스는 파일의 생성, 액세스 및 수정과 관련 된 날짜 및 시간 값을 관리 하기 위한 메서드를 제공 합니다. 이 클래스의 메서드 및 데이터는 `CFileTimeSpan` 상대 시간 값을 처리 하는 개체와 함께 자주 사용 됩니다.

날짜 및 시간 값은 1601 1 월 1 일 이후 100 나노초 간격의 수를 나타내는 64 비트 값으로 저장 됩니다. UTC (협정 세계시) 형식입니다.

계산을 간소화 하기 위해 다음과 같은 정적 const 멤버 변수가 제공 됩니다.

|멤버 변수|100-나노초 간격 수|
|---------------------|-----------------------------------------|
|Millisecond|10000|
|Second|밀리초 \* 1000|
|Minute|초 \* 60|
|시간|분 \* 60|
|일|시간 \* 24|
|주|\*7 일|

**참고** 모든 파일 시스템에서 작성 및 마지막 액세스 시간을 기록할 수 있는 것은 아니므로 모든 파일 시스템이 같은 방식으로 기록 하는 것은 아닙니다. 예를 들어 Windows NT FAT 파일 시스템에서 만들기 시간이 10 밀리초를 확인 하 고, 쓰기 시간의 해상도는 2 초 이며, 액세스 시간에는 1 일 (액세스 날짜)의 해결 방법이 있습니다. NTFS에서 액세스 시간은 1 시간으로 확인 됩니다. 또한 FAT는 로컬 시간에 디스크에서 시간을 기록 하지만 NTFS는 UTC로 디스크에 시간을 기록 합니다. 자세한 내용은 [파일 시간](/windows/win32/SysInfo/file-times)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`FILETIME`

`CFileTime`

## <a name="requirements"></a>요구 사항

**헤더:** 고 지 시간. h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a> CFileTime:: CFileTime

생성자입니다.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 구조체입니다.

*않았습니다*<br/>
64 비트 값으로 표시 되는 날짜와 시간입니다.

### <a name="remarks"></a>설명

`CFileTime`구조체의 기존 날짜 및 시간을 사용 하 여 개체를 만들거나 `FILETIME` 현지 또는 Utc (협정 세계시) 시간 형식으로 64 비트 값으로 나타낼 수 있습니다. 기본 생성자는 시간을 0으로 설정 합니다.

## <a name="cfiletimeday"></a><a name="day"></a> CFileTime::D ay

1 일을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>예제

[Cfiletime:: 밀리초](#millisecond)의 예제를 참조 하세요.

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a> CFileTime:: GetCurrentTime

현재 시스템 날짜 및 시간을 나타내는 개체를 검색 하려면이 정적 함수를 호출 `CFileTime` 합니다.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>반환 값

현재 시스템 날짜 및 시간을 UTC (협정 세계시) 형식으로 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a> CFileTime:: GetTime

개체에서 시간을 검색 하려면이 메서드를 호출 `CFileTime` 합니다.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>반환 값

날짜 및 시간을 현지 또는 UTC (협정 세계시) 형식일 수 있는 64 비트 숫자로 반환 합니다.

## <a name="cfiletimehour"></a><a name="hour"></a> CFileTime:: Hour

1 시간을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>예제

[Cfiletime:: 밀리초](#millisecond)의 예제를 참조 하세요.

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a> CFileTime:: LocalToUTC

UTC (협정 세계시)를 기준으로 로컬 파일 시간을 파일 시간으로 변환 하려면이 메서드를 호출 합니다.

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>반환 값

`CFileTime`UTC 형식의 시간을 포함 하는 개체를 반환 합니다.

### <a name="example"></a>예제

[Cfiletime:: UTCToLocal](#utctolocal)에 대 한 예제를 참조 하세요.

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a> CFileTime:: 밀리초

1 밀리초를 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a> CFileTime:: Minute

1 분을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>예제

[Cfiletime:: 밀리초](#millisecond)의 예제를 참조 하세요.

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a> CFileTime:: operator-

이 연산자는 또는 개체에서 빼기를 수행 하는 데 사용 됩니다 `CFileTime` `CFileTimeSpan` .

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
`CFileTimeSpan` 개체입니다.

*ft*<br/>
`CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

`CFileTime` `CFileTimeSpan` 두 개체 간의 시간 차이에 대 한 결과를 나타내는 개체 또는 개체를 반환 합니다.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a> CFileTime:: operator! =

이 연산자는 두 `CFileTime` 개체가 같지 않은지 비교 합니다.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

비교할 항목이 개체와 같지 않으면 TRUE `CFileTime` 를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a> CFileTime:: operator +

이 연산자는 `CFileTimeSpan` 개체에 대해 더하기를 수행하는 데 사용됩니다.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
`CFileTimeSpan` 개체입니다.

### <a name="return-value"></a>반환 값

`CFileTime`원래 시간에 상대 시간을 더한 결과를 나타내는 개체를 반환 합니다.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a> CFileTime:: operator + =

이 연산자는 `CFileTimeSpan` 개체에 대해 더하기를 수행하고 결과를 현재 개체에 할당하는 데 사용됩니다.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
`CFileTimeSpan` 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 합니다 `CFileTime` .이 개체는 원래 시간에 상대 시간을 더한 결과를 나타냅니다.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a> CFileTime:: operator &lt;

이 연산자는 두 `CFileTime` 개체를 비교하여 더 작은 값을 확인합니다.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

첫 번째 개체가 두 번째 개체 보다 작은 경우 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a> CFileTime:: operator &lt;=

이 연산자는 두 `CFileTime` 개체를 비교하여 더 작거나 같은 값을 확인합니다.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

첫 번째 개체가 (이전 시간) 보다 작거나 두 번째 개체와 같으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a> CFileTime:: operator =

할당 연산자입니다.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
`CFileTime`새 시간 및 날짜를 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CFileTime` 합니다.

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a> CFileTime:: operator-=

이 연산자는 개체에 대해 빼기를 수행 하 `CFileTimeSpan` 고 결과를 현재 개체에 할당 하는 데 사용 됩니다.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
`CFileTimeSpan`뺄 상대 시간을 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CFileTime` 합니다.

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a> CFileTime:: operator = =

이 연산자는 두 `CFileTime` 개체가 같은지 비교합니다.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

개체가 같으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a> CFileTime:: operator &gt;

이 연산자는 두 `CFileTime` 개체를 비교하여 더 큰 값을 확인합니다.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

첫 번째 개체가 두 번째 개체 보다 크면 TRUE이 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a> CFileTime:: operator &gt;=

이 연산자는 두 `CFileTime` 개체를 비교하여 더 크거나 같은 값을 확인합니다.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>매개 변수

*ft*<br/>
비교할 `CFileTime` 개체입니다.

### <a name="return-value"></a>반환 값

첫 번째 개체가 (이후 시간) 보다 크거나 두 번째 개체와 같으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cfiletimesecond"></a><a name="second"></a> CFileTime:: Second

1 일을 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>예제

[Cfiletime:: 밀리초](#millisecond)의 예제를 참조 하세요.

## <a name="cfiletimesettime"></a><a name="settime"></a> CFileTime:: SetTime

개체에 저장 된 날짜 및 시간을 설정 하려면이 메서드를 호출 `CFileTime` 합니다.

```cpp
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>매개 변수

*않았습니다*<br/>
날짜 및 시간을 현지 또는 UTC (협정 세계시) 형식으로 나타내는 64 비트 값입니다.

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a> CFileTime:: UTCToLocal

UTC (협정 세계시)를 기준으로 시간을 로컬 파일 시간으로 변환 하려면이 메서드를 호출 합니다.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>반환 값

`CFileTime`현지 파일 시간 형식의 시간을 포함 하는 개체를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a> CFileTime:: Week

1 주를 구성 하는 100 나노초 간격의 수를 저장 하는 정적 데이터 멤버입니다.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>예제

[Cfiletime:: 밀리초](#millisecond)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan 클래스](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)

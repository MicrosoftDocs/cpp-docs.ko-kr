---
title: COleDateTimeSpan 클래스
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 5934a456b519d14def14018f966c7bff8206c3c4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500139"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 클래스

시간 범위에 상대적인 시간을 나타냅니다.

## <a name="syntax"></a>구문

```
class COleDateTimeSpan
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|`COleDateTimeSpan` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDateTimeSpan:: Format](#format)|개체의 형식이 지정 된 문자열 표현을 생성 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetDays](#getdays)|이 개체가 나타내는 범위의 일 부분을 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetHours](#gethours)|이 개체가 나타내는 범위의 시간 부분을 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetMinutes](#getminutes)|이 개체가 나타내는 범위에서 분 부분을 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetSeconds](#getseconds)|이 개체가 나타내는 범위의 두 번째 부분을 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetStatus](#getstatus)|이 개체의 상태 (유효성)를 가져옵니다 `COleDateTimeSpan` .|
|[COleDateTimeSpan:: GetTotalDays](#gettotaldays)|이 개체가 나타내는 일 수를 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetTotalHours](#gettotalhours)|이 개체가 나타내는 시간 수를 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: GetTotalMinutes](#gettotalminutes)|이 개체가 나타내는 시간 (분)을 반환 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|이 개체가 나타내는 시간 (초)을 반환 합니다 `COleDateTimeSpan` .|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|이 개체의 값을 설정 합니다 `COleDateTimeSpan` .|
|[COleDateTimeSpan:: SetStatus](#setstatus)|이 개체의 상태 (유효성)를 설정 합니다 `COleDateTimeSpan` .|

### <a name="public-operators"></a>Public 연산자

|속성|설명|
|-|-|
|[연산자 +,-](#operator_add_-)|값의 부호를 추가, 빼기 및 변경 `COleDateTimeSpan` 합니다.|
|[operator + =,-=](#operator_add_eq_-_eq)|`COleDateTimeSpan`이 값에서 값을 더하거나 뺍니다 `COleDateTimeSpan` .|
|[연산자 =](#operator_eq)|값을 복사 `COleDateTimeSpan` 합니다.|
|[operator = =, <, <=](#coledatetimespan_relational_operators)|두 `COleDateTimeSpan` 값을 비교 합니다.|
|[operator double](#operator_double)|이 값을로 변환 `COleDateTimeSpan` **`double`** 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|속성|설명|
|----------|-----------------|
|[COleDateTimeSpan:: m_span](#m_span)|**`double`** 이 개체의 내부를 포함 `COleDateTimeSpan` 합니다.|
|[COleDateTimeSpan:: m_status](#m_status)|이 개체의 상태를 포함 `COleDateTimeSpan` 합니다.|

## <a name="remarks"></a>설명

`COleDateTimeSpan` 에 기본 클래스가 없습니다.

은 `COleDateTimeSpan` (는) 시간 (일)을 유지 합니다.

`COleDateTimeSpan` 는 동반 클래스 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)와 함께 사용 됩니다. `COleDateTime``DATE`OLE 자동화의 데이터 형식을 캡슐화 합니다. `COleDateTime` 절대 시간 값을 나타냅니다. 모든 `COleDateTime` 계산에는 값이 포함 `COleDateTimeSpan` 됩니다. 이러한 클래스 간의 관계는 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 과 [ctimespan](../../atl-mfc-shared/reference/ctimespan-class.md)간의 관계와 유사 합니다.

및 클래스에 대 한 자세한 내용은 `COleDateTime` `COleDateTimeSpan` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 없음. h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a> COleDateTimeSpan 관계형 연산자

비교 연산자.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>매개 변수

*dateSpan*<br/>
비교할 `COleDateTimeSpan`입니다.

### <a name="return-value"></a>반환 값

이러한 연산자는 두 개의 날짜/시간 범위 값을 비교 하 고 조건이 true 이면 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 두 피연산자 중 하나가 잘못 된 경우에는가 없는 어설션이 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a> COleDateTimeSpan::COleDateTimeSpan

`COleDateTimeSpan` 개체를 생성합니다.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>매개 변수

*dblSpanSrc*<br/>
새 개체에 복사할 일 수입니다 `COleDateTimeSpan` .

*Ldays*, *nhours*, *nhours*, *nhours*<br/>
새 개체에 복사할 날짜 및 시간 값을 지정 `COleDateTimeSpan` 합니다.

### <a name="remarks"></a>설명

이러한 모든 생성자는 지정 된 `COleDateTimeSpan` 값으로 초기화 된 새 개체를 만듭니다. 이러한 각 생성자에 대 한 간략 한 설명은 다음과 같습니다.

- **COleDateTimeSpan ()** `COleDateTimeSpan` 0으로 초기화 되는 개체를 생성 합니다.

- **COleDateTimeSpan (** `dblSpanSrc` **)** 는 `COleDateTimeSpan` 부동 소수점 값에서 개체를 생성 합니다.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** 는 `COleDateTimeSpan` 지정 된 숫자 값으로 초기화 되는 개체를 생성 합니다.

새 개체의 상태가 `COleDateTimeSpan` valid로 설정 됩니다.

값의 범위에 대 한 자세한 내용은 `COleDateTimeSpan` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a> COleDateTimeSpan:: Format

개체의 형식이 지정 된 문자열 표현을 생성 `COleDateTimeSpan` 합니다.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>매개 변수

*pFormat*<br/>
서식 지정 문자열과 유사한 형식 문자열 `printf` 입니다. 백분율 () 기호가 앞에 나오는 서식 지정 코드 `%` 는 해당 구성 요소로 대체 됩니다 `COleDateTimeSpan` . 서식 문자열의 다른 문자는 변경 되지 않은 상태로 반환 된 문자열에 복사 됩니다. 에 대 한 서식 지정 코드의 값과 의미는 `Format` 다음과 같습니다.

- **% H** 현재 날짜의 시간

- **% M** 현재 시간의 분

- **% S** 현재 분의 초

- **%%** 백분율 기호

위에 나열 된 네 가지 형식 코드는 형식에서 허용 하는 유일한 코드입니다.

-

*nID*<br/>
형식 컨트롤 문자열에 대 한 리소스 ID입니다.

### <a name="return-value"></a>반환 값

`CString`형식이 지정 된 날짜/시간 범위 값을 포함 하는입니다.

### <a name="remarks"></a>설명

이러한 함수를 호출 하 여 시간 범위 값의 형식이 지정 된 표현을 만듭니다. 이 개체의 상태가 `COleDateTimeSpan` null 이면 반환 값은 빈 문자열입니다. 상태가 잘못 된 경우 문자열 리소스 IDS_INVALID_DATETIMESPAN에 의해 반환 문자열이 지정 됩니다.

이 함수의 폼에 대 한 간략 한 설명은 다음과 같습니다.

**Format (** *pformat* **)**<br/>
이 폼은에서와 같이 백분율 기호 (%)가 앞에 나오는 특수 서식 지정 코드가 포함 된 서식 문자열을 사용 하 여 값의 서식을 지정 합니다 `printf` . 형식 문자열은 함수에 매개 변수로 전달 됩니다.

**Format (** *nID* **)**<br/>
이 폼은에서와 같이 백분율 기호 (%)가 앞에 나오는 특수 서식 지정 코드가 포함 된 서식 문자열을 사용 하 여 값의 서식을 지정 합니다 `printf` . 형식 문자열은 리소스입니다. 이 문자열 리소스의 ID는 매개 변수로 전달 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a> COleDateTimeSpan:: GetDays

이 날짜/시간 범위 값의 일 부분을 검색 합니다.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값의 일 부분입니다.

### <a name="remarks"></a>설명

이 함수의 반환 값 범위는 약-3615000 ~ 3615000입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a> COleDateTimeSpan:: GetHours

이 날짜/시간 범위 값의 시간 부분을 검색 합니다.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값의 시간 부분입니다.

### <a name="remarks"></a>설명

이 함수의 반환 값 범위는-23에서 23 사이입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a> COleDateTimeSpan:: GetMinutes

이 날짜/시간 범위 값의 분 부분을 검색 합니다.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값의 분 부분입니다.

### <a name="remarks"></a>설명

이 함수의 반환 값 범위는-59에서 59 사이입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a> COleDateTimeSpan:: GetSeconds

이 날짜/시간 범위 값의 초 부분을 검색 합니다.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값의 초 부분입니다.

### <a name="remarks"></a>설명

이 함수의 반환 값 범위는-59에서 59 사이입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a> COleDateTimeSpan:: GetStatus

이 개체의 상태 (유효성)를 가져옵니다 `COleDateTimeSpan` .

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>반환 값

이 값의 상태 `COleDateTimeSpan` 입니다.

### <a name="remarks"></a>설명

반환 값은 `DateTimeSpanStatus` 클래스 내에 정의 된 열거형 형식에 의해 정의 됩니다 `COleDateTimeSpan` .

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleDateTimeSpan::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleDateTimeSpan` .

- `COleDateTimeSpan::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleDateTimeSpan` , 해당 값이 잘못 되었을 수 있습니다.

- `COleDateTimeSpan::null` 이 `COleDateTimeSpan` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

개체의 상태는 `COleDateTimeSpan` 다음과 같은 경우 유효 하지 않습니다.

- 산술 할당 작업 중이 개체에 오버플로 또는 언더플로가 발생 한 경우, 즉 `+=` 또는 `-=` 입니다.

- 이 개체에 잘못 된 값이 할당 된 경우

- 이 개체의 상태가를 사용 하 여 명시적으로 잘못 설정 된 경우 `SetStatus` 입니다.

상태를 잘못 된 것으로 설정할 수 있는 작업에 대 한 자세한 내용은 [COleDateTimeSpan:: operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) and [COleDateTimeSpan:: operator + =,-=를](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)참조 하세요.

값의 범위에 대 한 자세한 내용은 `COleDateTimeSpan` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a> COleDateTimeSpan:: GetTotalDays

일 단위로 표시 되는이 날짜/시간 범위 값을 검색 합니다.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값 (일)입니다. 이 함수는 double을 반환 하기 위해 프로토타입화 되지만 항상 정수 값을 반환 합니다.

### <a name="remarks"></a>설명

이 함수에서 반환 되는 값의 범위는 약 3.65 e6 및 3.65 e6입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a> COleDateTimeSpan:: GetTotalHours

시간으로 표시 된이 날짜/시간 범위 값을 검색 합니다.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>반환 값

시간으로 표시 된이 날짜/시간 범위 값입니다. 이 함수는 double을 반환 하기 위해 프로토타입화 되지만 항상 정수 값을 반환 합니다.

### <a name="remarks"></a>설명

이 함수에서 반환 되는 값의 범위는 약 8.77 e7 및 8.77 e7입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[Gettotaldays](#gettotaldays)의 예제를 참조 하세요.

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a> COleDateTimeSpan:: GetTotalMinutes

분 단위로 표현 된이 날짜/시간 범위 값을 검색 합니다.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>반환 값

이 날짜/시간 범위 값 (분)입니다. 이 함수는 double을 반환 하기 위해 프로토타입화 되지만 항상 정수 값을 반환 합니다.

### <a name="remarks"></a>설명

이 함수에서 반환 되는 값의 범위는 약 5.26 e9 및 5.26 e9입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[Gettotaldays](#gettotaldays)의 예제를 참조 하세요.

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a> COleDateTimeSpan::GetTotalSeconds

초 단위로 표시 되는이 날짜/시간 범위 값을 검색 합니다.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>반환 값

초 단위로 표시 되는이 날짜/시간 범위 값입니다. 이 함수는 double을 반환 하기 위해 프로토타입화 되지만 항상 정수 값을 반환 합니다.

### <a name="remarks"></a>설명

이 함수의 반환 값은 대략 3.16 e11에서 3.16 e11 까지입니다.

개체의 값을 쿼리 하는 다른 함수의 경우에는 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>예제

[Gettotaldays](#gettotaldays)의 예제를 참조 하세요.

## <a name="coledatetimespanm_span"></a><a name="m_span"></a> COleDateTimeSpan:: m_span

**`double`** 이 개체의 내부 값 `COleDateTime` 입니다.

```
double m_span;
```

### <a name="remarks"></a>설명

이 값은 일 단위로 날짜/시간 범위를 나타냅니다.

> [!CAUTION]
> 데이터 멤버의 값을 변경 **`double`** 하면이 개체의 값이 변경 됩니다 `COleDateTimeSpan` . 이 개체의 상태는 변경 되지 않습니다 `COleDateTimeSpan` .

## <a name="coledatetimespanm_status"></a><a name="m_status"></a> COleDateTimeSpan:: m_status

이 데이터 멤버의 형식은 클래스 내에 정의 된 열거형 형식입니다 `DateTimeSpanStatus` `COleDateTimeSpan` .

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>설명

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleDateTimeSpan::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleDateTimeSpan` .

- `COleDateTimeSpan::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleDateTimeSpan` , 해당 값이 잘못 되었을 수 있습니다.

- `COleDateTimeSpan::null` 이 `COleDateTimeSpan` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

개체의 상태는 `COleDateTimeSpan` 다음과 같은 경우 유효 하지 않습니다.

- 산술 할당 작업 중이 개체에 오버플로 또는 언더플로가 발생 한 경우, 즉 `+=` 또는 `-=` 입니다.

- 이 개체에 잘못 된 값이 할당 된 경우

- 이 개체의 상태가 [SetStatus](#setstatus)를 사용 하 여 명시적으로 잘못 설정 된 경우입니다.

상태를 잘못 된 것으로 설정할 수 있는 작업에 대 한 자세한 내용은 [COleDateTimeSpan:: operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) and [COleDateTimeSpan:: operator + =,-=를](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)참조 하세요.

> [!CAUTION]
> 이 데이터 멤버는 고급 프로그래밍 상황을 위한 것입니다. 인라인 멤버 함수 [GetStatus](#getstatus) 및 [SetStatus](#setstatus)를 사용 해야 합니다. `SetStatus`이 데이터 멤버를 명시적으로 설정 하는 방법에 대 한 자세한 내용은을 참조 하십시오.

값의 범위에 대 한 자세한 내용은 `COleDateTimeSpan` [날짜 및 시간: 자동화 지원](../date-and-time.md)문서를 참조 하세요.

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a> COleDateTimeSpan:: operator =

값을 복사 `COleDateTimeSpan` 합니다.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>설명

이 오버 로드 된 할당 연산자는 원본 날짜/시간 범위 값을이 `COleDateTimeSpan` 개체에 복사 합니다.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a> COleDateTimeSpan:: operator +,-

값의 부호를 추가, 빼기 및 변경 `COleDateTimeSpan` 합니다.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>설명

처음 두 연산자를 사용 하 여 날짜/시간 범위 값을 더하거나 뺄 수 있습니다. 세 번째에서는 날짜/시간 범위 값의 부호를 변경할 수 있습니다.

피연산자 중 하나가 null 이면 결과 값의 상태가 `COleDateTimeSpan` null입니다.

피연산자 중 하나가 유효 하지 않은 경우 다른 피연산자가 null이 아니면 결과 값의 상태가 잘못 된 `COleDateTimeSpan` 것입니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTimeSpan:: operator + =,-=

`COleDateTimeSpan`이 값에서 값을 더하거나 뺍니다 `COleDateTimeSpan` .

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>설명

이러한 연산자를 사용 하 여이 개체에서 날짜/시간 범위 값을 더하거나 뺄 수 있습니다 `COleDateTimeSpan` . 피연산자 중 하나가 null 이면 결과 값의 상태가 `COleDateTimeSpan` null입니다.

피연산자 중 하나가 유효 하지 않은 경우 다른 피연산자가 null이 아니면 결과 값의 상태가 잘못 된 `COleDateTimeSpan` 것입니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a> COleDateTimeSpan:: operator double

이 값을로 변환 `COleDateTimeSpan` **`double`** 합니다.

```
operator double() const throw();
```

### <a name="remarks"></a>설명

이 연산자는이 값의 값을 `COleDateTimeSpan` 부동 소수점 일 수로 반환 합니다.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a> COleDateTimeSpan::SetDateTimeSpan

이 날짜/시간 범위 값의 값을 설정 합니다.

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>매개 변수

*Ldays*, *nhours*, *nhours*, *nhours*<br/>
이 개체에 복사할 날짜 범위 및 시간 범위 값을 지정 합니다 `COleDateTimeSpan` .

### <a name="remarks"></a>설명

개체의 값을 쿼리 하는 함수의 경우 `COleDateTimeSpan` 다음 멤버 함수를 참조 하세요.

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a> COleDateTimeSpan:: SetStatus

이 개체의 상태 (유효성)를 설정 합니다 `COleDateTimeSpan` .

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>매개 변수

*status*<br/>
이 개체의 새 상태 값 `COleDateTimeSpan` 입니다.

### <a name="remarks"></a>설명

*상태* 매개 변수 값은 `DateTimeSpanStatus` 클래스 내에서 정의 되는 열거 된 형식에 의해 정의 됩니다 `COleDateTimeSpan` .

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleDateTimeSpan::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleDateTimeSpan` .

- `COleDateTimeSpan::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleDateTimeSpan` , 해당 값이 잘못 되었을 수 있습니다.

- `COleDateTimeSpan::null` 이 `COleDateTimeSpan` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

   > [!CAUTION]
   > 이 함수는 고급 프로그래밍 상황을 위한 것입니다. 이 함수는이 개체의 데이터를 변경 하지 않습니다. 상태를 **null** 또는 **잘못**된 것으로 설정 하는 데 주로 사용 됩니다. 할당 연산자 ([operator =](#operator_eq)) 및 [SetDateTimeSpan](#setdatetimespan) 는 원본 값을 기준으로 개체의 상태를 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>참고 항목

[COleDateTime 클래스](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 클래스](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 클래스](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)

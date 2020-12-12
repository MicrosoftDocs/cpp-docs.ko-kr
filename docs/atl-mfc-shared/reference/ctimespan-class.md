---
description: '자세한 정보: CTimeSpan 클래스'
title: CTimeSpan 클래스
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: b15fa247baaa4de77c5caab12d584a80321b9420
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166579"
---
# <a name="ctimespan-class"></a>CTimeSpan 클래스

시간 범위의 초 수로 내부적으로 저장 되는 시간 간격입니다.

## <a name="syntax"></a>구문

```
class CTimeSpan
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CTimeSpan:: CTimeSpan](#ctimespan)|`CTimeSpan`여러 가지 방법으로 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTimeSpan:: Format](#format)|를 `CTimeSpan` 형식이 지정 된 문자열로 변환 합니다.|
|[CTimeSpan:: GetDays](#getdays)|이의 전체 일 수를 나타내는 값을 반환 합니다 `CTimeSpan` .|
|[CTimeSpan:: GetHours](#gethours)|현재 날짜의 시간 (-23 ~ 23)을 나타내는 값을 반환 합니다.|
|[CTimeSpan:: GetMinutes](#getminutes)|현재 시간 (-59 ~ 59)의 시간 (분)을 나타내는 값을 반환 합니다.|
|[CTimeSpan:: GetSeconds](#getseconds)|현재 분의 초 수를 나타내는 값을 반환 합니다 (-59 ~ 59).|
|[CTimeSpan:: GetTimeSpan](#gettimespan)|개체의 값을 반환 합니다 `CTimeSpan` .|
|[CTimeSpan:: GetTotalHours](#gettotalhours)|이에 있는 전체 시간 수를 나타내는 값을 반환 합니다 `CTimeSpan` .|
|[CTimeSpan:: GetTotalMinutes](#gettotalminutes)|이에서 전체 완료 된 분 수를 나타내는 값을 반환 합니다 `CTimeSpan` .|
|[CTimeSpan:: GetTotalSeconds](#gettotalseconds)|이에서 전체 초 수를 나타내는 값을 반환 `CTimeSpan` 합니다.|
|[CTimeSpan:: Serialize64](#serialize64)|보관 파일에서 데이터를 직렬화 합니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[operator +-](#operator_add_-)|개체를 추가 하거나 뺍니다 `CTimeSpan` .|
|[operator + =-=](#operator_add_eq_-_eq)|이에서 개체를 추가 하거나 뺍니다 `CTimeSpan` `CTimeSpan` .|
|[연산자 = = < 등](#ctimespan_comparison_operators)|두 상대 시간 값을 비교 합니다.|

## <a name="remarks"></a>설명

`CTimeSpan` 에 기본 클래스가 없습니다.

`CTimeSpan` 함수는 초, 시간, 분 및 초를 다양 하 게 조합 하 여 초를 변환 합니다.

`CTimeSpan`개체는 8 바이트인 **__time64_t** 구조에 저장 됩니다.

동반 클래스 [CTime](../../atl-mfc-shared/reference/ctime-class.md)은 절대 시간을 나타냅니다.

`CTime`및 `CTimeSpan` 클래스는 파생을 위해 디자인 되지 않았습니다. 가상 함수가 없으므로 및 개체의 크기는 `CTime` `CTimeSpan` 정확히 8 바이트입니다. 대부분의 멤버 함수는 인라인 함수입니다.

사용에 대 한 자세한 내용은 `CTimeSpan` *런타임 라이브러리 참조* 의 [날짜 및 시간](../../atl-mfc-shared/date-and-time.md)및 [시간 관리](../../c-runtime-library/time-management.md) 문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 고 지 시간. h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a> CTimeSpan 비교 연산자

비교 연산자.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
비교할 개체입니다.

### <a name="return-value"></a>반환 값

이러한 연산자는 두 개의 상대 시간 값을 비교 합니다. 조건이 true 이면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a> CTimeSpan:: CTimeSpan

`CTimeSpan`여러 가지 방법으로 개체를 생성 합니다.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>매개 변수

*timeSpanSrc*<br/>
`CTimeSpan`이미 존재 하는 개체입니다.

*time*<br/>
시간 범위의 초 수 인 **__time64_t** 시간 값입니다.

*Ldays*, *nhours*, *nhours*, *nhours*<br/>
일, 시, 분 및 초를 각각 허용 합니다.

### <a name="remarks"></a>설명

이러한 모든 생성자는 지정 된 `CTimeSpan` 상대 시간을 사용 하 여 초기화 된 새 개체를 만듭니다. 각 생성자에 대 한 설명은 다음과 같습니다.

- `CTimeSpan( );` 초기화 되지 않은 `CTimeSpan` 개체를 생성 합니다.

- `CTimeSpan( const CTimeSpan& );``CTimeSpan`다른 값에서 개체를 생성 `CTimeSpan` 합니다.

- `CTimeSpan( __time64_t );``CTimeSpan` **__Time64_t** 형식에서 개체를 생성 합니다.

- `CTimeSpan( LONG, int, int, int );``CTimeSpan`각 구성 요소를 다음 범위로 제한 하는 구성 요소에서 개체를 생성 합니다.

   |구성 요소|범위|
   |---------------|-----------|
   |*lDays*|0-25000 (대략)|
   |*nHours*|0-23|
   |*n 분*|0-59|
   |*nSecs*|0-59|

MFC 라이브러리 디버그 버전의 시간 구성 요소 중 하나 이상이 범위를 벗어난 경우 어설션이 어설션 됩니다. 를 호출 하기 전에 인수의 유효성을 검사 하는 것은 사용자의 책임입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a> CTimeSpan:: Format

이에 해당 하는 형식이 지정 된 문자열을 생성 `CTimeSpan` 합니다.

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>매개 변수

*Pformat*, *pszFormat*<br/>
서식 지정 문자열과 유사한 형식 문자열 `printf` 입니다. 백분율 () 기호가 앞에 나오는 서식 지정 코드 `%` 는 해당 구성 요소로 대체 됩니다 `CTimeSpan` . 서식 문자열의 다른 문자는 변경 되지 않은 상태로 반환 된 문자열에 복사 됩니다. 에 대 한 서식 지정 코드의 값과 의미는 `Format` 다음과 같습니다.

- **% D** 이의 총 일 수 `CTimeSpan`

- **% H** 현재 날짜의 시간

- **% M** 현재 시간의 분

- **% S** 현재 분의 초

- **%%** 백분율 기호

*nID*<br/>
이 형식을 식별 하는 문자열의 ID입니다.

### <a name="return-value"></a>반환 값

`CString`형식이 지정 된 시간을 포함 하는 개체입니다.

### <a name="remarks"></a>설명

라이브러리의 디버그 버전은 코드 형식이 위의 목록에 없는 경우 형식 지정 코드 및 어설션을 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a> CTimeSpan:: GetDays

이의 전체 일 수를 나타내는 값을 반환 합니다 `CTimeSpan` .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>반환 값

시간 범위의 전체 24 시간 일 수를 반환 합니다. 시간 범위가 음수 이면이 값은 음수일 수 있습니다.

### <a name="remarks"></a>설명

일광 절약 시간제 `GetDays` 로 인해 잠재적으로 놀라운 결과가 반환 될 수 있습니다. 예를 들어, DST가 적용 되는 경우은 4 월 `GetDays` 1 일의 일 수를 보고 하며, 4 월 1 일은 1 시간으로 단축 되기 때문에 전체 일 수는 없습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a> CTimeSpan:: GetHours

현재 날짜의 시간 (-23 ~ 23)을 나타내는 값을 반환 합니다.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>반환 값

현재 날짜의 시간 수를 반환 합니다. 범위는-23에서 23 까지입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a> CTimeSpan:: GetMinutes

현재 시간 (-59 ~ 59)의 시간 (분)을 나타내는 값을 반환 합니다.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>반환 값

현재 시간의 분 수를 반환 합니다. 범위는-59 ~ 59입니다.

### <a name="example"></a>예제

[GetHours](#gethours)의 예제를 참조 하세요.

## <a name="ctimespangetseconds"></a><a name="getseconds"></a> CTimeSpan:: GetSeconds

현재 분의 초 수를 나타내는 값을 반환 합니다 (-59 ~ 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>반환 값

현재 분의 초 수를 반환 합니다. 범위는-59 ~ 59입니다.

### <a name="example"></a>예제

[GetHours](#gethours)의 예제를 참조 하세요.

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a> CTimeSpan:: GetTimeSpan

개체의 값을 반환 합니다 `CTimeSpan` .

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>반환 값

개체의 현재 값을 반환 합니다 `CTimeSpan` .

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a> CTimeSpan:: GetTotalHours

이에 있는 전체 시간 수를 나타내는 값을 반환 합니다 `CTimeSpan` .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>반환 값

이의 총 전체 시간 수를 반환 합니다 `CTimeSpan` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a> CTimeSpan:: GetTotalMinutes

이에서 전체 완료 된 분 수를 나타내는 값을 반환 합니다 `CTimeSpan` .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>반환 값

이에서 전체 완료 된 분 수를 반환 합니다 `CTimeSpan` .

### <a name="example"></a>예제

[Gettotalhours](#gettotalhours)의 예제를 참조 하세요.

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a> CTimeSpan:: GetTotalSeconds

이에서 전체 초 수를 나타내는 값을 반환 `CTimeSpan` 합니다.

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>반환 값

이의 전체 전체 초 수를 반환 합니다 `CTimeSpan` .

### <a name="example"></a>예제

[Gettotalhours](#gettotalhours)의 예제를 참조 하세요.

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a> CTimeSpan:: operator +,-

개체를 추가 하거나 뺍니다 `CTimeSpan` .

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
개체에 추가할 값 `CTimeSpan` 입니다.

### <a name="return-value"></a>반환 값

`CTimeSpan`작업의 결과를 나타내는 개체입니다.

### <a name="remarks"></a>설명

이러한 두 연산자를 사용 하면 개체를 서로 추가 하 고 서로 뺄 수 있습니다 `CTimeSpan` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> CTimeSpan:: operator + =,-=

이에서 개체를 추가 하거나 뺍니다 `CTimeSpan` `CTimeSpan` .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>매개 변수

*거칠*<br/>
개체에 추가할 값 `CTimeSpan` 입니다.

### <a name="return-value"></a>반환 값

업데이트 된 `CTimeSpan` 개체입니다.

### <a name="remarks"></a>설명

이러한 연산자를 사용 하 여이에서 개체를 추가 하거나 뺄 수 있습니다 `CTimeSpan` `CTimeSpan` .

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a> CTimeSpan:: Serialize64

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

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)

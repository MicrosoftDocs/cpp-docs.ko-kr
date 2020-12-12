---
description: '자세히 알아보기: COleCurrency 클래스'
title: COleCurrency 클래스
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: 4a877d455de3f4254711a752bc422bb1cbdcd8c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227392"
---
# <a name="colecurrency-class"></a>COleCurrency 클래스

OLE 자동화의 `CURRENCY` 데이터 형식을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class COleCurrency
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleCurrency:: COleCurrency](#colecurrency)|`COleCurrency` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleCurrency:: Format](#format)|개체의 형식이 지정 된 문자열 표현을 생성 `COleCurrency` 합니다.|
|[COleCurrency:: GetStatus](#getstatus)|이 개체의 상태 (유효성)를 가져옵니다 `COleCurrency` .|
|[COleCurrency::P arseCurrency](#parsecurrency)|문자열에서 통화 값을 읽고의 값을 설정 합니다 `COleCurrency` .|
|[COleCurrency:: SetCurrency](#setcurrency)|이 개체의 값을 설정 합니다 `COleCurrency` .|
|[COleCurrency:: SetStatus](#setstatus)|이 개체의 상태 (유효성)를 설정 합니다 `COleCurrency` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[연산자 =](#operator_eq)|값을 복사 `COleCurrency` 합니다.|
|[연산자 +,-](#operator_plus_minus)|값의 부호를 추가, 빼기 및 변경 `COleCurrency` 합니다.|
|[operator + =,-=](#operator_plus_minus_eq)|`COleCurrency`이 개체의 값을 추가 하거나 뺍니다 `COleCurrency` .|
|[연산자 */](#operator_star)|`COleCurrency`정수 값을 기준으로 값의 배율을 조정 합니다.|
|[연산자 * =,/=](#operator_star_div_eq)|`COleCurrency`정수 값을 기준으로이 값의 배율을 조정 합니다.|
|[연산자 <<](#operator_stream)|`COleCurrency`또는에 값을 `CArchive` 출력 `CDumpContext` 합니다.|
|[연산자 >>](#operator_stream)|`COleCurrency`에서 개체를 입력 `CArchive` 합니다.|
|[연산자 통화](#operator_currency)|값을 `COleCurrency` 통화로 변환 합니다.|
|[operator = =, <, <= 등](#colecurrency_relational_operators)|두 `COleCurrency` 값을 비교 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|이 개체의 내부 통화를 포함 합니다 `COleCurrency` .|
|[COleCurrency:: m_status](#m_status)|이 개체의 상태를 포함 `COleCurrency` 합니다.|

## <a name="remarks"></a>설명

`COleCurrency` 에 기본 클래스가 없습니다.

CURRENCY는 1만으로 크기가 조정 된 8 바이트 2의 보수 정수 값으로 구현 됩니다. 소수점 기호 왼쪽에는 15자리 고정 소수점 번호가 있고 오른쪽에는 4자리 고정 소수점 번호가 있습니다. CURRENCY 데이터 형식은 money를 포함 하는 계산 또는 정확성이 중요 한 고정 소수점 계산에 매우 유용 합니다. OLE 자동화의 데이터 형식에 사용할 수 있는 형식 중 하나입니다 `VARIANT` .

`COleCurrency` 는 또한이 고정 소수점 형식에 대 한 몇 가지 기본 산술 연산을 구현 합니다. 지원 되는 작업을 선택 하 여 고정 소수점 계산 중에 발생 하는 반올림 오류를 제어 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`COleCurrency`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a> COleCurrency:: COleCurrency

`COleCurrency` 개체를 생성합니다.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>매개 변수

*cySrc*<br/>
새 개체에 복사할 통화 값 `COleCurrency` 입니다.

*curSrc*<br/>
`COleCurrency`새 개체에 복사할 기존 개체 `COleCurrency` 입니다.

*varSrc*<br/>
`VARIANT` `COleVariant` 통화 값 (VT_CY)으로 변환 되 고 새 개체로 복사 될 수 있는 기존 데이터 구조 (개체 일 수 있음) `COleCurrency` 입니다.

*Nunits*, *nFractionalUnits* 는 새 개체로 복사할 값의 단위 및 소수 부분 (1/10000)을 표시 합니다 `COleCurrency` .

### <a name="remarks"></a>설명

이러한 모든 생성자는 지정 된 `COleCurrency` 값으로 초기화 된 새 개체를 만듭니다. 이러한 각 생성자에 대 한 간략 한 설명은 다음과 같습니다. 별도로 언급 하지 않는 한 새 항목의 상태는 `COleCurrency` valid로 설정 됩니다.

- COleCurrency ()는 `COleCurrency` 0으로 초기화 되는 개체를 생성 합니다.

- COleCurrency ( `cySrc` )는 `COleCurrency` [통화](/windows/win32/api/wtypes/ns-wtypes-cy-r1) 값에서 개체를 생성 합니다.

- COleCurrency ( `curSrc` )는 `COleCurrency` 기존 개체에서 개체를 생성 `COleCurrency` 합니다. 새 개체의 상태는 원본 개체와 동일 합니다.

- COleCurrency ( `varSrc` )는 개체를 생성 `COleCurrency` 합니다. [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 구조체 또는 `COleVariant` 개체를 currency (VT_CY) 값으로 변환 하려고 합니다. 이 변환에 성공 하면 변환 된 값이 새 개체에 복사 됩니다 `COleCurrency` . 그렇지 않으면 개체의 값이 `COleCurrency` 0으로 설정 되 고 상태가 잘못 됨으로 설정 됩니다.

- COleCurrency ( `nUnits` , `nFractionalUnits` ) `COleCurrency` 은 지정 된 숫자 구성 요소에서 개체를 생성 합니다. 소수 부분의 절대값이 1만 보다 큰 경우 해당 단위에 적절 한 조정이 적용 됩니다. 단위 및 소수 부분은 부호 있는 long 값으로 지정 됩니다.

자세한 내용은 Windows SDK의 [통화](/windows/win32/api/wtypes/ns-wtypes-cy-r1) 및 [변형](/windows/win32/api/oaidl/ns-oaidl-variant) 항목을 참조 하세요.

### <a name="example"></a>예제

다음 예에서는 0 매개 변수 및 두 매개 변수 생성자의 영향을 보여 줍니다.

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a> COleCurrency:: Format

통화 값의 형식이 지정 된 표현을 만들려면이 멤버 함수를 호출 합니다.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
로캘 설정에 대 한 플래그를 나타냅니다. 통화와 관련 된 플래그는 다음과 같습니다.

- 사용자 지정 사용자 설정이 아닌 시스템 기본 로캘 설정을 사용 LOCALE_NOUSEROVERRIDE 합니다.

*lcid*<br/>
변환에 사용할 로캘 ID를 나타냅니다.

### <a name="return-value"></a>반환 값

`CString`서식이 지정 된 통화 값을 포함 하는입니다.

### <a name="remarks"></a>설명

로컬 언어 사양 (로캘 Id)을 사용 하 여 값의 서식을 지정 합니다. 통화 기호가 반환 된 값에 포함 되지 않습니다. 이 개체의 상태가 `COleCurrency` null 이면 반환 값은 빈 문자열입니다. 상태가 잘못 된 경우 문자열 리소스 IDS_INVALID_CURRENCY에 의해 반환 문자열이 지정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a> COleCurrency:: GetStatus

지정 된 개체의 상태 (유효성)를 가져오려면이 멤버 함수를 호출 `COleCurrency` 합니다.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>반환 값

이 값의 상태를 반환 `COleCurrency` 합니다.

### <a name="remarks"></a>설명

반환 값은 `CurrencyStatus` 클래스 내에 정의 된 열거형 형식에 의해 정의 됩니다 `COleCurrency` .

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleCurrency::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleCurrency` .

- `COleCurrency::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleCurrency` , 해당 값이 잘못 되었을 수 있습니다.

- `COleCurrency::null` 이 `COleCurrency` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

개체의 상태는 `COleCurrency` 다음과 같은 경우 유효 하지 않습니다.

- 해당 값이 `COleVariant` 통화 값으로 변환 될 수 없는 변형 또는 값에서 설정 된 경우

- 산술 할당 작업 중이 개체에 오버플로 또는 언더플로가 발생 한 경우 (예: `+=` 또는) **\*=**

- 이 개체에 잘못 된 값이 할당 된 경우

- 이 개체의 상태가 [SetStatus](#setstatus)를 사용 하 여 명시적으로 잘못 설정 된 경우입니다.

상태를 잘못 된 것으로 설정할 수 있는 작업에 대 한 자세한 내용은 다음 멤버 함수를 참조 하세요.

- [COleCurrency](#colecurrency)

- [연산자 =](#operator_eq)

- [operator +-](#operator_plus_minus)

- [operator + = 및-=](#operator_plus_minus_eq)

- [연산자 */](#operator_star)

- [연산자 * = 및/=](#operator_star_div_eq)

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a> COleCurrency:: m_cur

이 개체의 기본 [통화](/windows/win32/api/wtypes/ns-wtypes-cy-r1) 구조 `COleCurrency` 입니다.

### <a name="remarks"></a>설명

> [!CAUTION]
> 이 함수에서 반환 하는 포인터에 의해 액세스 되는 구조체의 값을 변경 `CURRENCY` 하면이 개체의 값이 변경 됩니다 `COleCurrency` . 이 개체의 상태는 변경 되지 않습니다 `COleCurrency` .

자세한 내용은 Windows SDK의 [통화](/windows/win32/api/wtypes/ns-wtypes-cy-r1) 항목을 참조 하세요.

## <a name="colecurrencym_status"></a><a name="m_status"></a> COleCurrency:: m_status

이 데이터 멤버의 형식은 클래스 내에 정의 된 열거형 형식입니다 `CurrencyStatus` `COleCurrency` .

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>설명

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleCurrency::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleCurrency` .

- `COleCurrency::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleCurrency` , 해당 값이 잘못 되었을 수 있습니다.

- `COleCurrency::null` 이 `COleCurrency` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

개체의 상태는 `COleCurrency` 다음과 같은 경우 유효 하지 않습니다.

- 해당 값이 `COleVariant` 통화 값으로 변환 될 수 없는 변형 또는 값에서 설정 된 경우

- 산술 할당 작업 중이 개체에 오버플로 또는 언더플로가 발생 한 경우 (예: `+=` 또는) **\*=**

- 이 개체에 잘못 된 값이 할당 된 경우

- 이 개체의 상태가 [SetStatus](#setstatus)를 사용 하 여 명시적으로 잘못 설정 된 경우입니다.

상태를 잘못 된 것으로 설정할 수 있는 작업에 대 한 자세한 내용은 다음 멤버 함수를 참조 하세요.

- [COleCurrency](#colecurrency)

- [연산자 =](#operator_eq)

- [연산자 +,-](#operator_plus_minus)

- [operator + =,-=](#operator_plus_minus_eq)

- [연산자 */](#operator_star)

- [연산자 * =,/=](#operator_star_div_eq)

> [!CAUTION]
> 이 데이터 멤버는 고급 프로그래밍 상황을 위한 것입니다. 인라인 멤버 함수 [GetStatus](#getstatus) 및 [SetStatus](#setstatus)를 사용 해야 합니다. `SetStatus`이 데이터 멤버를 명시적으로 설정 하는 방법에 대 한 자세한 내용은을 참조 하십시오.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a> COleCurrency:: operator =

이러한 오버 로드 된 할당 연산자는 원본 통화 값을이 개체에 복사 `COleCurrency` 합니다.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>설명

각 연산자에 대 한 간략 한 설명은 다음과 같습니다.

- **operator = (** `cySrc` **)** `CURRENCY` 값이 개체에 복사 되 `COleCurrency` 고 해당 상태가 valid로 설정 됩니다.

- **operator = (** `curSrc` **)** 피연산자의 값과 상태 이며, 기존 `COleCurrency` 개체가이 개체에 복사 됩니다 `COleCurrency` .

- **operator = (** *varsrc* **)** `VARIANT` 값 (또는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체)을 통화 ()로 변환 하면 변환 된 `VT_CY` 값이이 개체에 복사 되 `COleCurrency` 고 상태는 valid로 설정 됩니다. 변환이 실패 하면 개체의 값 `COleCurrency` 이 0으로 설정 되 고 상태가 잘못 된 것으로 설정 됩니다.

자세한 내용은 Windows SDK의 [통화](/windows/win32/api/wtypes/ns-wtypes-cy-r1) 및 [변형](/windows/win32/api/oaidl/ns-oaidl-variant) 항목을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a> COleCurrency:: operator +,-

이러한 연산자를 사용 하 여 두 값을 더하거나 서로 빼서 `COleCurrency` 값의 부호를 변경할 수 있습니다 `COleCurrency` .

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>설명

피연산자 중 하나가 null 이면 결과 값의 상태가 `COleCurrency` null입니다.

산술 연산이 오버플로 되는 경우 결과 `COleCurrency` 값이 유효 하지 않습니다.

피연산자가 유효 하지 않고 다른가 null이 아닌 경우 결과 값의 상태가 잘못 된 `COleCurrency` 것입니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a> COleCurrency:: operator + =,-=

`COleCurrency`이 개체에서 값을 추가 하 고 뺄 수 있습니다 `COleCurrency` .

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>설명

피연산자 중 하나가 null 이면이 개체의 상태는 `COleCurrency` null로 설정 됩니다.

산술 연산이 오버플로 되는 경우이 개체의 상태는 `COleCurrency` 잘못 됨으로 설정 됩니다.

피연산자 중 하나가 유효 하지 않고 다른 피연산자가 null이 아닌 경우이 개체의 상태는 `COleCurrency` 잘못 됨으로 설정 됩니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a> COleCurrency:: operator \* 및/

`COleCurrency`정수 값을 기준으로 값의 크기를 조정할 수 있습니다.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>설명

`COleCurrency`피연산자가 null 이면 결과 값의 상태가 `COleCurrency` null입니다.

산술 연산이 오버플로 되거나 언더플로 면 결과 값의 상태가 `COleCurrency` 잘못 된 것입니다.

`COleCurrency`피연산자가 잘못 된 경우 결과 값의 상태가 잘못 된 `COleCurrency` 것입니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a> COleCurrency:: operator \* =,/=

`COleCurrency`정수 계열 값으로이 값의 크기를 조정할 수 있습니다.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>설명

`COleCurrency`피연산자가 null 이면이 개체의 상태가 `COleCurrency` null로 설정 됩니다.

산술 연산이 오버플로 되는 경우이 개체의 상태는 `COleCurrency` 잘못 됨으로 설정 됩니다.

`COleCurrency`피연산자가 잘못 된 경우이 개체의 상태가 `COleCurrency` 잘못 됨으로 설정 됩니다.

유효한, 유효 하지 않음 및 null 상태 값에 대 한 자세한 내용은 [m_status](#m_status) 멤버 변수를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency:: operator &lt; &lt; ,&gt;&gt;

진단 덤프를 지원 하 고 보관 파일에 저장 합니다.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>설명

추출 ( **>>** ) 연산자는 보관 파일에서 로드를 지원 합니다.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a> COleCurrency:: operator CURRENCY

`CURRENCY`이 개체에서 값이 복사 되는 구조체를 반환 `COleCurrency` 합니다.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>설명

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a> COleCurrency::P arseCurrency

통화 값을 읽도록 문자열을 구문 분석 하려면이 멤버 함수를 호출 합니다.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>매개 변수

*lpszCurrency*<br/>
구문 분석할 null로 끝나는 문자열에 대 한 포인터입니다.

*dwFlags*<br/>
로캘 설정에 대 한 플래그를 나타냅니다. 플래그는 다음과 같습니다.

- 사용자 지정 사용자 설정이 아닌 시스템 기본 로캘 설정을 사용 LOCALE_NOUSEROVERRIDE 합니다.

*lcid*<br/>
변환에 사용할 로캘 ID를 나타냅니다.

### <a name="return-value"></a>반환 값

문자열이 통화 값으로 성공적으로 변환 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

소스 문자열에서 숫자가 아닌 문자에 대 한 의미를 위해 지역 언어 사양 (로캘 Id)을 사용 합니다.

로캘 ID 값에 대 한 설명은 [여러 언어 지원](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)을 참조 하세요.

문자열이 통화 값으로 성공적으로 변환 된 경우이 개체의 값은 `COleCurrency` 해당 값으로 설정 되 고 상태는 valid로 설정 됩니다.

문자열을 통화 값으로 변환할 수 없거나 숫자 오버플로가 발생 한 경우에는이 개체의 상태가 `COleCurrency` 유효 하지 않습니다.

메모리 할당 오류로 인해 문자열 변환이 실패 한 경우이 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md)을 throw 합니다. 다른 오류 상태에서이 함수는 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a> COleCurrency 관계형 연산자

두 통화 값을 비교 하 고 조건이 true 이면 0이 아닌 값을 반환 합니다. 그렇지 않으면 0입니다.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>설명

> [!NOTE]
> **<** **\<=**, **>** **>=** 두 피연산자의 상태가 null 이거나 잘못 된 경우 정렬 작업 (,,)의 반환 값은 정의 되지 않습니다. 같음 연산자 ( `==` , `!=` )는 피연산자의 상태를 고려 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a> COleCurrency:: SetCurrency

이 멤버 함수를 호출 하 여이 개체의 단위와 소수 부분을 설정 `COleCurrency` 합니다.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>매개 변수

*Nunits*( *nFractionalUnits* )는이 개체에 복사할 값의 단위 및 소수 부분 (1/10000)을 표시 `COleCurrency` 합니다.

### <a name="remarks"></a>설명

소수 부분의 절대값이 1만 보다 큰 경우 다음 예의 세 번째 예에 표시 된 것 처럼 해당 단위에 대 한 적절 한 조정이 수행 됩니다.

단위 및 소수 부분은 부호 있는 long 값으로 지정 됩니다. 다음 예의 네 번째 예에서는 매개 변수의 부호가 다를 때 발생 하는 상황을 보여 줍니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a> COleCurrency:: SetStatus

이 멤버 함수를 호출 하 여이 개체의 상태 (유효성)를 설정 `COleCurrency` 합니다.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>매개 변수

*status*<br/>
이 개체의 새 상태 `COleCurrency` 입니다.

### <a name="remarks"></a>설명

*상태* 매개 변수 값은 `CurrencyStatus` 클래스 내에서 정의 되는 열거 된 형식에 의해 정의 됩니다 `COleCurrency` .

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

이러한 상태 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `COleCurrency::valid` 이 개체가 유효한 지 여부를 나타냅니다 `COleCurrency` .

- `COleCurrency::invalid` 이 개체가 잘못 되었음을 나타냅니다. 즉 `COleCurrency` , 해당 값이 잘못 되었을 수 있습니다.

- `COleCurrency::null` 이 `COleCurrency` 개체가 null 임을 나타냅니다. 즉,이 개체에 대해 값이 제공 되지 않았음을 나타냅니다. 이는 c + + NULL과는 달리 "값이 없습니다" 라는 데이터베이스 의미의 "null"입니다.

> [!CAUTION]
> 이 함수는 고급 프로그래밍 상황을 위한 것입니다. 이 함수는이 개체의 데이터를 변경 하지 않습니다. 상태를 null 또는 잘못 된 것으로 설정 하는 데 주로 사용 됩니다. 할당 연산자 ( [operator =](#operator_eq)) 및 [setcurrency](#setcurrency) 는 원본 값을 기준으로 개체의 상태를 설정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 클래스](../../mfc/reference/colevariant-class.md)

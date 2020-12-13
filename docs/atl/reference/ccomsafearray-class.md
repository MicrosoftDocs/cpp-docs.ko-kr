---
description: '자세히 알아보기: CComSafeArray 클래스'
title: CComSafeArray 클래스
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: e25719ffb9817595a1c1cc108a9d9ffc91459fe1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142311"
---
# <a name="ccomsafearray-class"></a>CComSafeArray 클래스

이 클래스는 구조체에 대 한 래퍼입니다 `SAFEARRAY` .

## <a name="syntax"></a>구문

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
배열에 저장할 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComSafeArray:: CComSafeArray](#ccomsafearray)|생성자입니다.|
|[CComSafeArray:: ~ CComSafeArray](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComSafeArray:: Add](#add)|하나 이상의 요소 또는 구조체를에 추가 `SAFEARRAY` `CComSafeArray` 합니다.|
|[CComSafeArray:: Attach](#attach)|구조체를 `SAFEARRAY` 개체에 연결 `CComSafeArray` 합니다.|
|[CComSafeArray:: CopyFrom](#copyfrom)|구조체의 내용을 `SAFEARRAY` 개체에 복사 합니다 `CComSafeArray` .|
|[CComSafeArray:: CopyTo](#copyto)|`CComSafeArray` 개체의 복사본을 만듭니다.|
|[개체를 만들려면](#create)|`CComSafeArray` 개체를 만듭니다.|
|[CComSafeArray::Destroy](#destroy)|`CComSafeArray` 개체를 제거합니다.|
|[CComSafeArray::D etach](#detach)|`SAFEARRAY`개체에서를 분리 `CComSafeArray` 합니다.|
|[CComSafeArray:: GetAt](#getat)|1차원 배열에서 단일 요소를 검색합니다.|
|[CComSafeArray:: GetCount](#getcount)|배열의 요소 수를 반환합니다.|
|[CComSafeArray:: GetDimensions](#getdimensions)|배열의 차원 수를 반환합니다.|
|[CComSafeArray:: GetLowerBound](#getlowerbound)|배열의 지정된 차원에 대한 하한을 반환합니다.|
|[CComSafeArray:: GetSafeArrayPtr](#getsafearrayptr)|`m_psa` 데이터 멤버의 주소를 반환합니다.|
|[CComSafeArray:: GetType](#gettype)|배열에 저장된 데이터의 형식을 반환합니다.|
|[CComSafeArray:: System.array.getupperbound](#getupperbound)|배열의 모든 차원에 대한 상한을 반환합니다.|
|[CComSafeArray:: IsSizable 가능](#issizable)|`CComSafeArray` 개체의 크기를 조정할 수 있는지 테스트합니다.|
|[CComSafeArray:: MultiDimGetAt](#multidimgetat)|다차원 배열에서 단일 요소를 검색합니다.|
|[CComSafeArray:: MultiDimSetAt](#multidimsetat)|다차원 배열의 요소 값을 설정합니다.|
|[CComSafeArray:: Resize](#resize)|`CComSafeArray` 개체의 크기를 조정합니다.|
|[CComSafeArray:: SetAt](#setat)|1차원 배열의 요소 값을 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CComSafeArray:: operator LPSAFEARRAY](#operator_lpsafearray)|값을 `SAFEARRAY` 포인터로 캐스팅 합니다.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|배열에서 요소를 검색합니다.|
|[CComSafeArray:: operator =](#operator_eq)|대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComSafeArray:: m_psa](#m_psa)|이 데이터 멤버는 구조체의 주소를 보유 합니다 `SAFEARRAY` .|

## <a name="remarks"></a>설명

`CComSafeArray` 는 [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray) 클래스에 대한 래퍼를 제공합니다. 따라서 거의 모든 VARIANT 지원 형식의 1차원 및 다차원 배열을 쉽게 만들고 관리할 수 있습니다.

`CComSafeArray` 는 프로세스 간의 배열 전달을 간소화할 뿐만 아니라 상한과 하한에 대해 배열 인덱스 값을 확인하여 추가 보안을 제공합니다.

`CComSafeArray` 의 하한은 모든 사용자 정의 값에서 시작할 수 있지만 C++를 통해 액세스하는 배열에서는 0을 하한으로 사용해야 합니다. Visual Basic과 같은 다른 언어에서는 다른 경계 값(예: -10~10)을 사용할 수 있습니다.

[개체를 만들려면](#create) CComSafeArray::Create `CComSafeArray` 를 사용하고, 제거하려면 [CComSafeArray::Destroy](#destroy) 를 사용합니다.

`CComSafeArray` 는 VARIANT 데이터 형식의 다음 하위 집합을 포함할 수 있습니다.

|VARTYPE|설명|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|decimal pointer|
|VT_VARIANT|variant pointer|
|VT_CY|Currency 데이터 형식|

## <a name="requirements"></a>요구 사항

**헤더:** atlsafe.h

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a> CComSafeArray:: Add

하나 이상의 요소 또는 구조체를에 추가 `SAFEARRAY` `CComSafeArray` 합니다.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>매개 변수

*psaSrc*<br/>
`SAFEARRAY` 개체에 대한 포인터입니다.

*ulCount*<br/>
배열에 추가할 개체의 수입니다.

*P t*<br/>
배열에 추가할 하나 이상의 개체에 대 한 포인터입니다.

*t*<br/>
배열에 추가할 개체에 대 한 참조입니다.

*bCopy*<br/>
데이터 복사본을 만들어야 하는지 여부를 나타냅니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

새 개체는 기존 개체의 끝에 추가 됩니다 `SAFEARRAY` . 다차원 개체에 개체를 추가 하 `SAFEARRAY` 는 것은 지원 되지 않습니다. 개체의 기존 배열을 추가할 때 두 배열 모두 동일한 형식의 요소를 포함 해야 합니다.

*Bcopy* 플래그는 BSTR 또는 VARIANT 형식의 요소가 배열에 추가 될 때 고려 됩니다. 기본값인 TRUE로 설정 하면 요소가 배열에 추가 될 때 데이터의 새 복사본이 생성 됩니다.

## <a name="ccomsafearrayattach"></a><a name="attach"></a> CComSafeArray:: Attach

구조체를 `SAFEARRAY` 개체에 연결 `CComSafeArray` 합니다.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>매개 변수

*psaSrc*<br/>
구조체에 대 한 포인터 `SAFEARRAY` 입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

구조체를 `SAFEARRAY` 개체에 연결 `CComSafeArray` 하 여 기존 메서드를 `CComSafeArray` 사용할 수 있도록 합니다.

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a> CComSafeArray:: CComSafeArray

생성자입니다.

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>매개 변수

*바인딩하면*<br/>
`SAFEARRAYBOUND` 구조체입니다.

*ulCount*<br/>
배열의 요소 수입니다.

*lLBound*<br/>
하 한 값입니다. 즉, 배열에 있는 첫 번째 요소의 인덱스입니다.

*pBound*<br/>
구조체에 대 한 포인터 `SAFEARRAYBOUND` 입니다.

*uDims*<br/>
배열의 차원 수입니다.

*saSrc*<br/>
구조체 또는 개체에 대 한 참조 `SAFEARRAY` `CComSafeArray` 입니다. 두 경우 모두 생성자는이 참조를 사용 하 여 배열의 복사본을 만들기 때문에 배열을 생성 후 참조 하지 않습니다.

*psaSrc*<br/>
구조체에 대 한 포인터 `SAFEARRAY` 입니다. 생성자는이 주소를 사용 하 여 배열의 복사본을 만들기 때문에 배열이 생성 된 후 참조 되지 않습니다.

### <a name="remarks"></a>설명

`CComSafeArray` 개체를 만듭니다.

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a> CComSafeArray:: ~ CComSafeArray

소멸자입니다.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a> CComSafeArray:: CopyFrom

구조체의 내용을 `SAFEARRAY` 개체에 복사 합니다 `CComSafeArray` .

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>매개 변수

*ppArray*<br/>
복사할에 대 한 포인터 `SAFEARRAY` 입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는의 내용을 `SAFEARRAY` 현재 `CComSafeArray` 개체로 복사 합니다. 배열의 기존 내용이 바뀝니다.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a> CComSafeArray:: CopyTo

`CComSafeArray` 개체의 복사본을 만듭니다.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>매개 변수

*ppArray*<br/>
새을 만들 위치에 대 한 포인터입니다 `SAFEARRAY` .

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 개체의 내용을 `CComSafeArray` `SAFEARRAY` 구조체로 복사 합니다.

## <a name="ccomsafearraycreate"></a><a name="create"></a> CComSafeArray:: Create

`CComSafeArray`을 만듭니다.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>매개 변수

*pBound*<br/>
`SAFEARRAYBOUND` 개체에 대한 포인터입니다.

*uDims*<br/>
배열의 차수입니다.

*ulCount*<br/>
배열의 요소 수입니다.

*lLBound*<br/>
하 한 값입니다. 즉, 배열에 있는 첫 번째 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`CComSafeArray`개체는 기존 `SAFEARRAYBOUND` 구조와 차원 수에서 만들 수도 있고 배열의 요소 수와 하 한을 지정 하 여 만들 수도 있습니다. C + +에서 배열에 액세스 하는 경우 하 한은 0 이어야 합니다. 다른 언어에서는 하 한에 다른 값을 허용할 수 있습니다. 예를 들어 Visual Basic는 범위가-10 ~ 10 인 요소가 포함 된 배열을 지원 합니다.

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a> CComSafeArray::D estroy

`CComSafeArray` 개체를 제거합니다.

```
HRESULT Destroy();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

기존 `CComSafeArray` 개체와 여기에 포함 된 모든 데이터를 소멸 시킵니다.

## <a name="ccomsafearraydetach"></a><a name="detach"></a> CComSafeArray::D etach

`SAFEARRAY`개체에서를 분리 `CComSafeArray` 합니다.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>반환 값

개체에 대 한 포인터를 반환 `SAFEARRAY` 합니다.

### <a name="remarks"></a>설명

이 메서드는 개체 `SAFEARRAY` 에서 개체를 분리 `CComSafeArray` 합니다.

## <a name="ccomsafearraygetat"></a><a name="getat"></a> CComSafeArray:: GetAt

1차원 배열에서 단일 요소를 검색합니다.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>매개 변수

*lIndex*<br/>
반환할 배열 값의 인덱스 번호입니다.

### <a name="return-value"></a>반환 값

필수 배열 요소에 대 한 참조를 반환 합니다.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a> CComSafeArray:: GetCount

배열의 요소 수를 반환합니다.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>매개 변수

*uDim*<br/>
배열 차원입니다.

### <a name="return-value"></a>반환 값

배열의 요소 수를 반환합니다.

### <a name="remarks"></a>설명

다차원 배열과 함께 사용 하는 경우이 메서드는 특정 차원에 있는 요소 수만 반환 합니다.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a> CComSafeArray:: GetDimensions

배열의 차원 수를 반환합니다.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>반환 값

배열의 차원 수를 반환합니다.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a> CComSafeArray:: GetLowerBound

배열의 지정된 차원에 대한 하한을 반환합니다.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>매개 변수

*uDim*<br/>
하 한을 가져올 배열 차원입니다. 생략 하는 경우 기본값은 0입니다.

### <a name="return-value"></a>반환 값

하 한을 반환 합니다.

### <a name="remarks"></a>설명

하 한이 0 이면 첫 번째 요소가 요소 번호 0 인 C와 비슷한 배열을 나타냅니다. 오류가 발생 하는 경우 (예: 잘못 된 차원 인수)이 메서드는 `AtlThrow` 오류를 설명 하는 HRESULT를 사용 하 여를 호출 합니다.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a> CComSafeArray:: GetSafeArrayPtr

`m_psa` 데이터 멤버의 주소를 반환합니다.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>반환 값

[CComSafeArray:: m_psa](#m_psa) 데이터 멤버에 대 한 포인터를 반환 합니다.

## <a name="ccomsafearraygettype"></a><a name="gettype"></a> CComSafeArray:: GetType

배열에 저장된 데이터의 형식을 반환합니다.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>반환 값

배열에 저장 된 데이터의 형식을 반환 합니다. 여기에는 다음 형식 중 하나일 수 있습니다.

|VARTYPE|설명|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|decimal pointer|
|VT_VARIANT|variant pointer|
|VT_CY|Currency 데이터 형식|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a> CComSafeArray:: System.array.getupperbound

배열의 모든 차원에 대한 상한을 반환합니다.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>매개 변수

*uDim*<br/>
상한을 가져올 배열 차원입니다. 생략 하는 경우 기본값은 0입니다.

### <a name="return-value"></a>반환 값

상한을 반환 합니다. 이 값은이 차원에 대 한 최대 유효 인덱스 (포함)입니다.

### <a name="remarks"></a>설명

오류가 발생 하는 경우 (예: 잘못 된 차원 인수)이 메서드는 `AtlThrow` 오류를 설명 하는 HRESULT를 사용 하 여를 호출 합니다.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a> CComSafeArray:: IsSizable 가능

`CComSafeArray` 개체의 크기를 조정할 수 있는지 테스트합니다.

```
bool IsSizable() const;
```

### <a name="return-value"></a>반환 값

의 `CComSafeArray` 크기를 조정할 수 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a> CComSafeArray:: m_psa

액세스 한 구조체의 주소를 보유 `SAFEARRAY` 합니다.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a> CComSafeArray:: MultiDimGetAt

다차원 배열에서 단일 요소를 검색합니다.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>매개 변수

*alIndex*<br/>
배열의 각 차원에 대 한 인덱스 벡터에 대 한 포인터입니다. 가장 왼쪽 (가장 중요) 차원은 `alIndex[0]` 입니다.

*t*<br/>
반환 된 데이터에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a> CComSafeArray:: MultiDimSetAt

다차원 배열의 요소 값을 설정합니다.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>매개 변수

*alIndex*<br/>
배열의 각 차원에 대 한 인덱스 벡터에 대 한 포인터입니다. 가장 오른쪽 (최하위) 차원은 `alIndex` [0]입니다.

*T*<br/>
새 요소의 값을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이는 [CComSafeArray:: SetAt](#setat)의 다차원 버전입니다.

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a> CComSafeArray:: operator \[\]

배열에서 요소를 검색합니다.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>매개 변수

*lIndex, n 인덱스*<br/>
배열에 있는 필수 요소의 인덱스 번호입니다.

### <a name="return-value"></a>반환 값

적절 한 배열 요소를 반환 합니다.

### <a name="remarks"></a>설명

[CComSafeArray:: GetAt](#getat)와 유사한 함수를 수행 하지만이 연산자는 1 차원 배열 에서만 작동 합니다.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a> CComSafeArray:: operator =

대입 연산자입니다.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>매개 변수

*saSrc*<br/>
`CComSafeArray` 개체에 대한 참조입니다.

*psaSrc*<br/>
`SAFEARRAY` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

배열에 저장된 데이터의 형식을 반환합니다.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a> CComSafeArray:: operator LPSAFEARRAY

값을 `SAFEARRAY` 포인터로 캐스팅 합니다.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>반환 값

값을 `SAFEARRAY` 포인터로 캐스팅 합니다.

## <a name="ccomsafearrayresize"></a><a name="resize"></a> CComSafeArray:: Resize

`CComSafeArray` 개체의 크기를 조정합니다.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>매개 변수

*pBound*<br/>
`SAFEARRAYBOUND`요소의 수와 배열의 하 한에 대 한 정보를 포함 하는 구조체에 대 한 포인터입니다.

*ulCount*<br/>
크기 조정 된 배열의 요청 된 개체 수입니다.

*lLBound*<br/>
하한입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 가장 오른쪽 차원의 크기를 조정 합니다. FALSE로 반환 하는 배열의 크기는 조정 되지 않습니다 `IsResizable` .

## <a name="ccomsafearraysetat"></a><a name="setat"></a> CComSafeArray:: SetAt

1차원 배열의 요소 값을 설정합니다.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>매개 변수

*lIndex*<br/>
설정할 배열 요소의 인덱스 번호입니다.

*t*<br/>
지정된 요소의 새 값입니다.

*bCopy*<br/>
데이터 복사본을 만들어야 하는지 여부를 나타냅니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

*Bcopy* 플래그는 BSTR 또는 VARIANT 형식의 요소가 배열에 추가 될 때 고려 됩니다. 기본값인 TRUE로 설정 하면 요소가 배열에 추가 될 때 데이터의 새 복사본이 생성 됩니다.

## <a name="see-also"></a>참고 항목

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[개체를 만들려면](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

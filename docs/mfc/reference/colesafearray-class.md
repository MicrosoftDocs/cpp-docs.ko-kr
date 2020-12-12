---
description: '자세한 정보: COleSafeArray 클래스'
title: COleSafeArray 클래스
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: 6c33f58f71167c492883a25b05fce6bb8fb09916
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226703"
---
# <a name="colesafearray-class"></a>COleSafeArray 클래스

임의의 형식 및 차원 배열 작업용 클래스입니다.

## <a name="syntax"></a>구문

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleSafeArray:: COleSafeArray](#colesafearray)|`COleSafeArray` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleSafeArray:: AccessData](#accessdata)|배열 데이터에 대 한 포인터를 검색 합니다.|
|[COleSafeArray:: AllocData](#allocdata)|배열에 메모리를 할당 합니다.|
|[COleSafeArray:: AllocDescriptor](#allocdescriptor)|안전 배열 설명자의 메모리를 할당 합니다.|
|[COleSafeArray:: Attach](#attach)|`VARIANT`개체에 대 한 기존 배열의 제어를 제공 `COleSafeArray` 합니다.|
|[COleSafeArray:: Clear](#clear)|내부에 있는 모든 데이터를 해제 `VARIANT` 합니다.|
|[COleSafeArray:: Copy](#copy)|기존 배열의 복사본을 만듭니다.|
|[COleSafeArray:: Create](#create)|안전 배열을 만듭니다.|
|[COleSafeArray:: CreateOneDim](#createonedim)|1 차원 개체를 만듭니다 `COleSafeArray` .|
|[COleSafeArray::D estroy](#destroy)|기존 배열을 소멸 시킵니다.|
|[COleSafeArray::D estroyData](#destroydata)|안전 배열의 데이터를 소멸 시킵니다.|
|[COleSafeArray::D estroyDescriptor](#destroydescriptor)|안전 배열의 설명자를 소멸 시킵니다.|
|[COleSafeArray::D etach](#detach)|데이터를 해제 하지 않도록 개체에서 변형 배열을 분리 `COleSafeArray` 합니다.|
|[COleSafeArray:: GetByteArray](#getbytearray)|안전 배열의 내용을 [CByteArray](../../mfc/reference/cbytearray-class.md)에 복사 합니다.|
|[COleSafeArray:: GetDim](#getdim)|배열의 차원 수를 반환합니다.|
|[COleSafeArray:: GetElement](#getelement)|안전 배열의 단일 요소를 검색 합니다.|
|[COleSafeArray:: GetElemSize](#getelemsize)|안전 배열에서 한 요소의 크기 (바이트)를 반환 합니다.|
|[COleSafeArray:: GetLBound](#getlbound)|안전 배열의 모든 차원에 대 한 하 한을 반환 합니다.|
|[COleSafeArray:: Getonesize 크기](#getonedimsize)|1 차원 개체의 요소 수를 반환 합니다 `COleSafeArray` .|
|[COleSafeArray:: GetUBound](#getubound)|안전 배열의 모든 차원에 대 한 상한을 반환 합니다.|
|[COleSafeArray:: Lock](#lock)|배열의 잠금 횟수를 늘리고 배열 설명자의 배열 데이터에 대 한 포인터를 배치 합니다.|
|[COleSafeArray::P trOfIndex](#ptrofindex)|인덱싱된 요소에 대 한 포인터를 반환 합니다.|
|[COleSafeArray::P utElement](#putelement)|단일 요소를 배열에 할당합니다.|
|[COleSafeArray:: Redim](#redim)|안전 배열의 최하위 (가장 오른쪽) 범위를 변경 합니다.|
|[COleSafeArray:: ResizeOneDim](#resizeonedim)|1 차원 개체의 요소 수를 변경 `COleSafeArray` 합니다.|
|[COleSafeArray:: UnaccessData](#unaccessdata)|배열의 잠금 횟수를 감소 시키고로 검색 된 포인터를 무효화 `AccessData` 합니다.|
|[COleSafeArray:: Unlock](#unlock)|배열의 잠금 횟수를 감소 시켜 해제 하거나 크기를 조정할 수 있습니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[COleSafeArray:: operator LPCVARIANT](#operator_lpcvariant)|`VARIANT`개체의 기본 구조에 액세스 `COleSafeArray` 합니다.|
|[COleSafeArray:: operator LPVARIANT](#operator_lpvariant)|`VARIANT`개체의 기본 구조에 액세스 `COleSafeArray` 합니다.|
|[COleSafeArray:: operator =](#operator_eq)|값을 `COleSafeArray` 개체 (,, `SAFEARRAY` `VARIANT` `COleVariant` 또는 `COleSafeArray` 배열)로 복사 합니다.|
|[COleSafeArray:: operator = =](#operator_eq_eq)|두 variant 배열 ( `SAFEARRAY` , `VARIANT` , `COleVariant` 또는 배열)을 비교 `COleSafeArray` 합니다.|
|[COleSafeArray:: operator &lt;&lt;](#operator_lt_lt)|개체의 내용을 `COleSafeArray` 덤프 컨텍스트에 출력 합니다.|

## <a name="remarks"></a>설명

`COleSafeArray` OLE 구조에서 파생 `VARIANT` 됩니다. OLE `SAFEARRAY` 멤버 함수는를 통해 사용할 수 있으며 `COleSafeArray` , 1 차원 바이트 배열에 대해 특별히 디자인 된 멤버 함수 집합을 사용할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a> COleSafeArray:: AccessData

배열 데이터에 대 한 포인터를 검색 합니다.

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>매개 변수

*ppvData*<br/>
배열 데이터에 대 한 포인터에 대 한 포인터입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a> COleSafeArray:: AllocData

안전 배열에 대해 메모리를 할당 합니다.

```cpp
void AllocData();
```

### <a name="remarks"></a>설명

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a> COleSafeArray:: AllocDescriptor

안전 배열의 설명자에 대해 메모리를 할당 합니다.

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>매개 변수

*dwDims*<br/>
안전 배열의 차원 수입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearrayattach"></a><a name="attach"></a> COleSafeArray:: Attach

기존 배열의 데이터를 개체에 대 한 제어 `VARIANT` 를 제공 `COleSafeArray` 합니다.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>매개 변수

*varSrc*<br/>
`VARIANT` 개체입니다. *Varsrc* 매개 변수에는 VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)있어야 합니다.

### <a name="remarks"></a>설명

소스의 `VARIANT` 형식은 VT_EMPTY로 설정 됩니다. 이 함수는 현재 배열 데이터 (있는 경우)를 지웁니다.

### <a name="example"></a>예제

  [Colesafearray:: AccessData](#accessdata)의 예제를 참조 하세요.

## <a name="colesafearrayclear"></a><a name="clear"></a> COleSafeArray:: Clear

안전 배열을 지웁니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

함수는 개체의를 VT_EMPTY 설정 하 여 안전 배열을 지웁니다 `VARTYPE` . 현재 콘텐츠가 해제 되 고 배열이 해제 됩니다.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a> COleSafeArray:: COleSafeArray

`COleSafeArray` 개체를 생성합니다.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>매개 변수

*saSrc*<br/>
새 개체에 `COleSafeArray` 복사 되는 기존 개체 또는 `SAFEARRAY` `COleSafeArray` 입니다.

*vtSrc*<br/>
새 개체의 VARTYPE입니다 `COleSafeArray` .

*psaSrc*<br/>
새 개체로 복사할에 대 한 포인터 `SAFEARRAY` `COleSafeArray` 입니다.

*varSrc*<br/>
`VARIANT` `COleVariant` 새 개체에 복사할 기존 또는 개체 `COleSafeArray` 입니다.

*.Psrc*<br/>
`VARIANT`새 개체로 복사할 개체에 대 한 포인터 `COleSafeArray` 입니다.

### <a name="remarks"></a>설명

이러한 모든 생성자는 새 개체를 만듭니다 `COleSafeArray` . 매개 변수가 없으면 빈 `COleSafeArray` 개체가 생성 됩니다 (VT_EMPTY). 가 `COleSafeArray` VARTYPE을 암시적으로 알려진 다른 배열 (, 또는)에서 복사 된 경우 `COleSafeArray` `COleVariant` `VARIANT` 원본 배열의 vartype은 유지 되 고 지정할 필요가 없습니다. `COleSafeArray`가 vartype을 알 수 없는 다른 배열에서 복사 된 경우 ( `SAFEARRAY` ) *vtSrc* 매개 변수에서 vartype을 지정 해야 합니다.

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearraycopy"></a><a name="copy"></a> COleSafeArray:: Copy

기존 안전 배열의 복사본을 만듭니다.

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>매개 변수

*ppsa*<br/>
새 배열 설명자를 반환할 위치에 대 한 포인터입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearraycreate"></a><a name="create"></a> COleSafeArray:: Create

배열에 대 한 데이터를 할당 하 고 초기화 합니다.

```cpp
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>매개 변수

*vtSrc*<br/>
배열의 기본 형식입니다. 즉, 배열의 각 요소에 대 한 VARTYPE입니다. VARTYPE은 variant 형식의 하위 집합으로 제한 됩니다. VT_ARRAY와 VT_BYREF 플래그는 모두 설정할 수 없습니다. VT_EMPTY 및 VT_NULL는 배열에 대해 유효한 기본 형식이 아닙니다. 다른 모든 형식은 유효 합니다.

*dwDims*<br/>
배열의 차원 수입니다. 이는 [Redim](#redim)을 사용 하 여 배열을 만든 후에 변경할 수 있습니다.

*rgElements*<br/>
배열의 각 차원에 대 한 요소 수의 배열에 대 한 포인터입니다.

*rgsabounds*<br/>
배열에 할당할 범위 벡터 (각 차원에 대 한 하나)에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 필요한 경우 현재 배열 데이터를 지웁니다. 오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a> COleSafeArray:: CreateOneDim

새 1 차원 개체를 만듭니다 `COleSafeArray` .

```cpp
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>매개 변수

*vtSrc*<br/>
배열의 기본 형식입니다. 즉, 배열의 각 요소에 대 한 VARTYPE입니다.

*dwElements*<br/>
배열의 요소 수입니다. [ResizeOneDim](#resizeonedim)를 사용 하 여 배열을 만든 후이를 변경할 수 있습니다.

*pvSrcData*<br/>
배열에 복사할 데이터에 대 한 포인터입니다.

*nLBound*<br/>
배열의 하 한입니다.

### <a name="remarks"></a>설명

함수는 *pvSrcData* 가 NULL이 아닌 경우 지정 된 데이터를 복사 하 여 배열에 대 한 데이터를 할당 하 고 초기화 합니다.

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a> COleSafeArray::D estroy

기존 배열 설명자와 배열의 모든 데이터를 소멸 시킵니다.

```cpp
void Destroy();
```

### <a name="remarks"></a>설명

개체를 배열에 저장 하면 각 개체가 릴리스됩니다. 오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a> COleSafeArray::D estroyData

안전 배열의 모든 데이터를 소멸 시킵니다.

```cpp
void DestroyData();
```

### <a name="remarks"></a>설명

개체를 배열에 저장 하면 각 개체가 릴리스됩니다. 오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a> COleSafeArray::D estroyDescriptor

안전 배열의 설명자를 소멸 시킵니다.

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>설명

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearraydetach"></a><a name="detach"></a> COleSafeArray::D etach

`VARIANT`개체에서 데이터를 분리 `COleSafeArray` 합니다.

```
VARIANT Detach();
```

### <a name="return-value"></a>반환 값

`VARIANT`개체의 내부 값 `COleSafeArray` 입니다.

### <a name="remarks"></a>설명

함수는 개체의 VARTYPE을 VT_EMPTY로 설정 하 여 안전 배열의 데이터를 분리 합니다. Windows 함수 [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)를 호출 하 여 배열을 해제 하는 것은 호출자의 책임입니다.

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

  [Colesafearray::P utElement](#putelement)의 예제를 참조 하세요.

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a> COleSafeArray:: GetByteArray

안전 배열의 내용을에 복사 합니다 `CByteArray` .

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>매개 변수

*bytes*<br/>
[CByteArray](../../mfc/reference/cbytearray-class.md) 개체에 대 한 참조입니다.

## <a name="colesafearraygetdim"></a><a name="getdim"></a> COleSafeArray:: GetDim

개체의 차원 수를 반환 합니다 `COleSafeArray` .

```
DWORD GetDim();
```

### <a name="return-value"></a>반환 값

안전 배열의 차원 수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a> COleSafeArray:: GetElement

안전 배열의 단일 요소를 검색 합니다.

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>매개 변수

*rgIndices*<br/>
각 배열 차원의 인덱스 배열에 대한 포인터입니다.

*pvData*<br/>
배열의 요소를 배치 하는 위치에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 `SafeArrayLock` `SafeArrayUnlock` 요소를 검색 하기 전후에 windows 함수를 자동으로 호출 합니다. 데이터 요소가 문자열, 개체 또는 변형 인 경우 함수는 올바른 방식으로 요소를 복사 합니다. *PvData* 매개 변수는 요소를 포함 하기에 충분 한 크기의 버퍼를 가리켜야 합니다.

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a> COleSafeArray:: GetElemSize

개체의 요소 크기를 검색 합니다 `COleSafeArray` .

```
DWORD GetElemSize();
```

### <a name="return-value"></a>반환 값

안전 배열 요소의 크기 (바이트)입니다.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a> COleSafeArray:: GetLBound

개체의 모든 차원에 대 한 하 한을 반환 `COleSafeArray` 합니다.

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>매개 변수

*dwDim*<br/>
하 한을 가져올 배열 차원입니다.

*pLBound*<br/>
하 한을 반환할 위치에 대 한 포인터입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a> COleSafeArray:: Getonesize 크기

1 차원 개체의 요소 수를 반환 합니다 `COleSafeArray` .

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>반환 값

1 차원 안전 배열의 요소 수입니다.

### <a name="example"></a>예제

  [Colesafearray:: CreateOneDim](#createonedim)의 예제를 참조 하세요.

## <a name="colesafearraygetubound"></a><a name="getubound"></a> COleSafeArray:: GetUBound

안전 배열의 모든 차원에 대 한 상한을 반환 합니다.

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>매개 변수

*dwDim*<br/>
상한을 가져올 배열 차원입니다.

*pUBound*<br/>
상한을 반환할 위치에 대 한 포인터입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a> COleSafeArray:: Lock

배열의 잠금 횟수를 늘리고 배열 설명자의 배열 데이터에 대 한 포인터를 놓습니다.

```cpp
void Lock();
```

### <a name="remarks"></a>설명

오류가 발생 하면 [Coleexception](../../mfc/reference/coleexception-class.md)이 throw 됩니다.

배열 설명자의 포인터는가 호출 될 때까지 유효 `Unlock` 합니다. 에 대 한 호출은 `Lock` 중첩 될 수 있습니다 .에 대 한 호출 수는 동일 `Unlock` 해야 합니다.

배열이 잠겨 있는 동안에는 삭제할 수 없습니다.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a> COleSafeArray:: operator LPCVARIANT

이 캐스팅 연산자를 호출 하 여 `VARIANT` 이 개체의 기본 구조에 액세스 `COleSafeArray` 합니다.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a> COleSafeArray:: operator LPVARIANT

이 캐스팅 연산자를 호출 하 여 `VARIANT` 이 개체의 기본 구조에 액세스 `COleSafeArray` 합니다.

```
operator LPVARIANT();
```

### <a name="remarks"></a>설명

이 함수에서 반환 하는 포인터에 의해 액세스 되는 구조체의 값을 변경 `VARIANT` 하면이 개체의 값이 변경 됩니다 `COleSafeArray` .

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a> COleSafeArray:: operator =

이러한 오버 로드 된 할당 연산자는 원본 값을이 개체에 복사 `COleSafeArray` 합니다.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>설명

각 연산자에 대 한 간략 한 설명은 다음과 같습니다.

- **연산자 = (** *saSrc* **)** 기존 `COleSafeArray` 개체를이 개체에 복사 합니다.

- **operator = (** *varsrc* **)** 기존 `VARIANT` 또는 `COleVariant` 배열을이 개체에 복사 합니다.

- **operator = (** *psrc* **)** `VARIANT` *Psrc* 에서 액세스 하는 배열 개체를이 개체에 복사 합니다.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a> COleSafeArray:: operator = =

이 연산자는 두 배열 ( `SAFEARRAY` , `VARIANT` , `COleVariant` 또는 `COleSafeArray` 배열)을 비교 하 고 동일 하면 0이 아닌 값을 반환 하 고 그렇지 않으면 0을 반환 합니다.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>설명

두 배열의 차수가 동일 하 고, 각 차원에 동일한 크기가 있고, 요소 값이 같으면 두 배열이 동일 합니다.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a> COleSafeArray:: operator &lt;&lt;

`COleSafeArray`삽입 (<<) 연산자는 `COleSafeArray` 보관에 대 한 개체의 진단 덤프 및 저장을 지원 합니다.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a> COleSafeArray::P trOfIndex

인덱스 값으로 지정 된 요소에 대 한 포인터를 반환 합니다.

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>매개 변수

*rgIndices*<br/>
배열의 요소를 식별 하는 인덱스 값의 배열입니다. 요소에 대 한 모든 인덱스를 지정 해야 합니다.

*ppvData*<br/>
반환 시 *rgIndices* 의 값으로 식별 되는 요소에 대 한 포인터입니다.

## <a name="colesafearrayputelement"></a><a name="putelement"></a> COleSafeArray::P utElement

단일 요소를 배열에 할당합니다.

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>매개 변수

*rgIndices*<br/>
각 배열 차원의 인덱스 배열에 대한 포인터입니다.

*pvData*<br/>
배열에 할당할 데이터에 대한 포인터입니다. VT_DISPATCH, VT_UNKNOWN 및 VT_BSTR variant 형식은 포인터 이며 다른 수준의 간접 참조가 필요 하지 않습니다.

### <a name="remarks"></a>설명

이 함수는 요소를 할당 하기 전과 후에 Windows 함수 [Safearraylock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) 및 [safearraylock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) 을 자동으로 호출 합니다. 데이터 요소가 문자열, 개체 또는 Variant이면 함수는 이를 올바르게 복사하고 기존 요소가 문자열, 개체 또는 Variant이면 제대로 지워집니다.

배열에는 여러 잠금이 있을 수 있으므로 다른 작업에 의해 배열이 잠긴 동안 요소를 배열에 삽입할 수 있습니다.

오류가 발생 하면 함수는 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a> COleSafeArray:: Redim

안전 배열의 최하위 (가장 오른쪽) 범위를 변경 합니다.

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>매개 변수

*psaboundNew*<br/>
새 배열 바운드가 포함 된 새 안전 배열 바인딩 구조체에 대 한 포인터입니다. 배열의 최하위 차원만 변경할 수 있습니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a> COleSafeArray:: ResizeOneDim

1 차원 개체의 요소 수를 변경 `COleSafeArray` 합니다.

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>매개 변수

*dwElements*<br/>
1 차원 안전 배열의 요소 수입니다.

### <a name="remarks"></a>설명

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

  [Colesafearray:: CreateOneDim](#createonedim)의 예제를 참조 하세요.

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a> COleSafeArray:: UnaccessData

배열의 잠금 횟수를 감소 시키고로 검색 된 포인터를 무효화 `AccessData` 합니다.

```cpp
void UnaccessData();
```

### <a name="remarks"></a>설명

오류가 발생 하면 함수에서 [Coleexception](../../mfc/reference/coleexception-class.md)을 throw 합니다.

### <a name="example"></a>예제

  [Colesafearray:: AccessData](#accessdata)의 예제를 참조 하세요.

## <a name="colesafearrayunlock"></a><a name="unlock"></a> COleSafeArray:: Unlock

배열의 잠금 횟수를 감소 시켜 해제 하거나 크기를 조정할 수 있습니다.

```cpp
void Unlock();
```

### <a name="remarks"></a>설명

이 함수는 배열에서 데이터에 액세스 하는 작업이 완료 된 후 호출 됩니다. 오류가 발생 하면 [Coleexception](../../mfc/reference/coleexception-class.md)이 throw 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 클래스](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 클래스](../../mfc/reference/cdatabase-class.md)<br/>

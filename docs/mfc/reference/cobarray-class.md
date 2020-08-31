---
title: CObArray 클래스
description: '`CObArray` `MFC` 배열에 포인터를 저장 하는 클래스에 대 한 API 참조 `CObject` 입니다.'
ms.date: 08/27/2020
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: cbc1799a9634b3d8c09077b755b8a097289460fd
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062149"
---
# <a name="cobarray-class"></a>CObArray 클래스

`CObject` 포인터 배열을 지원합니다.

## <a name="syntax"></a>구문

```cpp
class CObArray : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CObArray:: CObArray](#cobarray)|포인터에 대 한 빈 배열을 생성 `CObject` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CObArray:: Add](#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CObArray:: Append](#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|
|[CObArray:: Copy](#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CObArray:: ElementAt](#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|
|[CObArray:: FreeExtra](#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CObArray:: GetAt](#getat)|지정된 인덱스의 값을 반환합니다.|
|[CObArray:: GetCount](#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CObArray:: GetData](#getdata)|배열의 요소에 대한 액세스를 허용합니다. `NULL`일 수 있습니다.|
|[CObArray:: GetSize](#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CObArray:: System.array.getupperbound](#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[CObArray:: InsertAt](#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CObArray:: IsEmpty](#isempty)|배열이 비어 있는지를 확인합니다.|
|[CObArray:: RemoveAll](#removeall)|이 배열의 모든 요소를 반환합니다.|
|[CObArray:: RemoveAt](#removeat)|특정 인덱스의 요소를 제거합니다.|
|[CObArray:: SetAt](#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CObArray:: SetAtGrow](#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CObArray:: SetSize](#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[CObArray:: operator \[\]](#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

이러한 개체 배열은 C 배열과 유사 하지만 필요에 따라 동적으로 축소 하 고 확장할 수 있습니다.

배열 인덱스는 항상 0 위치에서 시작 합니다. 상한을 수정할지 아니면 현재 바인딩된 요소를 벗어나는 요소를 추가할 때 배열을 확장할 수 있는지 여부를 결정할 수 있습니다. 일부 요소가 인 경우에도 메모리는 상한에 인접 하 게 할당 됩니다 `NULL` .

Win32에서 개체의 크기는 `CObArray` 사용 가능한 메모리로만 제한 됩니다.

C 배열과 마찬가지로 인덱싱된 요소에 대 한 액세스 시간은 `CObArray` 상수 이며 배열 크기와는 독립적입니다.

`CObArray` 는 IMPLEMENT_SERIAL 매크로를 통합 하 여 요소의 serialization 및 덤프를 지원 합니다. `CObject`오버 로드 된 삽입 연산자나 멤버 함수를 사용 하 여 포인터 배열을 보관에 저장 한 경우 `Serialize` 각 `CObject` 요소는 차례로 배열 인덱스와 함께 직렬화 됩니다.

배열의 개별 요소에 대 한 덤프가 필요한 경우 `CObject` 개체의 깊이를 `CDumpContext` 1 이상으로 설정 해야 합니다.

개체를 `CObArray` 삭제 하거나 해당 요소를 제거 하면 `CObject` 참조 하는 개체가 아니라 포인터만 제거 됩니다.

> [!NOTE]
> 배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

배열 클래스 파생은 목록 파생과 비슷합니다. 특수 한 용도의 목록 클래스의 파생에 대 한 자세한 내용은 [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

> [!NOTE]
> 배열을 serialize 하려는 경우 파생 클래스의 구현에서 IMPLEMENT_SERIAL 매크로를 사용 해야 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a> CObArray:: Add

배열의 끝에 새 요소를 추가 하 여 배열을 1 만큼 증가 합니다.

```cpp
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>매개 변수

*newElement*\
`CObject`이 배열에 추가할 포인터입니다.

### <a name="return-value"></a>반환 값

추가 된 요소의 인덱스입니다.

### <a name="remarks"></a>설명

[SetSize](#setsize) 가 1 보다 큰 *nGrowBy* 값을 사용 하는 경우 추가 메모리가 할당 될 수 있습니다. 그러나 상한을 1 씩 증가 시킵니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::Add` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Add(BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Add(DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Add(void* newElement);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Add(LPCTSTR newElement); throw(CMemoryException*);`<br /><br />`INT_PTR Add(const CString& newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Add(UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Add(WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>예제

  모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a> CObArray:: Append

이 멤버 함수를 호출 하 여 다른 배열의 내용을 지정 된 배열의 끝에 추가 합니다.

```cpp
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>매개 변수

*소스*\
배열에 추가할 요소의 원본입니다.

### <a name="return-value"></a>반환 값

추가 된 첫 번째 요소의 인덱스입니다.

### <a name="remarks"></a>설명

배열의 형식은 동일 해야 합니다.

필요한 경우에서 `Append` 추가 메모리를 할당 하 여 배열에 추가 된 요소를 수용할 수 있습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::Append` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Append(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Append(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Append(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Append(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Append(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Append(const CWordArray& src);`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a> CObArray:: Copy

지정 된 배열의 요소를 동일한 형식의 다른 배열 요소로 덮어쓰려면이 멤버 함수를 호출 합니다.

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>매개 변수

*소스*\
배열에 복사할 요소의 원본입니다.

### <a name="remarks"></a>설명

`Copy` 메모리를 해제 하지 않습니다. 필요한 경우 `Copy` 배열에 복사 된 요소를 수용 하기 위해에서 추가 메모리를 할당할 수 있습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::Copy` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void Copy(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void Copy(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void Copy(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void Copy(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void Copy(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void Copy(const CWordArray& src);`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a> CObArray:: CObArray

빈 `CObject` 포인터 배열을 생성 합니다.

```cpp
CObArray();
```

### <a name="remarks"></a>설명

배열은 한 번에 하나의 요소를 늘립니다.

다음 표에서는와 유사한 다른 생성자를 보여 줍니다 `CObArray::CObArray` .

|클래스|생성자|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`CByteArray();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`CDWordArray();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`CPtrArray();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CStringArray();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`CUIntArray();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`CWordArray();`|

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a> CObArray:: ElementAt

배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.

```cpp
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
0 보다 크거나 같고에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다 `GetUpperBound` .

### <a name="return-value"></a>반환 값

포인터에 대 한 참조 `CObject` 입니다.

### <a name="remarks"></a>설명

배열의 왼쪽 할당 연산자를 구현 하는 데 사용 됩니다. 특수 배열 연산자를 구현 하는 데만 사용 해야 하는 고급 함수입니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::ElementAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& ElementAt(INT_PTR nIndex);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& ElementAt(INT_PTR nIndex);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& ElementAt(INT_PTR nIndex);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& ElementAt(INT_PTR nIndex);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& ElementAt(INT_PTR nIndex);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& ElementAt(INT_PTR nIndex);`|

### <a name="example"></a>예제

[CObArray:: GetSize](#getsize)의 예제를 참조 하세요.

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a> CObArray:: FreeExtra

배열이 증가 하는 동안 할당 된 추가 메모리를 해제 합니다.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>설명

이 함수는 배열의 크기나 상한에는 영향을 주지 않습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::FreeExtra` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void FreeExtra();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void FreeExtra();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void FreeExtra();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void FreeExtra();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void FreeExtra();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void FreeExtra();`|

### <a name="example"></a>예제

  [CObArray:: GetData](#getdata)의 예제를 참조 하세요.

## <a name="cobarraygetat"></a><a name="getat"></a> CObArray:: GetAt

지정 된 인덱스에 있는 배열 요소를 반환 합니다.

```cpp
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
0 보다 크거나 같고에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다 `GetUpperBound` .

### <a name="return-value"></a>반환 값

`CObject`현재이 인덱스에 있는 포인터 요소입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 에서 반환 된 값 보다 큰 값 이나 음수 값을 전달 `GetUpperBound` 하면 어설션이 실패 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::GetAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE GetAt(INT_PTR nIndex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD GetAt(INT_PTR nIndex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void* GetAt(INT_PTR nIndex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString GetAt(INT_PTR nIndex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT GetAt(INT_PTR nIndex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD GetAt(INT_PTR nIndex) const;`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a> CObArray:: GetCount

배열 요소의 수를 반환 합니다.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

배열의 항목 수입니다.

### <a name="remarks"></a>설명

배열의 요소 수를 검색 하려면이 메서드를 호출 합니다. 인덱스는 0부터 시작 하므로 크기는 1에서 가장 큰 인덱스 보다 큽니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::GetCount` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetCount() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetCount() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetCount() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetCount() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetCount() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetCount() const;`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a> CObArray:: GetData

이 멤버 함수를 사용 하 여 배열의 요소에 직접 액세스할 수 있습니다.

```cpp
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>반환 값

포인터의 배열에 대 한 포인터 `CObject` 입니다.

### <a name="remarks"></a>설명

사용할 수 있는 요소가 없는 경우는 `GetData` 값을 반환 `NULL` 합니다.

배열의 요소에 대 한 직접 액세스를 통해 보다 신속 하 게 작업 하는 데 도움이 되지만를 호출할 때 주의를 기울여야 `GetData` 합니다. 발생 하는 모든 오류는 배열의 요소에 직접적인 영향을 줍니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::GetData` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`const BYTE* GetData() const; BYTE* GetData();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`const DWORD* GetData() const; DWORD* GetData();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`const void** GetData() const; void** GetData();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`const CString* GetData() const; CString* GetData();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`const UINT* GetData() const; UINT* GetData();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`const WORD* GetData() const; WORD* GetData();`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a> CObArray:: GetSize

배열의 크기를 반환합니다.

```cpp
INT_PTR GetSize() const;
```

### <a name="remarks"></a>설명

인덱스는 0부터 시작 하므로 크기는 1에서 가장 큰 인덱스 보다 큽니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::GetSize` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetSize() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetSize() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetSize() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetSize() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetSize() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetSize() const;`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a> CObArray:: System.array.getupperbound

이 배열의 현재 상한을 반환 합니다.

```cpp
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>반환 값

상한의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

배열 인덱스는 0부터 시작 하므로이 함수는 1 보다 작은 값을 반환 `GetSize` 합니다.

이 조건은 `GetUpperBound() = -1` 배열에 요소가 포함 되어 있지 않음을 나타냅니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::GetUpperBound` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetUpperBound() const;`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a> CObArray:: InsertAt

지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.

```cpp
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다 `GetUpperBound` .

*newElement*\
`CObject`이 배열에 배치할 포인터입니다. 값의 *Newelement* 를 `NULL` 사용할 수 있습니다.

*n 개수*\
이 요소를 삽입 해야 하는 횟수입니다. 기본값은 1입니다.

*nStartIndex*\
에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다 `GetUpperBound` .

*pNewArray*\
이 배열에 추가할 요소를 포함 하는 다른 배열입니다.

### <a name="remarks"></a>설명

첫 번째 버전은 `InsertAt` 배열의 지정 된 인덱스에 하나의 요소 (또는 요소의 여러 복사본)를 삽입 합니다. 이 프로세스에서는 인덱스를 증가 시켜이 인덱스에 있는 기존 요소를 위로 이동 하 고 위의 모든 요소를 위로 이동 합니다.

두 번째 버전은 `CObArray` *nstartindex* 위치에서 시작 하 여 다른 컬렉션의 모든 요소를 삽입 합니다.

`SetAt`반면 함수는 지정 된 하나의 배열 요소를 대체 하 고 아무 요소도 이동 하지 않습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::InsertAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void InsertAt(INT_PTR nIndex, BYTE newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CByteArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void InsertAt(INT_PTR nIndex, DWORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CDWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void InsertAt(INT_PTR nIndex, void* newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CPtrArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void InsertAt(INT_PTR nIndex, LPCTSTR newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CStringArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void InsertAt(INT_PTR nIndex, UINT newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CUIntArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void InsertAt(INT_PTR nIndex, WORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>예제

  모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a> CObArray:: IsEmpty

배열이 비어 있는지를 확인합니다.

```cpp
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

배열이 비어 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a> CObArray:: operator []

이러한 첨자 연산자는 및 함수에 대 한 편리한 대체 방법 `SetAt` `GetAt` 입니다.

```cpp
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>설명

이 아닌 배열에 대해 호출 되는 첫 번째 연산자는 **`const`** 대입문의 right (r-value) 또는 left (l-value)에서 사용할 수 있습니다. 배열에 대해 호출 되는 두 번째는 **`const`** 오른쪽에만 사용할 수 있습니다.

라이브러리의 디버그 버전은 대입문 (대입문의 왼쪽 또는 오른쪽)이 범위를 벗어난 경우 어설션 합니다.

다음 표에서는와 유사한 다른 연산자를 보여 줍니다 `CObArray::operator []` .

|클래스|연산자|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& operator [](INT_PTR nindex);`<br /><br />`BYTE operator [](INT_PTR nindex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& operator [](INT_PTR nindex);`<br /><br />`DWORD operator [](INT_PTR nindex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& operator [](INT_PTR nindex);`<br /><br />`void* operator [](INT_PTR nindex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& operator [](INT_PTR nindex);`<br /><br />`CString operator [](INT_PTR nindex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& operator [](INT_PTR nindex);`<br /><br />`UINT operator [](INT_PTR nindex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& operator [](INT_PTR nindex);`<br /><br />`WORD operator [](INT_PTR nindex) const;`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a> CObArray:: RemoveAll

이 배열에서 모든 포인터를 제거 하지만 실제로 개체를 삭제 하지는 않습니다 `CObject` .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

배열이 이미 비어 있으면 함수는 계속 작동 합니다.

`RemoveAll`함수는 포인터 저장소에 사용 되는 모든 메모리를 해제 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::RemoveAll` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAll();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAll();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAll();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAll();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAll();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAll();`|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a> CObArray:: RemoveAt

배열의 지정 된 인덱스에서 시작 하는 하나 이상의 요소를 제거 합니다.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
0 보다 크거나 같고에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다 `GetUpperBound` .

*n 개수*\
제거할 요소의 수입니다.

### <a name="remarks"></a>설명

이 프로세스에서는 제거 된 요소 위의 모든 요소를 아래로 이동 합니다. 배열의 상한을 감소 시키지만 메모리를 해제 하지는 않습니다.

제거 지점 위의 배열에 포함 된 것 보다 더 많은 요소를 제거 하려고 하면 라이브러리의 디버그 버전이 어설션 됩니다.

`RemoveAt`함수는 `CObject` 배열에서 포인터를 제거 하지만 개체 자체는 삭제 하지 않습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::RemoveAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|

### <a name="example"></a>예제

  모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a> CObArray:: SetAt

지정 된 인덱스에 배열 요소를 설정 합니다.

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
0 보다 크거나 같고에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다 `GetUpperBound` .

*newElement*\
이 배열에 삽입할 개체 포인터입니다. `NULL`값을 사용할 수 있습니다.

### <a name="remarks"></a>설명

`SetAt` 배열을 증가 시 키도 안 됩니다. `SetAtGrow`배열이 자동으로 증가 하도록 하려면를 사용 합니다.

인덱스 값이 배열의 올바른 위치를 나타내는지 확인 하십시오. 범위를 벗어나면 라이브러리의 디버그 버전이 어설션 됩니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::SetAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAt(INT_PTR nIndex, BYTE newElement);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAt(INT_PTR nIndex, DWORD newElement);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAt(INT_PTR nIndex, void* newElement);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAt(INT_PTR nIndex, LPCTSTR newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAt(INT_PTR nIndex, UINT newElement);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAt(INT_PTR nIndex, WORD newElement);`|

### <a name="example"></a>예제

  모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a> CObArray:: SetAtGrow

지정 된 인덱스에 배열 요소를 설정 합니다.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>매개 변수

*n 인덱스*\
0 보다 크거나 같은 정수 인덱스입니다.

*newElement*\
이 배열에 추가할 개체 포인터입니다. `NULL`값을 사용할 수 있습니다.

### <a name="remarks"></a>설명

필요한 경우 배열이 자동으로 증가 합니다. 즉, 상한이 새 요소에 맞게 조정 됩니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::SetAtGrow` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAtGrow(INT_PTR nIndex, BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAtGrow(INT_PTR nIndex, void* newElement);`<br /><br />`throw( CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAtGrow(INT_PTR nIndex, LPCTSTR newElement);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAtGrow(INT_PTR nIndex, UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>예제

  모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a> CObArray:: SetSize

비어 있거나 기존 배열의 크기를 설정 합니다. 필요한 경우 메모리를 할당 합니다.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>매개 변수

*nNewSize*\
새 배열 크기 (요소 수)입니다. 0보다 크거나 같아야 합니다.

*nGrowBy*\
크기 증가가 필요한 경우 할당할 요소 슬롯의 최소 개수입니다.

### <a name="remarks"></a>설명

새 크기가 이전 크기 보다 작으면 배열이 잘리고 사용 하지 않는 모든 메모리가 해제 됩니다. 효율성을 위해를 호출 하 여 `SetSize` 배열의 크기를 설정 합니다. 이렇게 하면 항목이 추가 될 때마다 배열을 다시 할당 하 고 복사할 필요가 없습니다.

*NGrowBy* 매개 변수는 배열이 증가 하는 동안 내부 메모리 할당에 영향을 줍니다. 해당 사용은 및에서 보고 하는 배열 크기에 영향을 주지 않습니다 `GetSize` `GetUpperBound` .

배열의 크기가 커지면 새로 할당 `CObject *` 된 모든 포인터가로 설정 됩니다 `NULL` .

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CObArray::SetSize` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|

### <a name="example"></a>예제

  [CObArray:: GetData](#getdata)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)\
[계층 구조 차트](../../mfc/hierarchy-chart.md)\
[CStringArray 클래스](../../mfc/reference/cstringarray-class.md)\
[CPtrArray 클래스](../../mfc/reference/cptrarray-class.md)\
[CByteArray 클래스](../../mfc/reference/cbytearray-class.md)\
[CWordArray 클래스](../../mfc/reference/cwordarray-class.md)\
[CDWordArray 클래스](../../mfc/reference/cdwordarray-class.md)

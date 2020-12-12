---
description: '자세히 알아보기: CArray 클래스'
title: CArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 2aea88178347fd146720a8205974049e4baf039f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259645"
---
# <a name="carray-class"></a>CArray 클래스

는 C 배열과 유사한 배열을 지원 하지만 필요에 따라 동적으로 감소 하 고 확장할 수 있습니다.

## <a name="syntax"></a>구문

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열에 저장 된 개체의 형식을 지정 하는 템플릿 매개 변수입니다. *TYPE* 은에서 반환 하는 매개 변수입니다 `CArray` .

*ARG_TYPE*<br/>
배열에 저장 된 개체에 액세스 하는 데 사용 되는 인수 형식을 지정 하는 템플릿 매개 변수입니다. 일반적으로 *형식* 에 대 한 참조입니다. *ARG_TYPE* 은에 전달 되는 매개 변수입니다 `CArray` .

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CArray:: CArray](#carray)|빈 배열을 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CArray:: Add](#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CArray:: Append](#append)|배열에 다른 배열을 추가 합니다. 필요한 경우 배열 증가|
|[CArray:: Copy](#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CArray:: ElementAt](#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|
|[CArray:: FreeExtra](#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CArray:: GetAt](#getat)|지정된 인덱스의 값을 반환합니다.|
|[CArray:: GetCount](#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CArray:: GetData](#getdata)|배열의 요소에 대한 액세스를 허용합니다. NULL일 수 있습니다.|
|[CArray:: GetSize](#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CArray:: System.array.getupperbound](#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[CArray:: InsertAt](#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CArray:: IsEmpty](#isempty)|배열이 비어 있는지 여부를 확인 합니다.|
|[CArray:: RemoveAll](#removeall)|이 배열의 모든 요소를 반환합니다.|
|[CArray:: RemoveAt](#removeat)|특정 인덱스의 요소를 제거합니다.|
|[CArray:: SetAt](#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CArray:: SetAtGrow](#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CArray:: SetSize](#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

배열 인덱스는 항상 0 위치에서 시작 합니다. 상한을 수정할지 아니면 현재 바인딩된 요소를 벗어나는 요소를 추가할 때 배열을 확장할 수 있는지 여부를 결정할 수 있습니다. 일부 요소가 null 인 경우에도 메모리는 상한에 인접 하 게 할당 됩니다.

> [!NOTE]
> 개체 크기를 조정 하거나 요소를 추가 하는 대부분의 메서드는 `CArray` [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) 를 사용 하 여 요소를 이동 합니다. `memcpy_s`는 생성자를 호출 해야 하는 개체와 호환 되지 않기 때문에 문제가 발생 합니다. 의 항목이 `CArray` 와 호환 되지 않는 경우 `memcpy_s` `CArray` 적절 한 크기의 새를 만들어야 합니다. 그런 다음 [CArray:: Copy](#copy) 및 [CArray:: setat](#setat) 를 사용 하 여 새 배열을 채워야 합니다. 이러한 메서드는 대신 대입 연산자를 사용 하기 때문 `memcpy_s` 입니다.

C 배열과 마찬가지로 인덱싱된 요소에 대 한 액세스 시간은 `CArray` 상수 이며 배열 크기와는 독립적입니다.

> [!TIP]
> 배열을 사용 하기 전에 [SetSize](#setsize) 를 사용 하 여 크기를 설정 하 고 메모리를 할당 합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

배열의 개별 요소에 대 한 덤프가 필요한 경우 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 개체의 깊이를 1 이상으로 설정 해야 합니다.

이 클래스의 특정 멤버 함수는 대부분의 클래스 사용에 대해 사용자 지정 해야 하는 전역 도우미 함수를 호출 합니다 `CArray` . MFC 매크로 및 전역 섹션에서 [컬렉션 클래스 도우미](../../mfc/reference/collection-class-helpers.md) 항목을 참조 하세요.

배열 클래스 파생은 목록 파생과 비슷합니다.

를 사용 하는 방법에 대 한 자세한 내용은 `CArray` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a> CArray:: Add

배열의 끝에 새 요소를 추가 하 여 배열을 1 만큼 증가 합니다.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*ARG_TYPE*<br/>
이 배열의 요소를 참조 하는 인수의 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
이 배열에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

추가 된 요소의 인덱스입니다.

### <a name="remarks"></a>설명

[SetSize](#setsize) 가 1 보다 큰 값을 사용 하는 경우 `nGrowBy` 추가 메모리가 할당 될 수 있습니다. 그러나 상한을 1 씩 증가 시킵니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a> CArray:: Append

한 배열의 내용을 다른 배열의 끝에 추가 하려면이 멤버 함수를 호출 합니다.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
배열에 추가할 요소의 원본입니다.

### <a name="return-value"></a>반환 값

추가 된 첫 번째 요소의 인덱스입니다.

### <a name="remarks"></a>설명

배열의 형식은 동일 해야 합니다.

필요한 경우에서 `Append` 추가 메모리를 할당 하 여 배열에 추가 된 요소를 수용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a> CArray:: CArray

빈 배열을 생성합니다.

```
CArray();
```

### <a name="remarks"></a>설명

배열은 한 번에 하나의 요소를 늘립니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a> CArray:: Copy

한 배열의 요소를 다른 배열에 복사 하려면이 멤버 함수를 사용 합니다.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
배열에 복사할 요소의 원본입니다.

### <a name="remarks"></a>설명

한 배열의 요소를 다른 배열의 요소로 덮어쓰려면이 멤버 함수를 호출 합니다.

`Copy` 메모리를 해제 하지 않습니다. 그러나 필요한 경우 `Copy` 배열에 복사 된 요소를 수용 하기 위해 추가 메모리를 할당할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a> CArray:: ElementAt

배열 내에서 지정 된 요소에 대 한 임시 참조를 반환 합니다.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같고 [system.array.getupperbound](#getupperbound)에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

### <a name="return-value"></a>반환 값

배열 요소에 대 한 참조입니다.

### <a name="remarks"></a>설명

배열의 왼쪽 할당 연산자를 구현 하는 데 사용 됩니다.

### <a name="example"></a>예제

  [Getsize](#getsize)의 예제를 참조 하세요.

## <a name="carrayfreeextra"></a><a name="freeextra"></a> CArray:: FreeExtra

배열이 증가 하는 동안 할당 된 추가 메모리를 해제 합니다.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>설명

이 함수는 배열의 크기나 상한에는 영향을 주지 않습니다.

### <a name="example"></a>예제

  [GetData](#getdata)의 예제를 참조 하세요.

## <a name="carraygetat"></a><a name="getat"></a> CArray:: GetAt

지정 된 인덱스에 있는 배열 요소를 반환 합니다.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*nIndex*<br/>
0 보다 크거나 같고 [system.array.getupperbound](#getupperbound)에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

### <a name="return-value"></a>반환 값

현재이 인덱스에 있는 배열 요소입니다.

### <a name="remarks"></a>설명

에서 반환 된 값 보다 큰 값 이나 음수 값을 전달 `GetUpperBound` 하면 어설션이 실패 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a> CArray:: GetCount

배열 요소의 수를 반환 합니다.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

배열의 항목 수입니다.

### <a name="remarks"></a>설명

배열의 요소 수를 검색 하려면이 메서드를 호출 합니다. 인덱스는 0부터 시작 하므로 크기는 1에서 가장 큰 인덱스 보다 큽니다. 이 메서드를 호출 하면 [CArray:: GetSize](#getsize) 메서드와 동일한 결과가 생성 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a> CArray:: GetData

이 멤버 함수를 사용 하 여 배열의 요소에 직접 액세스할 수 있습니다.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

배열 요소에 대 한 포인터입니다.

### <a name="remarks"></a>설명

사용할 수 있는 요소가 없는 경우는 `GetData` null 값을 반환 합니다.

배열의 요소에 대 한 직접 액세스를 통해 보다 신속 하 게 작업 하는 데 도움이 되지만를 호출할 때 주의를 기울여야 `GetData` 합니다. 발생 하는 모든 오류는 배열의 요소에 직접적인 영향을 줍니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a> CArray:: GetSize

배열의 크기를 반환합니다.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>설명

인덱스는 0부터 시작 하므로 크기는 1에서 가장 큰 인덱스 보다 큽니다. 이 메서드를 호출 하면 [CArray:: GetCount](#getcount) 메서드와 동일한 결과가 생성 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a> CArray:: System.array.getupperbound

이 배열의 현재 상한을 반환 합니다.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>설명

배열 인덱스는 0부터 시작 하므로이 함수는 1 보다 작은 값을 반환 `GetSize` 합니다.

조건 `GetUpperBound( )` =-1은 배열에 요소가 포함 되어 있지 않음을 나타냅니다.

### <a name="example"></a>예제

  [CArray:: GetAt](#getat)의 예제를 참조 하세요.

## <a name="carrayinsertat"></a><a name="insertat"></a> CArray:: InsertAt

첫 번째 버전은 `InsertAt` 배열의 지정 된 인덱스에 하나의 요소 (또는 요소의 여러 복사본)를 삽입 합니다.

```cpp
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다 `GetUpperBound` .

*ARG_TYPE*<br/>
이 배열의 요소 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
이 배열에 배치할 요소입니다.

*nCount*<br/>
이 요소를 삽입 해야 하는 횟수입니다. 기본값은 1입니다.

*nStartIndex*<br/>
[System.array.getupperbound](#getupperbound)에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다.

*pNewArray*<br/>
이 배열에 추가할 요소를 포함 하는 다른 배열입니다.

### <a name="remarks"></a>설명

이 프로세스에서는 인덱스를 증가 시켜이 인덱스에 있는 기존 요소를 위로 이동 하 고 위의 모든 요소를 위로 이동 합니다.

두 번째 버전은 `CArray` *nstartindex* 위치에서 시작 하 여 다른 컬렉션의 모든 요소를 삽입 합니다.

`SetAt`반면 함수는 지정 된 하나의 배열 요소를 대체 하 고 아무 요소도 이동 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a> CArray:: IsEmpty

배열이 비어 있는지 여부를 확인 합니다.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

배열에 요소가 없으면 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="carrayoperator-"></a><a name="operator_at"></a> CArray:: operator \[\]

이러한 첨자 연산자는 [Setat](#setat) 및 [GetAt](#getat) 함수를 편리 하 게 대체 합니다.

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
이 배열의 요소 형식을 지정 하는 템플릿 매개 변수입니다.

*nIndex*<br/>
액세스할 요소의 인덱스입니다.

### <a name="remarks"></a>설명

이 아닌 배열에 대해 호출 되는 첫 번째 연산자는 **`const`** 할당 문의 오른쪽 (r-값) 이나 왼쪽 (l-value)에서 사용할 수 있습니다. 배열에 대해 호출 되는 두 번째는 **`const`** 오른쪽에만 사용할 수 있습니다.

라이브러리의 디버그 버전은 대입문 (대입문의 왼쪽 또는 오른쪽)이 범위를 벗어난 경우 어설션 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a> CArray:: RelocateElements

배열을 확장 하거나 축소할 때 데이터를 새 버퍼에 재배치 합니다.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>매개 변수

*pNewData*<br/>
요소의 배열에 대 한 새 버퍼입니다.

*pData*<br/>
요소의 이전 배열입니다.

*nCount*<br/>
이전 배열의 요소 수입니다.

### <a name="remarks"></a>설명

*pNewData* 는 항상 모든 *.pdata* 요소를 저장할 수 있을 만큼 커야 합니다.

[CArray](../../mfc/reference/carray-class.md) 구현에서는이 메서드를 사용 하 여 배열을 확장 하거나 축소할 때 ( [SetSize](#setsize) 또는 [freeextra](#freeextra) 를 호출한 경우)이 메서드를 사용 하 여 이전 데이터를 새 버퍼에 복사 합니다. 기본 구현에서는 데이터만 복사 합니다.

요소가 자체 멤버 중 하나에 대 한 포인터를 포함 하는 배열 또는 다른 구조체에 배열 요소 중 하나에 대 한 포인터가 포함 된 경우 포인터는 일반 복사본으로 업데이트 되지 않습니다. 이 경우 관련 형식으로의 특수화를 구현 하 여 포인터를 수정할 수 있습니다 `RelocateElements` . 데이터 복사를 담당 하기도 합니다.

## <a name="carrayremoveall"></a><a name="removeall"></a> CArray:: RemoveAll

이 배열의 모든 요소를 반환합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

배열이 이미 비어 있으면 함수는 계속 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a> CArray:: RemoveAt

배열의 지정 된 인덱스에서 시작 하는 하나 이상의 요소를 제거 합니다.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같고 [system.array.getupperbound](#getupperbound)에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

*nCount*<br/>
제거할 요소의 수입니다.

### <a name="remarks"></a>설명

이 프로세스에서는 제거 된 요소 위의 모든 요소를 아래로 이동 합니다. 배열의 상한을 감소 시키지만 메모리를 해제 하지는 않습니다.

제거 지점 위의 배열에 포함 된 것 보다 더 많은 요소를 제거 하려고 하면 라이브러리의 디버그 버전이 어설션 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a> CArray:: SetAt

지정 된 인덱스에 배열 요소를 설정 합니다.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같고 [system.array.getupperbound](#getupperbound)에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

*ARG_TYPE*<br/>
배열 요소를 참조 하는 데 사용 되는 인수의 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
지정 된 위치에 저장할 새 요소 값입니다.

### <a name="remarks"></a>설명

`SetAt` 는 배열을 증가 시 키 지 않습니다. 배열이 자동으로 증가 하 게 하려면 [SetAtGrow](#setatgrow) 를 사용 합니다.

인덱스 값이 배열의 올바른 위치를 나타내는지 확인 해야 합니다. 범위를 벗어나면 라이브러리의 디버그 버전이 어설션 됩니다.

### <a name="example"></a>예제

  [GetAt](#getat)의 예제를 참조 하세요.

## <a name="carraysetatgrow"></a><a name="setatgrow"></a> CArray:: SetAtGrow

지정 된 인덱스에 배열 요소를 설정 합니다.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같은 정수 인덱스입니다.

*ARG_TYPE*<br/>
배열의 요소 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
이 배열에 추가할 요소입니다. NULL 값을 사용할 수 있습니다.

### <a name="remarks"></a>설명

필요한 경우 배열이 자동으로 증가 합니다. 즉, 상한이 새 요소에 맞게 조정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a> CArray:: SetSize

비어 있거나 기존 배열의 크기를 설정 합니다. 필요한 경우 메모리를 할당 합니다.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>매개 변수

*nNewSize*<br/>
새 배열 크기 (요소 수)입니다. 0보다 크거나 같아야 합니다.

*nGrowBy*<br/>
크기 증가가 필요한 경우 할당할 요소 슬롯의 최소 개수입니다.

### <a name="remarks"></a>설명

새 크기가 이전 크기 보다 작으면 배열이 잘리고 사용 하지 않는 모든 메모리가 해제 됩니다.

배열 사용을 시작 하기 전에이 함수를 사용 하 여 배열의 크기를 설정 합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

*NGrowBy* 매개 변수는 배열이 증가 하는 동안 내부 메모리 할당에 영향을 줍니다. [Getsize](#getsize) 및 [system.array.getupperbound](#getupperbound)에서 보고 하는 배열 크기에는 영향을 주지 않습니다. 기본값이 사용 되는 경우 MFC는 메모리 조각화를 방지 하 고 대부분의 경우 효율성을 최적화 하기 위해 계산 방식으로 메모리를 할당 합니다.

### <a name="example"></a>예제

  [GetData](#getdata)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObArray 클래스](../../mfc/reference/cobarray-class.md)<br/>
[컬렉션 클래스 도우미](../../mfc/reference/collection-class-helpers.md)

---
description: '자세히 알아보기: CAtlArray 클래스'
title: CAtlArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 0ae3f5aef84cac64adba20ef438f5063abda098e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158428"
---
# <a name="catlarray-class"></a>CAtlArray 클래스

이 클래스는 배열 개체를 구현 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

### <a name="parameters"></a>매개 변수

*E*<br/>
배열에 저장할 데이터의 형식입니다.

*ETraits*<br/>
요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다.

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|함수|설명|
|-|-|
|[추가](#add)|배열 개체에 요소를 추가 하려면이 메서드를 호출 합니다.|
|[Append](#append)|한 배열의 내용을 다른 배열의 끝에 추가 하려면이 메서드를 호출 합니다.|
|[AssertValid](#assertvalid)|배열 개체가 유효한 지 확인 하려면이 메서드를 호출 합니다.|
|[CAtlArray](#catlarray)|생성자입니다.|
|[~ CAtlArray](#dtor)|소멸자입니다.|
|[복사](#copy)|한 배열의 요소를 다른 배열의 요소에 복사 하려면이 메서드를 호출 합니다.|
|[FreeExtra](#freeextra)|배열에서 빈 요소를 제거 하려면이 메서드를 호출 합니다.|
|[GetAt](#getat)|배열 개체에서 단일 요소를 검색 하려면이 메서드를 호출 합니다.|
|[GetCount](#getcount)|배열에 저장 된 요소의 수를 반환 하려면이 메서드를 호출 합니다.|
|[GetData](#getdata)|배열의 첫 번째 요소에 대 한 포인터를 반환 하려면이 메서드를 호출 합니다.|
|[InsertArrayAt](#insertarrayat)|한 배열을 다른 배열에 삽입 하려면이 메서드를 호출 합니다.|
|[InsertAt](#insertat)|이 메서드를 호출 하 여 새 요소 (또는 요소의 여러 복사본)를 배열 개체에 삽입 합니다.|
|[IsEmpty](#isempty)|배열이 비어 있는지 테스트 하려면이 메서드를 호출 합니다.|
|[RemoveAll](#removeall)|이 메서드를 호출 하 여 배열 개체에서 모든 요소를 제거 합니다.|
|[RemoveAt](#removeat)|배열에서 하나 이상의 요소를 제거 하려면이 메서드를 호출 합니다.|
|[SetAt](#setat)|배열 개체의 요소 값을 설정 하려면이 메서드를 호출 합니다.|
|[SetAtGrow](#setatgrow)|배열 개체의 요소 값을 설정 하 여 필요에 따라 배열을 확장 하는이 메서드를 호출 합니다.|
|[SetCount](#setcount)|이 메서드를 호출 하 여 배열 개체의 크기를 설정 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 &#91;&#93;](#operator_at)|배열의 요소에 대 한 참조를 반환 하려면이 연산자를 호출 합니다.|

### <a name="typedefs"></a>Typedefs

|형식 정의|Description|
|-|-|
|[INARGTYPE](#inargtype)|배열에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[OUTARGTYPE](#outargtype)|배열에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

## <a name="remarks"></a>설명

`CAtlArray` 사용자 정의 형식의 요소 배열을 만들고 관리 하는 메서드를 제공 합니다. 표준 C 배열과 유사 하지만 `CAtlArray` 개체는 필요에 따라 동적으로 축소 하 고 확장할 수 있습니다. 배열 인덱스는 항상 0 위치에서 시작 하 고, 상한을 고정 하거나, 새 요소가 추가 될 때 확장할 수 있습니다.

요소 수가 적은 배열의 경우에는 ATL 클래스 [CSimpleArray](../../atl/reference/csimplearray-class.md) 을 사용할 수 있습니다.

`CAtlArray` 는 MFC의 클래스와 밀접 하 게 관련 되어 `CArray` 있으며 serialization이 지원 되지 않는 한 mfc 프로젝트에서 작동 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="catlarrayadd"></a><a name="add"></a> CAtlArray:: Add

배열 개체에 요소를 추가 하려면이 메서드를 호출 합니다.

```cpp
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
배열에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

추가 된 요소의 인덱스를 반환 합니다.

### <a name="remarks"></a>설명

새 요소가 배열의 끝에 추가 됩니다. 요소를 제공 하지 않으면 빈 요소가 추가 됩니다. 즉, 실제 요소가 추가 된 것 처럼 배열의 크기가 증가 합니다. 작업이 실패 하는 경우 E_OUTOFMEMORY 인수를 사용 하 [여이를](debugging-and-error-reporting-global-functions.md#atlthrow) 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a> CAtlArray:: Append

한 배열의 내용을 다른 배열의 끝에 추가 하려면이 메서드를 호출 합니다.

```cpp
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>매개 변수

*aSrc*<br/>
추가할 배열입니다.

### <a name="return-value"></a>반환 값

첫 번째 추가 된 요소의 인덱스를 반환 합니다.

### <a name="remarks"></a>설명

제공 된 배열의 요소는 기존 배열의 끝에 추가 됩니다. 필요한 경우 새 요소를 수용할 수 있도록 메모리가 할당 됩니다.

배열은 동일한 형식 이어야 하며, 배열을 자체에 추가할 수 없습니다.

디버그 빌드에서는 `CAtlArray` 인수가 올바른 배열이 아니거나 *asrc* 가 동일한 개체를 참조 하는 경우에는이 아닌 어설션이 발생 합니다. 릴리스 빌드에서 잘못 된 인수로 인해 예기치 않은 동작이 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a> CAtlArray::AssertValid

배열 개체가 유효한 지 확인 하려면이 메서드를 호출 합니다.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>설명

배열 개체가 유효 하지 않은 경우에는이 어설션이 throw 됩니다. 이 메서드는 _DEBUG 정의 된 경우에만 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a> CAtlArray::CAtlArray

생성자입니다.

```cpp
CAtlArray() throw();
```

### <a name="remarks"></a>설명

배열 개체를 초기화 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a> CAtlArray:: ~ CAtlArray

소멸자입니다.

```cpp
~CAtlArray() throw();
```

### <a name="remarks"></a>설명

배열 개체에서 사용 하는 모든 리소스를 해제 합니다.

## <a name="catlarraycopy"></a><a name="copy"></a> CAtlArray:: Copy

한 배열의 요소를 다른 배열의 요소에 복사 하려면이 메서드를 호출 합니다.

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>매개 변수

*aSrc*<br/>
배열에 복사할 요소의 소스입니다.

### <a name="remarks"></a>설명

한 배열의 요소를 다른 배열의 요소로 덮어쓰려면이 메서드를 호출 합니다. 필요한 경우 새 요소를 수용할 수 있도록 메모리가 할당 됩니다. 배열의 요소를 자신에 게 복사할 수는 없습니다.

배열의 기존 내용을 유지 하려면 [CAtlArray:: Append](#append) 를 대신 사용 합니다.

디버그 빌드에서는 기존 `CAtlArray` 개체가 유효 하지 않거나 *asrc* 가 동일한 개체를 참조 하는 경우에는 해당 어설션이 발생 합니다. 릴리스 빌드에서 잘못 된 인수로 인해 예기치 않은 동작이 발생할 수 있습니다.

> [!NOTE]
> `CAtlArray::Copy` 는 [CAutoPtr](../../atl/reference/cautoptr-class.md) 클래스를 사용 하 여 만든 요소로 구성 된 배열을 지원 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a> CAtlArray:: FreeExtra

배열에서 빈 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>설명

빈 요소는 제거 되지만 배열의 크기와 상한을 그대로 유지 합니다.

CAtlArray 개체가 유효 하지 않거나 배열의 최대 크기를 초과 하는 경우 디버그 빌드에서 어설션이 발생 합니다.

## <a name="catlarraygetat"></a><a name="getat"></a> CAtlArray:: GetAt

이 메서드를 호출 하 여 배열 개체에서 단일 요소를 검색 합니다.

```cpp
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
반환할 배열 요소의 인덱스 값입니다.

### <a name="return-value"></a>반환 값

필수 배열 요소에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

IElement가 배열에 있는 요소 수를 초과 하는 경우 디버그 빌드에서  어설션이 발생 합니다. 릴리스 빌드에서 잘못 된 인수로 인해 예기치 않은 동작이 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a> CAtlArray:: GetCount

배열에 저장 된 요소의 수를 반환 하려면이 메서드를 호출 합니다.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>반환 값

배열에 저장 된 요소의 수를 반환 합니다.

### <a name="remarks"></a>설명

배열의 첫 번째 요소가 위치 0에 있기 때문에에서 반환 되는 값은 `GetCount` 항상 가장 큰 인덱스 보다 1 큽니다.

### <a name="example"></a>예제

[CAtlArray:: GetAt](#getat)의 예제를 참조 하세요.

## <a name="catlarraygetdata"></a><a name="getdata"></a> CAtlArray:: GetData

배열의 첫 번째 요소에 대 한 포인터를 반환 하려면이 메서드를 호출 합니다.

```cpp
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>반환 값

배열의 첫 번째 요소를 저장 하는 메모리 위치에 대 한 포인터를 반환 합니다. 사용할 수 있는 요소가 없으면 NULL이 반환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a> CAtlArray:: INARGTYPE

배열에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a> CAtlArray::InsertArrayAt

한 배열을 다른 배열에 삽입 하려면이 메서드를 호출 합니다.

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>매개 변수

*iStart*<br/>
배열을 삽입할 인덱스입니다.

*paNew*<br/>
삽입할 배열입니다.

### <a name="remarks"></a>설명

*PaNew* 배열의 요소는 *istart* 요소에서 시작 하 여 배열 개체로 복사 됩니다. 기존 배열 요소를 덮어쓰지 않도록 이동 합니다.

디버그 빌드에서는 `CAtlArray` 개체가 유효 하지 않거나 *PANEW* 포인터가 NULL 이거나 잘못 된 경우에는가 없는 어설션이 발생 합니다.

> [!NOTE]
> `CAtlArray::InsertArrayAt` 는 [CAutoPtr](../../atl/reference/cautoptr-class.md) 클래스를 사용 하 여 만든 요소로 구성 된 배열을 지원 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a> CAtlArray:: InsertAt

이 메서드를 호출 하 여 새 요소 (또는 요소의 여러 복사본)를 배열 개체에 삽입 합니다.

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
요소 또는 요소를 삽입할 인덱스입니다.

*요소인*<br/>
삽입할 요소의 값입니다.

*nCount*<br/>
추가할 요소의 수입니다.

### <a name="remarks"></a>설명

인덱스 *iElement* 에서 시작 하 여 배열에 하나 이상의 요소를 삽입 합니다. 기존 요소를 덮어쓰지 않도록 이동 합니다.

디버그 빌드에서는 `CAtlArray` 개체가 유효 하지 않거나, 추가할 요소의 수가 0 이거나, 결합 된 요소의 수가 너무 커서 배열에 포함 될 수 없는 경우이 이벤트가 발생 합니다. 정품 빌드에서 잘못 된 매개 변수를 전달 하면 예기치 않은 결과가 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a> CAtlArray:: IsEmpty

배열이 비어 있는지 테스트 하려면이 메서드를 호출 합니다.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>반환 값

배열이 비어 있으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

요소를 포함 하지 않는 경우 배열이 비어 있는 것으로 간주 됩니다. 따라서 배열에 빈 요소가 포함 된 경우에도 비어 있지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a> CAtlArray:: operator []

배열의 요소에 대 한 참조를 반환 하려면이 연산자를 호출 합니다.

```cpp
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
반환할 배열 요소의 인덱스 값입니다.

### <a name="return-value"></a>반환 값

필수 배열 요소에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

[CAtlArray:: GetAt](#getat)와 유사한 함수를 수행 합니다. MFC 클래스 [CArray](../../mfc/reference/carray-class.md)와 달리이 연산자는 [CAtlArray:: setat](#setat)의 대체로 사용할 수 없습니다.

IElement가 배열에 있는 요소의 총 수를 초과 하는 경우 디버그 빌드에서  어설션이 발생 합니다. 일반 정품 빌드에서는 잘못 된 매개 변수로 인해 예기치 않은 결과가 발생할 수 있습니다.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a> CAtlArray:: OUTARGTYPE

배열에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```cpp
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a> CAtlArray:: RemoveAll

이 메서드를 호출 하 여 배열 개체에서 모든 요소를 제거 합니다.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>설명

배열 개체에서 모든 요소를 제거 합니다.

이 메서드는 [CAtlArray:: SetCount](#setcount) 를 호출 하 여 배열의 크기를 조정한 다음 할당 된 메모리를 해제 합니다.

### <a name="example"></a>예제

[CAtlArray:: IsEmpty](#isempty)의 예제를 참조 하세요.

## <a name="catlarrayremoveat"></a><a name="removeat"></a> CAtlArray:: RemoveAt

배열에서 하나 이상의 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
제거할 첫 번째 요소의 인덱스입니다.

*nCount*<br/>
제거할 요소의 수입니다.

### <a name="remarks"></a>설명

배열에서 하나 이상의 요소를 제거 합니다. 나머지 요소는 아래로 이동 됩니다. 상한을 감소 하지만 [CAtlArray:: FreeExtra](#freeextra) 를 호출할 때까지 메모리를 해제 하지 않습니다.

디버그 빌드에서는 `CAtlArray` 개체가 유효 하지 않은 경우 또는 *iElement* 의 총 합계와 *n 수가* 배열의 총 요소 수를 초과 하는 경우 관리 되지 않는 어설션이 발생 합니다. 정품 빌드에서 잘못 된 매개 변수는 예기치 않은 결과를 일으킬 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a> CAtlArray:: SetAt

배열 개체의 요소 값을 설정 하려면이 메서드를 호출 합니다.

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
설정할 배열 요소를 가리키는 인덱스입니다.

*요소인*<br/>
지정된 요소의 새 값입니다.

### <a name="remarks"></a>설명

IElement가 배열에 있는 요소 수를 초과 하는 경우 디버그 빌드에서  어설션이 발생 합니다. 정품 빌드에서 잘못 된 매개 변수를 통해 예기치 않은 결과가 발생할 수 있습니다.

### <a name="example"></a>예제

[CAtlArray:: GetAt](#getat)의 예제를 참조 하세요.

## <a name="catlarraysetcount"></a><a name="setcount"></a> CAtlArray:: SetCount

이 메서드를 호출 하 여 배열 개체의 크기를 설정 합니다.

```cpp
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>매개 변수

*nNewSize*<br/>
배열의 필요한 크기입니다.

*nGrowBy*<br/>
버퍼를 만들 크기를 결정 하는 데 사용 되는 값입니다. 값이-1 이면 내부적으로 계산 된 값이 사용 됩니다.

### <a name="return-value"></a>반환 값

배열의 크기가 성공적으로 조정 되 면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

배열의 크기를 늘리거나 줄일 수 있습니다. 증가 하면 빈 요소가 배열에 추가 됩니다. 감소 하면 인덱스가 가장 큰 요소가 삭제 되 고 메모리가 확보 됩니다.

이 메서드를 사용 하 여 배열의 크기를 설정 합니다. `SetCount`를 사용 하지 않으면 요소를 추가 하는 프로세스와 후속 메모리 할당이 수행 되 면 성능 및 조각화 메모리가 줄어듭니다.

### <a name="example"></a>예제

[CAtlArray:: GetData](#getdata)의 예제를 참조 하세요.

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a> CAtlArray::SetAtGrow

배열 개체의 요소 값을 설정 하 여 필요에 따라 배열을 확장 하는이 메서드를 호출 합니다.

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
설정할 배열 요소를 가리키는 인덱스입니다.

*요소인*<br/>
지정된 요소의 새 값입니다.

### <a name="remarks"></a>설명

인덱스에서 가리키는 요소의 값을 바꿉니다. *IElement* 가 배열의 현재 크기 보다 크면 [CAtlArray:: setcount](#setcount)호출을 사용 하 여 배열이 자동으로 증가 합니다. 디버그 빌드에서는 개체가 유효 하지 않은 경우에는가 없는 어설션이 발생 `CAtlArray` 합니다. 정품 빌드에서 잘못 된 매개 변수는 예기치 않은 결과를 일으킬 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>참고 항목

[MMXSwarm 샘플](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer 샘플](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 샘플](../../overview/visual-cpp-samples.md)<br/>
[Marquee 샘플](../../overview/visual-cpp-samples.md)<br/>
[CArray 클래스](../../mfc/reference/carray-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

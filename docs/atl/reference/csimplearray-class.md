---
description: '자세히 알아보기: CSimpleArray 클래스'
title: CSimpleArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: 95750662587c7ab47500a338c3ecd7e74a92eb34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140792"
---
# <a name="csimplearray-class"></a>CSimpleArray 클래스

이 클래스는 간단한 배열을 관리 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
배열에 저장할 데이터의 형식입니다.

*Te Al*<br/>
*T* 형식의 요소에 대 한 같음 테스트를 정의 하는 특성 개체입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|단순 배열에 대 한 생성자입니다.|
|[CSimpleArray:: ~ CSimpleArray](#dtor)|단순 배열의 소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleArray:: Add](#add)|배열에 새 요소를 추가 합니다.|
|[CSimpleArray:: Find](#find)|배열에서 요소를 찾습니다.|
|[CSimpleArray:: GetData](#getdata)|배열에 저장 된 데이터에 대 한 포인터를 반환 합니다.|
|[CSimpleArray:: GetSize](#getsize)|배열에 저장 된 요소의 수를 반환 합니다.|
|[CSimpleArray:: Remove](#remove)|배열에서 지정 된 요소를 제거 합니다.|
|[CSimpleArray:: RemoveAll](#removeall)|배열에서 요소를 모두 제거 합니다.|
|[CSimpleArray:: RemoveAt](#removeat)|배열에서 지정 된 요소를 제거 합니다.|
|[CSimpleArray::SetAtIndex](#setatindex)|배열에서 지정 된 요소를 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|배열에서 요소를 검색합니다.|
|[CSimpleArray:: operator =](#operator_eq)|대입 연산자입니다.|

## <a name="remarks"></a>설명

`CSimpleArray` 지정 된 형식의 단순 배열을 만들고 관리 하는 메서드를 제공 `T` 합니다.

매개 변수는 `TEqual` 형식의 두 요소에 대해 같음 함수를 정의 하는 방법을 제공 합니다 `T` . [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)와 유사한 클래스를 만들면 지정 된 배열에 대 한 같음 테스트의 동작을 변경할 수 있습니다. 예를 들어 포인터의 배열을 처리할 때 포인터가 참조 하는 값에 따라 같음을 정의 하는 것이 유용할 수 있습니다. 기본 구현에서는 **operator = ()** 를 활용 합니다.

`CSimpleArray`및 [csimplemap](../../atl/reference/csimplemap-class.md) 모두 적은 수의 요소를 위해 설계 되었습니다. 배열에 많은 수의 요소가 포함 된 경우 [CAtlArray](../../atl/reference/catlarray-class.md) 및 [catlmap](../../atl/reference/catlmap-class.md) 을 사용 해야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a> CSimpleArray:: Add

배열에 새 요소를 추가 합니다.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>매개 변수

*t*<br/>
배열에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

요소가 배열에 성공적으로 추가 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a> CSimpleArray::CSimpleArray

배열 개체에 대 한 생성자입니다.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>매개 변수

*src*<br/>
기존 `CSimpleArray` 개체입니다.

### <a name="remarks"></a>설명

데이터 멤버를 초기화 하 여 비어 있는 새 `CSimpleArray` 개체를 만들거나 기존 개체의 복사본을 만듭니다 `CSimpleArray` .

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a> CSimpleArray:: ~ CSimpleArray

소멸자입니다.

```
~CSimpleArray();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="csimplearrayfind"></a><a name="find"></a> CSimpleArray:: Find

배열에서 요소를 찾습니다.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>매개 변수

*t*<br/>
검색할 요소입니다.

### <a name="return-value"></a>반환 값

찾은 요소의 인덱스를 반환 하거나, 요소를 찾을 수 없는 경우-1을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a> CSimpleArray:: GetData

배열에 저장 된 데이터에 대 한 포인터를 반환 합니다.

```
T* GetData() const;
```

### <a name="return-value"></a>반환 값

배열의 데이터에 대 한 포인터를 반환 합니다.

## <a name="csimplearraygetsize"></a><a name="getsize"></a> CSimpleArray:: GetSize

배열에 저장 된 요소의 수를 반환 합니다.

```
int GetSize() const;
```

### <a name="return-value"></a>반환 값

배열에 저장 된 요소의 수를 반환 합니다.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a> CSimpleArray:: operator \[\]

배열에서 요소를 검색합니다.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
요소 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 에서 참조 하는 배열의 요소를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a> CSimpleArray:: operator =

대입 연산자입니다.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>매개 변수

*src*<br/>
복사할 배열입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체에 대 한 포인터를 반환 `CSimpleArray` 합니다.

### <a name="remarks"></a>설명

Src에서 참조 하는 개체의 모든 요소를 `CSimpleArray` 현재 배열 개체로 복사 하 여  모든 기존 데이터를 바꿉니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a> CSimpleArray:: Remove

배열에서 지정 된 요소를 제거 합니다.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>매개 변수

*t*<br/>
배열에서 제거할 요소입니다.

### <a name="return-value"></a>반환 값

요소를 찾아서 제거 하면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

요소가 제거 되 면 배열의 나머지 요소가 빈 공간을 채우도록 다시 매겨집니다.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a> CSimpleArray:: RemoveAll

배열에서 요소를 모두 제거 합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

배열에 현재 저장 되어 있는 모든 요소를 제거 합니다.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a> CSimpleArray:: RemoveAt

배열에서 지정 된 요소를 제거 합니다.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
제거할 요소를 가리키는 인덱스입니다.

### <a name="return-value"></a>반환 값

요소가 제거 되었으면 TRUE를 반환 하 고, 인덱스가 유효 하지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

요소가 제거 되 면 배열의 나머지 요소가 빈 공간을 채우도록 다시 매겨집니다.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a> CSimpleArray::SetAtIndex

배열에서 지정 된 요소를 설정 합니다.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
변경할 요소의 인덱스입니다.

*t*<br/>
지정된 요소에 할당할 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 인덱스가 유효 하지 않으면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

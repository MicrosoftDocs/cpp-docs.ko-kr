---
description: '자세히 알아보기: CTypedPtrArray 클래스'
title: CTypedPtrArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: 07d254072a51a56759a3dbe569c36ff65d199cfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345006"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray 클래스

`CPtrArray` 또는 `CObArray`클래스의 개체에 대해 형식 안전 "래퍼"를 제공합니다.

## <a name="syntax"></a>구문

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
형식화 된 포인터 배열 클래스의 기본 클래스입니다. 는 배열 클래스 ( `CObArray` 또는) 여야 합니다 `CPtrArray` .

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTypedPtrArray:: Add](#add)|배열의 끝에 새 요소를 추가 합니다. 필요한 경우 배열 증가|
|[CTypedPtrArray:: Append](#append)|한 배열의 내용을 다른 배열의 끝에 추가 합니다. 필요한 경우 배열 증가|
|[CTypedPtrArray:: Copy](#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CTypedPtrArray:: ElementAt](#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|
|[CTypedPtrArray:: GetAt](#getat)|지정된 인덱스의 값을 반환합니다.|
|[CTypedPtrArray:: InsertAt](#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CTypedPtrArray:: SetAt](#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CTypedPtrArray:: SetAtGrow](#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CTypedPtrArray:: operator \[\]](#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

`CTypedPtrArray`또는 대신를 사용 하 `CPtrArray` 는 경우 `CObArray` c + + 형식 검사 기능은 일치 하지 않는 포인터 형식으로 인 한 오류를 제거 하는 데 도움이 됩니다.

또한 `CTypedPtrArray` 래퍼는 또는를 사용 하는 경우 필요한 대부분의 캐스팅을 수행 합니다 `CObArray` `CPtrArray` .

모든 `CTypedPtrArray` 함수가 인라인 이므로이 템플릿을 사용 하면 코드의 크기나 속도가 크게 영향을 받지 않습니다.

사용에 대 한 자세한 내용은 `CTypedPtrArray` 문서 [컬렉션](../../mfc/collections.md) 및 [템플릿 기반 클래스](../../mfc/template-based-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a> CTypedPtrArray:: Add

이 멤버 함수는 `BASE_CLASS` **:: Add** 를 호출 합니다.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열에 추가할 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
이 배열에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

추가 된 요소의 인덱스입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: Add](../../mfc/reference/cobarray-class.md#add)를 참조 하세요.

## <a name="ctypedptrarrayappend"></a><a name="append"></a> CTypedPtrArray:: Append

이 멤버 함수는 `BASE_CLASS` :: Append * *를 호출 합니다.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
형식화 된 포인터 배열 클래스의 기본 클래스입니다. 는 배열 클래스 ( [CObArray](../../mfc/reference/cobarray-class.md) 또는 [cptrarray](../../mfc/reference/cptrarray-class.md)) 여야 합니다.

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

*src*<br/>
배열에 추가할 요소의 원본입니다.

### <a name="return-value"></a>반환 값

추가 된 첫 번째 요소의 인덱스입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: Append](../../mfc/reference/cobarray-class.md#append)를 참조 하세요.

## <a name="ctypedptrarraycopy"></a><a name="copy"></a> CTypedPtrArray:: Copy

이 멤버 함수는 `BASE_CLASS` **:: Copy** 를 호출 합니다.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
형식화 된 포인터 배열 클래스의 기본 클래스입니다. 는 배열 클래스 ( [CObArray](../../mfc/reference/cobarray-class.md) 또는 [cptrarray](../../mfc/reference/cptrarray-class.md)) 여야 합니다.

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

*src*<br/>
배열에 복사할 요소의 원본입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy)를 참조 하세요.

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a> CTypedPtrArray:: ElementAt

이 인라인 함수는 `BASE_CLASS` **:: elementat** 를 호출 합니다.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
이 배열에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*nIndex*<br/>
0 보다 크거나 같고 `BASE_CLASS` **:: system.array.getupperbound** 에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 위치에 있는 요소에 대 한 임시 참조입니다. 이 요소는 템플릿 매개 변수 *형식* 으로 지정 된 유형입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat)을 참조 하세요.

## <a name="ctypedptrarraygetat"></a><a name="getat"></a> CTypedPtrArray:: GetAt

이 인라인 함수는 `BASE_CLASS` **:: GetAt** 를 호출 합니다.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*nIndex*<br/>
0 보다 크거나 같고 `BASE_CLASS` **:: system.array.getupperbound** 에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 위치에 있는 요소의 복사본입니다. 이 요소는 템플릿 매개 변수 *형식* 으로 지정 된 유형입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: GetAt](../../mfc/reference/cobarray-class.md#getat) 를 참조 하세요.

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a> CTypedPtrArray:: InsertAt

이 멤버 함수는 `BASE_CLASS` **:: insertat** 를 호출 합니다.

```cpp
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
[CObArray:: system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다.

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

*newElement*<br/>
이 배열에 배치할 개체 포인터입니다. **NULL** 값의 *newelement* 를 사용할 수 있습니다.

*nCount*<br/>
이 요소를 삽입 해야 하는 횟수입니다. 기본값은 1입니다.

*nStartIndex*<br/>
에서 반환 된 값 보다 클 수 있는 정수 인덱스입니다 `CObArray::GetUpperBound` .

*BASE_CLASS*<br/>
형식화 된 포인터 배열 클래스의 기본 클래스입니다. 는 배열 클래스 ( [CObArray](../../mfc/reference/cobarray-class.md) 또는 [cptrarray](../../mfc/reference/cptrarray-class.md)) 여야 합니다.

*pNewArray*<br/>
이 배열에 추가할 요소를 포함 하는 다른 배열입니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat)을 참조 하세요.

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a> CTypedPtrArray:: operator []

이러한 인라인 연산자는: `BASE_CLASS` **: operator []** 를 호출 합니다.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
배열에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*nIndex*<br/>
0 보다 크거나 같고 `BASE_CLASS` **:: system.array.getupperbound** 에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

### <a name="remarks"></a>설명

이 아닌 배열에 대해 호출 되는 첫 번째 연산자는 **`const`** 할당 문의 오른쪽 (r-값) 이나 왼쪽 (l-value)에서 사용할 수 있습니다. 배열에 대해 호출 되는 두 번째는 **`const`** 오른쪽에만 사용할 수 있습니다.

라이브러리의 디버그 버전은 대입문 (대입문의 왼쪽 또는 오른쪽)이 범위를 벗어난 경우 어설션 합니다.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a> CTypedPtrArray:: SetAt

이 멤버 함수는 `BASE_CLASS` **:: setat** 를 호출 합니다.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같고 [CObArray:: system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)에서 반환 된 값 보다 작거나 같은 정수 인덱스입니다.

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

*ptr*<br/>
N 인덱스의 배열에 삽입할 요소에 대 한 포인터입니다. NULL 값을 사용할 수 있습니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)을 참조 하세요.

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a> CTypedPtrArray:: SetAtGrow

이 멤버 함수는 `BASE_CLASS` **:: SetAtGrow** 를 호출 합니다.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0 보다 크거나 같은 정수 인덱스입니다.

*TYPE*<br/>
기본 클래스 배열에 저장 된 요소의 형식입니다.

*newElement*<br/>
이 배열에 추가할 개체 포인터입니다. **NULL** 값을 사용할 수 있습니다.

### <a name="remarks"></a>설명

자세한 내용은 [CObArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 클래스](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 클래스](../../mfc/reference/cobarray-class.md)

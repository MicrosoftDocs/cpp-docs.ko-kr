---
description: '자세히 알아보기: CStringArray 클래스'
title: CStringArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: 7f9f8579545d79eaeaf2db9616a34040b4d8e038
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318613"
---
# <a name="cstringarray-class"></a>CStringArray 클래스

[CString](../../atl-mfc-shared/using-cstring.md) 개체의 배열을 지원 합니다.

## <a name="syntax"></a>구문

```
class CStringArray : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CStringArray` [CObArray](../../mfc/reference/cobarray-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CObArray` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`반환 값으로 포인터가 표시 되는 경우에는 cstring 포인터가 아닌 [cstring](../../atl-mfc-shared/using-cstring.md) 개체를 대체 [](../../atl-mfc-shared/using-cstring.md) 합니다. `CObject` 포인터가 함수 매개 변수로 사용될 때마다 `LPCTSTR`을 대체합니다.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

예를 들어 위의 코드는

`CString CStringArray::GetAt( int <nIndex> ) const;`

및

`void SetAt( int <nIndex>, CObject* <newElement> )`

위의 코드는 다음과 같이 변환됩니다.

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStringArray::CStringArray](../../mfc/reference/cobarray-class.md#cobarray)|빈 배열을 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStringArray:: Add](../../mfc/reference/cobarray-class.md#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CStringArray:: Append](../../mfc/reference/cobarray-class.md#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|
|[CStringArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CStringArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|
|[CStringArray:: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CStringArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|지정된 인덱스의 값을 반환합니다.|
|[CStringArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CStringArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|배열의 요소에 대한 액세스를 허용합니다. **NULL** 일 수 있습니다.|
|[CStringArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CStringArray:: System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[CStringArray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CStringArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|배열이 비어 있는지를 확인합니다.|
|[CStringArray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|이 배열의 모든 요소를 반환합니다.|
|[CStringArray:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|특정 인덱스의 요소를 제거합니다.|
|[CStringArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CStringArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CStringArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CStringArray:: operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

`CStringArray` 는 IMPLEMENT_SERIAL 매크로를 통합 하 여 요소의 serialization 및 덤프를 지원 합니다. 오버로드된 삽입 연산자 또는 `CString` 멤버 함수를 사용하여 `Serialize` 개체 배열을 보관 파일에 저장하는 경우에는 각 요소가 차례로 serialize됩니다.

> [!NOTE]
> 배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

배열에 개별 문자열 요소의 덤프가 필요하면 덤프 컨텍스트의 수준을 1 이상으로 설정해야 합니다.

`CString` 배열을 삭제하거나 해당 요소를 제거하면 문자열 메모리가 적절하게 해제됩니다.

사용에 대 한 자세한 내용은 `CStringArray` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

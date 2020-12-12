---
description: '자세한 정보: CUIntArray 클래스'
title: CUIntArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 1d316d349f4fd0457e1e66b275a213fe69b2c5ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318496"
---
# <a name="cuintarray-class"></a>CUIntArray 클래스

부호 없는 정수의 배열을 지원합니다.

## <a name="syntax"></a>구문

```
class CUIntArray : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CUIntArray` [CObArray](../../mfc/reference/cobarray-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CObArray` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터는 함수 매개 변수 또는 반환 값으로 표시 될 때마다 UINT를 대체 합니다.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

예를 들어 위의 코드는

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CUIntArray:: CUIntArray](../../mfc/reference/cobarray-class.md#cobarray)|빈 배열을 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CUIntArray:: Add](../../mfc/reference/cobarray-class.md#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CUIntArray:: Append](../../mfc/reference/cobarray-class.md#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|
|[CUIntArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[, 다음 위치에 있습니다.](../../mfc/reference/cobarray-class.md#elementat)|배열 내의 요소 포인터에 대한 임시 참조를 반환합니다.|
|[CUIntArray:: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CUIntArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|지정된 인덱스의 값을 반환합니다.|
|[CUIntArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CUIntArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|배열의 요소에 대한 액세스를 허용합니다. NULL일 수 있습니다.|
|[CUIntArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CUIntArray:: System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[비동기 배열:: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CUIntArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|배열이 비어 있는지를 확인합니다.|
|[CUIntArray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|이 배열의 모든 요소를 반환합니다.|
|[비동기 배열:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|특정 인덱스의 요소를 제거합니다.|
|[, CUIntArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CUIntArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CUIntArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CUIntArray:: operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

부호 없는 정수 또는 UINT는 대상 운영 환경에 따라 UINT의 물리적 크기가 변경 될 수 있다는 점에서 단어와 더블 워드와 다릅니다. UINT는 더블 워드와 크기가 같습니다.

`CUIntArray`[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) 매크로를 통합 하 여 런타임 형식 액세스를 지원 하 고 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 개체를 덤프 합니다. 부호 없는 개별 정수 요소의 덤프가 필요한 경우 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다. 부호 없는 정수 배열은 serialize 할 수 없습니다.

> [!NOTE]
> 배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

사용에 대 한 자세한 내용은 `CUIntArray` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

---
title: CByteArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352395"
---
# <a name="cbytearray-class"></a>CByteArray 클래스

바이트의 동적 배열을 지원합니다.

## <a name="syntax"></a>구문

```
class CByteArray : public CObject
```

## <a name="members"></a>멤버

의 `CByteArray` 멤버 함수는 [클래스 CObArray의](../../mfc/reference/cobarray-class.md)멤버 함수와 유사합니다. 이처럼 두 함수가 비슷하므로 `CObArray` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. 포인터를 `CObject` 함수 매개 변수 또는 반환 값으로 볼 때마다 BYTE를 대체합니다.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

예를 들어 위의 코드는

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|빈 배열을 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CByteArray::추가](../../mfc/reference/cobarray-class.md#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CByteArray::부속](../../mfc/reference/cobarray-class.md#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|
|[CByteArray::복사](../../mfc/reference/cobarray-class.md#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CByteArray::엘리먼트At](../../mfc/reference/cobarray-class.md#elementat)|배열 내의 바이트에 대한 임시 참조를 반환합니다.|
|[CByteArray::프리 엑스트라](../../mfc/reference/cobarray-class.md#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|지정된 인덱스의 값을 반환합니다.|
|[CByteArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CByteArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|배열의 요소에 대한 액세스를 허용합니다. NULL일 수 있습니다.|
|[CByteArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CByteArray::GetUpper바운드](../../mfc/reference/cobarray-class.md#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[CByteArray::삽입](../../mfc/reference/cobarray-class.md#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CByteArray::비어 있음](../../mfc/reference/cobarray-class.md#isempty)|배열이 비어 있는지를 확인합니다.|
|[CByteArray::제거모두](../../mfc/reference/cobarray-class.md#removeall)|이 배열의 모든 요소를 반환합니다.|
|[CByteArray::제거](../../mfc/reference/cobarray-class.md#removeat)|특정 인덱스의 요소를 제거합니다.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CByteArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|속성|Description|
|----------|-----------------|
|[CByteArray::연산자 \[\]](../../mfc/reference/cobarray-class.md#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

`CByteArray`IMPLEMENT_SERIAL 매크로를 통합하여 해당 요소의 직렬화 및 덤프를 지원합니다. 바이트 배열이 오버로드된 삽입() 연산자 또는 **<<** `Serialize` 멤버 함수를 사용하여 아카이브에 저장되는 경우 각 요소는 차례로 직렬화됩니다.

> [!NOTE]
> 배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

배열의 개별 요소에서 디버그 출력이 필요한 경우 개체의 `CDumpContext` 깊이를 1 이상으로 설정해야 합니다.

사용에 `CByteArray`대한 자세한 내용은 [컬렉션](../../mfc/collections.md)문서를 참조하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObArray 클래스](../../mfc/reference/cobarray-class.md)

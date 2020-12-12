---
description: '자세히 알아보기: CMapPtrToPtr 클래스'
title: CMapPtrToPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: 3cc561f7420e9c3c7bc2b2f6460536a80d7ef7cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259541"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr 클래스

void 포인터로 키가 지정된 void 포인터 맵을 지원합니다.

## <a name="syntax"></a>구문

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CMapPtrToPtr` [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CMapStringToOb` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터는 함수 매개 변수 또는 반환 값으로 표시 될 때마다 포인터로 대체 **`void`** 합니다. `CString`또는 **`const`** 포인터가 **`char`** 함수 매개 변수 또는 반환 값으로 표시 되는 경우 포인터를로 대체 **`void`** 합니다.

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

예를 들어 위의 코드는

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapPtrToPtr::CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapPtrToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMapPtrToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|해시 테이블의 현재 요소 수를 확인 합니다.|
|[CMapPtrToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMapPtrToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMapPtrToPtr:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapPtrToPtr:: HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|지정 된 키의 해시 값을 계산 합니다.|
|[CMapPtrToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|해시 테이블을 초기화 합니다.|
|[CMapPtrToPtr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMapPtrToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void 포인터 키에 기반 하 여 void 포인터를 조회 합니다. 포인터가 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapPtrToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapPtrToPtr:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMapPtrToPtr:: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapPtrToPtr:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMapPtrToPtr:: operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

`CMapPtrToPtr` IMPLEMENT_DYNAMIC 매크로를 통합 하 여 런타임 형식 액세스를 지원 하 고 개체를 덤프 `CDumpContext` 합니다. 개별 지도 요소 (포인터 값)의 덤프가 필요한 경우 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

포인터 포인터 맵은 serialize 할 수 없습니다.

`CMapPtrToPtr` 개체를 삭제하거나 해당 요소를 제거할 경우 참조하는 엔터티가 아니라 포인터만 제거됩니다.

에 대 한 자세한 내용은 `CMapPtrToPtr` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

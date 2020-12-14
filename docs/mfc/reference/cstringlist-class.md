---
description: '자세히 알아보기: CStringList 클래스'
title: CStringList 클래스
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: c9043ef648f50e880f3b5946c1912deca3de6714
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345071"
---
# <a name="cstringlist-class"></a>CStringList 클래스

`CString` 개체 목록을 지원합니다.

## <a name="syntax"></a>구문

```
class CStringList : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CStringList` [CObList](../../mfc/reference/coblist-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CObList` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터가 반환 값으로 표시 되는 경우에는 `CString` (포인터가 아님)로 대체 `CString` 합니다. `CObject`포인터가 함수 매개 변수로 표시 되는 경우를 대체 `LPCTSTR` 합니다.

`CObject*& CObList::GetHead() const;`

예를 들어 위의 코드는

`CString& CStringList::GetHead() const;`

및

`POSITION AddHead( CObject* <newElement> );`

위의 코드는 다음과 같이 변환됩니다.

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStringList::CStringList](../../mfc/reference/coblist-class.md#coblist)|빈 목록을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStringList:: AddHead](../../mfc/reference/coblist-class.md#addhead)|요소 (또는 다른 목록의 모든 요소)를 목록의 헤드에 추가 합니다 (새 헤드를 만듭니다).|
|[CStringList:: AddTail](../../mfc/reference/coblist-class.md#addtail)|요소 (또는 다른 목록의 모든 요소)를 목록 끝에 추가 합니다 (새 꼬리를 만듭니다).|
|[CStringList:: Find](../../mfc/reference/coblist-class.md#find)|포인터 값으로 지정 된 요소의 위치를 가져옵니다.|
|[CStringList:: FindIndex](../../mfc/reference/coblist-class.md#findindex)|0부터 시작 하는 인덱스로 지정 된 요소의 위치를 가져옵니다.|
|[CStringList:: GetAt](../../mfc/reference/coblist-class.md#getat)|지정 된 위치에 있는 요소를 가져옵니다.|
|[CStringList:: GetCount](../../mfc/reference/coblist-class.md#getcount)|이 목록에 있는 요소의 수를 반환 합니다.|
|[CStringList::GetHead](../../mfc/reference/coblist-class.md#gethead)|목록의 head 요소를 반환 합니다 (비워 둘 수 없음).|
|[CStringList:: Geadposition](../../mfc/reference/coblist-class.md#getheadposition)|목록에서 head 요소의 위치를 반환 합니다.|
|[CStringList:: GetNext](../../mfc/reference/coblist-class.md#getnext)|반복할 다음 요소를 가져옵니다.|
|[CStringList:: GetPrev](../../mfc/reference/coblist-class.md#getprev)|반복을 위한 이전 요소를 가져옵니다.|
|[CStringList:: GetSize](../../mfc/reference/coblist-class.md#getsize)|이 목록에 있는 요소의 수를 반환 합니다.|
|[CStringList:: GetTail](../../mfc/reference/coblist-class.md#gettail)|목록의 tail 요소를 반환 합니다 (비워 둘 수 없음).|
|[CStringList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|목록에서 tail 요소의 위치를 반환 합니다.|
|[CStringList:: InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|지정 된 위치 뒤에 새 요소를 삽입 합니다.|
|[CStringList:: InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|지정 된 위치 앞에 새 요소를 삽입 합니다.|
|[CStringList:: IsEmpty](../../mfc/reference/coblist-class.md#isempty)|빈 목록 조건 (요소 없음)을 테스트 합니다.|
|[CStringList:: RemoveAll](../../mfc/reference/coblist-class.md#removeall)|이 목록에서 모든 요소를 제거 합니다.|
|[CStringList:: RemoveAt](../../mfc/reference/coblist-class.md#removeat)|이 목록에서 위치로 지정 된 요소를 제거 합니다.|
|[CStringList:: RemoveHead](../../mfc/reference/coblist-class.md#removehead)|목록에서 요소를 제거 합니다.|
|[CStringList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|목록의 끝에서 요소를 제거 합니다.|
|[CStringList:: SetAt](../../mfc/reference/coblist-class.md#setat)|지정 된 위치에 요소를 설정 합니다.|

## <a name="remarks"></a>설명

모든 비교는 값으로 수행 됩니다. 즉, 문자열의 문자는 문자열의 주소 대신 비교 됩니다.

`CStringList` 는 IMPLEMENT_SERIAL 매크로를 통합 하 여 요소의 serialization 및 덤프를 지원 합니다. `CString`오버 로드 된 삽입 연산자나 멤버 함수를 사용 하 여 개체 목록을 보관에 저장 하면 `Serialize` 각 `CString` 요소가 차례로 직렬화 됩니다.

개별 요소의 덤프가 필요한 경우 `CString` 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

사용에 대 한 자세한 내용은 `CStringList` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

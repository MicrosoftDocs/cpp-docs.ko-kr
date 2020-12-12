---
description: '자세히 알아보기: CList 클래스'
title: CList 클래스
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: e216bda53c37c325ffb8aeb943d4cefb223ac1d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236687"
---
# <a name="clist-class"></a>CList 클래스

순차적으로 또는 값별로 액세스할 수 있고 고유하지 않은 개체의 순서가 지정된 목록을 지원합니다.

## <a name="syntax"></a>구문

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CList:: CList](#clist)|순서가 지정 된 빈 목록을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CList:: AddHead](#addhead)|요소 (또는 다른 목록의 모든 요소)를 목록의 헤드에 추가 합니다 (새 헤드를 만듭니다).|
|[CList:: AddTail](#addtail)|요소 (또는 다른 목록의 모든 요소)를 목록 끝에 추가 합니다 (새 꼬리를 만듭니다).|
|[CList:: Find](#find)|포인터 값으로 지정 된 요소의 위치를 가져옵니다.|
|[CList:: FindIndex](#findindex)|0부터 시작 하는 인덱스로 지정 된 요소의 위치를 가져옵니다.|
|[CList:: GetAt](#getat)|지정 된 위치에 있는 요소를 가져옵니다.|
|[CList:: GetCount](#getcount)|이 목록에 있는 요소의 수를 반환 합니다.|
|[CList:: GetHead](#gethead)|목록의 head 요소를 반환 합니다 (비워 둘 수 없음).|
|[CList:: Geadposition](#getheadposition)|목록에서 head 요소의 위치를 반환 합니다.|
|[CList:: GetNext](#getnext)|반복할 다음 요소를 가져옵니다.|
|[CList:: GetPrev](#getprev)|반복을 위한 이전 요소를 가져옵니다.|
|[CList:: GetSize](#getsize)|이 목록에 있는 요소의 수를 반환 합니다.|
|[CList:: GetTail](#gettail)|목록의 tail 요소를 반환 합니다 (비워 둘 수 없음).|
|[CList:: GetTailPosition](#gettailposition)|목록에서 tail 요소의 위치를 반환 합니다.|
|[CList:: InsertAfter](#insertafter)|지정 된 위치 뒤에 새 요소를 삽입 합니다.|
|[CList::InsertBefore](#insertbefore)|지정 된 위치 앞에 새 요소를 삽입 합니다.|
|[CList:: IsEmpty](#isempty)|빈 목록 조건 (요소 없음)을 테스트 합니다.|
|[CList:: RemoveAll](#removeall)|이 목록에서 모든 요소를 제거 합니다.|
|[CList:: RemoveAt](#removeat)|이 목록에서 위치로 지정 된 요소를 제거 합니다.|
|[CList:: RemoveHead](#removehead)|목록에서 요소를 제거 합니다.|
|[CList:: RemoveTail](#removetail)|목록의 끝에서 요소를 제거 합니다.|
|[CList:: SetAt](#setat)|지정 된 위치에 요소를 설정 합니다.|

#### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 개체의 유형입니다.

*ARG_TYPE*<br/>
목록에 저장 된 개체를 참조 하는 데 사용 되는 형식입니다. 참조일 수 있습니다.

## <a name="remarks"></a>설명

`CList` 목록은 이중 연결 목록 처럼 동작 합니다.

POSITION 형식의 변수는 목록의 키입니다. 위치 변수를 반복기로 사용 하 여 목록을 순차적으로 이동 하 고 책갈피를 사용 하 여 위치를 유지할 수 있습니다. 그러나 위치는 인덱스와 동일 하지 않습니다.

요소 삽입은 목록 헤드, 꼬리 및 알려진 위치에서 매우 빠릅니다. 순차 검색은 값 또는 인덱스를 기준으로 요소를 조회 하는 데 필요 합니다. 목록이 길면이 검색 속도가 느릴 수 있습니다.

목록에서 개별 요소의 덤프가 필요한 경우 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

이 클래스의 특정 멤버 함수는 대부분의 클래스 사용에 대해 사용자 지정 해야 하는 전역 도우미 함수를 호출 합니다 `CList` . "매크로 및 전역" 섹션의 [컬렉션 클래스 도우미](../../mfc/reference/collection-class-helpers.md) 를 참조 하세요.

사용에 대 한 자세한 내용은 `CList` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a> CList:: AddHead

이 목록의 맨 위에 새 요소나 요소 목록을 추가 합니다.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>매개 변수

*ARG_TYPE*<br/>
목록 요소의 형식을 지정하는 템플릿 매개 변수입니다(참조일 수 있음).

*newElement*<br/>
새 요소입니다.

*pNewList*<br/>
다른 목록에 대 한 포인터 `CList` 입니다. *Pnewlist* 의 요소가이 목록에 추가 됩니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 새로 삽입 된 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

작업을 수행 하기 전에 목록이 비어 있을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a> CList:: AddTail

이 목록의 꼬리에 새 요소 또는 요소 목록을 추가 합니다.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>매개 변수

*ARG_TYPE*<br/>
목록 요소의 형식을 지정하는 템플릿 매개 변수입니다(참조일 수 있음).

*newElement*<br/>
이 목록에 추가할 요소입니다.

*pNewList*<br/>
다른 목록에 대 한 포인터 `CList` 입니다. *Pnewlist* 의 요소가이 목록에 추가 됩니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 새로 삽입 된 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

작업을 수행 하기 전에 목록이 비어 있을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a> CList:: CList

순서가 지정 된 빈 목록을 생성 합니다.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
목록을 확장 하기 위한 메모리 할당 세분성입니다.

### <a name="remarks"></a>설명

목록이 커지면 메모리는 *Nblocksize* 항목의 단위로 할당 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a> CList:: Find

목록을 순차적으로 검색 하 여 지정 된 *Searchvalue* 와 일치 하는 첫 번째 요소를 찾습니다.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>매개 변수

*ARG_TYPE*<br/>
목록 요소의 형식을 지정하는 템플릿 매개 변수입니다(참조일 수 있음).

*searchValue*<br/>
목록에서 찾을 값입니다.

*startAfter*<br/>
검색의 시작 위치입니다. 값을 지정 하지 않으면 검색은 head 요소로 시작 합니다.

### <a name="return-value"></a>반환 값

반복 또는 개체 포인터 검색에 사용할 수 있는 위치 값입니다. 개체를 찾을 수 없는 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a> CList:: FindIndex

*N 인덱스* 값을 목록에 인덱스로 사용 합니다.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
찾을 목록 요소의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

반복 또는 개체 포인터 검색에 사용할 수 있는 위치 값입니다. *Nindex* 가 음수 이거나 너무 클 경우 NULL입니다.

### <a name="remarks"></a>설명

목록의 헤드에서 순차적 검색을 시작 하 고 *n* 번째 요소에서 중지 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a> CList:: GetAt

지정 된 위치에 있는 목록 요소를 가져옵니다.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 개체의 유형을 지정 하는 템플릿 매개 변수입니다.

*position*<br/>
가져올 요소의 목록 내 위치입니다.

### <a name="return-value"></a>반환 값

에 대 한 반환 값 설명을 참조 하십시오 `GetHead` .

### <a name="remarks"></a>설명

`GetAt` 지정 된 위치와 연결 된 요소 또는 요소에 대 한 참조를 반환 합니다. 인덱스와 동일 하지 않으며 위치 값에 직접 작업할 수 없습니다. POSITION 형식의 변수는 목록의 키입니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

### <a name="example"></a>예제

  [CList:: Gethe Adposition](#getheadposition)의 예제를 참조 하세요.

## <a name="clistgetcount"></a><a name="getcount"></a> CList:: GetCount

이 목록에 있는 요소의 수를 가져옵니다.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

요소 수를 포함 하는 정수 값입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하면 [CList:: GetSize](#getsize) 메서드와 동일한 결과가 생성 됩니다.

### <a name="example"></a>예제

  [CList:: RemoveHead](#removehead)의 예제를 참조 하세요.

## <a name="clistgethead"></a><a name="gethead"></a> CList:: GetHead

이 목록의 head 요소 또는 head 요소에 대 한 참조를 가져옵니다.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 개체의 유형을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

목록이 인 경우 **`const`** 목록의 맨 `GetHead` 위에 있는 요소의 복사본을 반환 합니다. 이를 통해 함수는 대입문의 오른쪽 에서만 사용 되 고 수정 되지 않도록 보호할 수 있습니다.

목록이가 아닌 경우 **`const`** `GetHead` 목록 맨 위에 있는 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `GetHead` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a> CList:: Geadposition

이 목록에 있는 head 요소의 위치를 가져옵니다.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>반환 값

반복 또는 개체 포인터 검색에 사용할 수 있는 위치 값입니다. 목록이 비어 있으면 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a> CList:: GetNext

*Rposition* 으로 식별 되는 목록 요소를 가져온 다음이 목록에 있는 다음 항목의 위치 값을 *rposition* 으로 설정 합니다.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*rPosition*<br/>
이전 `GetNext` , [geadposition](#getheadposition)또는 기타 멤버 함수 호출에서 반환 된 위치 값에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

목록이 인 경우 **`const`** `GetNext` 목록 요소의 복사본을 반환 합니다. 이를 통해 함수는 대입문의 오른쪽 에서만 사용 되 고 수정 되지 않도록 보호할 수 있습니다.

목록이이 아니면 **`const`** `GetNext` 목록의 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

`GetNext`또는에 대 한 호출을 사용 하 여 초기 위치를 설정 하는 경우 전방 반복 루프에서을 사용할 수 있습니다 `GetHeadPosition` `Find` .

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

검색 된 요소가 목록에서 마지막 이면의 새 값은 `rPosition` NULL로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a> CList:: GetPrev

로 식별 되는 목록 요소를 가져온 `rPosition` 다음 `rPosition` 를 목록에서 이전 항목의 위치 값으로 설정 합니다.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*rPosition*<br/>
이전 또는 다른 멤버 함수 호출에서 반환 된 위치 값에 대 한 참조 `GetPrev` 입니다.

### <a name="return-value"></a>반환 값

목록이 인 경우 **`const`** 목록의 맨 `GetPrev` 위에 있는 요소의 복사본을 반환 합니다. 이를 통해 함수는 대입문의 오른쪽 에서만 사용 되 고 수정 되지 않도록 보호할 수 있습니다.

목록이이 아니면 **`const`** `GetPrev` 목록의 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

또는에 대 한 호출을 사용 하 여 `GetPrev` 초기 위치를 설정 하는 경우 역방향 반복 루프에서를 사용할 수 있습니다 `GetTailPosition` `Find` .

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

검색 된 요소가 목록의 첫 번째 이면 *Rposition* 의 새 값이 NULL로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a> CList:: GetSize

목록 요소의 수를 반환 합니다.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>반환 값

목록에 있는 항목의 수입니다.

### <a name="remarks"></a>설명

목록의 요소 수를 검색 하려면이 메서드를 호출 합니다.  이 메서드를 호출 하면 [CList:: GetCount](#getcount) 메서드와 동일한 결과가 생성 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a> CList:: GetTail

`CObject`이 목록의 꼬리 요소를 나타내는 포인터를 가져옵니다.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

[GetHead](../../mfc/reference/coblist-class.md#gethead)에 대 한 반환 값 설명을 참조 하세요.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `GetTail` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](../../mfc/reference/coblist-class.md#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a> CList:: GetTailPosition

이 목록에 있는 tail 요소의 위치를 가져옵니다. 목록이 비어 있으면 NULL입니다.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>반환 값

반복 또는 개체 포인터 검색에 사용할 수 있는 위치 값입니다. 목록이 비어 있으면 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a> CList:: InsertAfter

이 목록에서 지정 된 위치에 있는 요소 뒤에 요소를 추가 합니다.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*position*<br/>
이전 `GetNext` , `GetPrev` 또는 멤버 함수 호출에서 반환 되는 위치 값 `Find` 입니다.

*ARG_TYPE*<br/>
목록 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*newElement*<br/>
이 목록에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

반복 또는 목록 요소 검색에 사용할 수 있는 POSITION 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a> CList:: InsertBefore

이 목록에서 지정된 위치의 요소 앞에 요소를 추가합니다.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*position*<br/>
이전 `GetNext` , `GetPrev` 또는 멤버 함수 호출에서 반환 되는 위치 값 `Find` 입니다.

*ARG_TYPE*<br/>
목록 요소의 형식을 지정하는 템플릿 매개 변수입니다(참조일 수 있음).

*newElement*<br/>
이 목록에 추가할 요소입니다.

### <a name="return-value"></a>반환 값

반복 또는 목록 요소 검색에 사용할 수 있는 POSITION 값입니다.

### <a name="remarks"></a>설명

*Position* 이 NULL 이면 요소가 목록의 맨 위에 삽입 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a> CList:: IsEmpty

이 목록에 요소가 없는지 여부를 나타냅니다.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

이 목록이 비어 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a> CList:: RemoveAll

이 목록에서 모든 요소를 제거 하 고 연결 된 메모리를 해제 합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

목록이 이미 비어 있으면 오류가 발생 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a> CList:: RemoveAt

이 목록에서 지정 된 요소를 제거 합니다.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>매개 변수

*position*<br/>
목록에서 제거할 요소의 위치입니다.

### <a name="remarks"></a>설명

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a> CList:: RemoveHead

목록의 맨 위에 있는 요소를 제거 하 고 해당 요소에 대 한 포인터를 반환 합니다.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

목록의 맨 앞에 있는 요소입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `RemoveHead` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a> CList:: RemoveTail

목록의 끝에서 요소를 제거 하 고 해당 요소에 대 한 포인터를 반환 합니다.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 있는 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

목록의 끝에 있는 요소입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `RemoveTail` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a> CList:: SetAt

POSITION 형식의 변수는 목록의 키입니다.

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
설정할 요소의 위치입니다.

*ARG_TYPE*<br/>
목록 요소의 형식을 지정하는 템플릿 매개 변수입니다(참조일 수 있음).

*newElement*<br/>
목록에 추가할 요소입니다.

### <a name="remarks"></a>설명

인덱스와 동일 하지 않으며 위치 값에 직접 작업할 수 없습니다. `SetAt` 목록의 지정 된 위치에 요소를 씁니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMap 클래스](../../mfc/reference/cmap-class.md)<br/>
[CArray 클래스](../../mfc/reference/carray-class.md)

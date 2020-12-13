---
description: '자세한 정보: CAtlList 클래스'
title: CAtlList 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 79ad0ab8e1a3cd1fb528776fa868aa806746b9da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147357"
---
# <a name="catllist-class"></a>CAtlList 클래스

이 클래스는 목록 개체를 만들고 관리 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>매개 변수

*E*<br/>
요소 형식입니다.

*ETraits*<br/>
요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다. 자세한 내용은 [CElementTraits 클래스](../../atl/reference/celementtraits-class.md) 를 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CAtlList:: INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlList:: CAtlList](#catllist)|생성자입니다.|
|[표시 되는 목록:: ~ Clllist](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[이상 목록:: AddHead](#addhead)|목록의 맨 위에 요소를 추가 하려면이 메서드를 호출 합니다.|
|[이상 목록:: Add헤드 목록](#addheadlist)|목록의 맨 위에 기존 목록을 추가 하려면이 메서드를 호출 합니다.|
|[가산 Llist:: AddTail](#addtail)|이 목록의 꼬리에 요소를 추가 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: AddTailList](#addtaillist)|이 메서드를 호출 하 여이 목록의 꼬리에 기존 목록을 추가 합니다.|
|[자세한 목록:: AssertValid](#assertvalid)|목록이 유효한 지 확인 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: Find](#find)|목록에서 지정 된 요소를 검색 하려면이 메서드를 호출 합니다.|
|[CAtlList:: FindIndex](#findindex)|인덱스 값이 지정 된 경우이 메서드를 호출 하 여 요소의 위치를 가져옵니다.|
|[자세한 목록:: GetAt](#getat)|목록의 지정 된 위치에 있는 요소를 반환 하려면이 메서드를 호출 합니다.|
|[CAtlList:: GetCount](#getcount)|목록에 있는 개체의 수를 반환 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: GetHead](#gethead)|목록의 맨 위에 있는 요소를 반환 하려면이 메서드를 호출 합니다.|
|[Gellist:: Geadposition](#getheadposition)|목록 헤드의 위치를 가져오려면이 메서드를 호출 합니다.|
|[자세한 목록:: GetNext](#getnext)|목록에서 다음 요소를 반환 하려면이 메서드를 호출 합니다.|
|[CAtlList:: GetPrev](#getprev)|목록에서 이전 요소를 반환 하려면이 메서드를 호출 합니다.|
|[CAtlList:: GetTail](#gettail)|목록의 끝에 있는 요소를 반환 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: GetTailPosition](#gettailposition)|목록의 꼬리 위치를 가져오려면이 메서드를 호출 합니다.|
|[자세한 목록:: InsertAfter](#insertafter)|목록에서 지정 된 위치 뒤에 새 요소를 삽입 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: InsertBefore](#insertbefore)|지정 된 위치 앞의 목록에 새 요소를 삽입 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: IsEmpty](#isempty)|목록이 비어 있는지 확인 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: MoveToHead](#movetohead)|지정 된 요소를 목록의 헤드로 이동 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: MoveToTail](#movetotail)|지정 된 요소를 목록의 꼬리 부분으로 이동 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: RemoveAll](#removeall)|목록에서 모든 요소를 제거 하려면이 메서드를 호출 합니다.|
|[CAtlList:: RemoveAt](#removeat)|목록에서 단일 요소를 제거 하려면이 메서드를 호출 합니다.|
|[CAtlList:: RemoveHead](#removehead)|목록의 맨 위에 있는 요소를 제거 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: RemoveHeadNoReturn](#removeheadnoreturn)|값을 반환 하지 않고 목록 맨 위에 있는 요소를 제거 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: RemoveTail](#removetail)|목록의 끝에 있는 요소를 제거 하려면이 메서드를 호출 합니다.|
|[자세한 목록:: RemoveTailNoReturn](#removetailnoreturn)|값을 반환 하지 않고 목록 끝에 있는 요소를 제거 하려면이 메서드를 호출 합니다.|
|[CAtlList:: SetAt](#setat)|목록의 지정 된 위치에 있는 요소의 값을 설정 하려면이 메서드를 호출 합니다.|
|[CAtlList:: SwapElements](#swapelements)|목록에서 요소를 교환 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

`CAtlList`클래스는 순차적으로 또는 값으로 액세스할 수 있는 고유 하지 않은 개체의 순서가 지정 된 목록을 지원 합니다. `CAtlList` 목록은 이중으로 연결 된 목록 처럼 동작 합니다. 각 목록에는 head와 tail이 있으며 새 요소 (또는 경우에 따라 목록)를 목록의 끝에 추가 하거나 특정 요소 앞 이나 뒤에 삽입할 수 있습니다.

대부분의 `CAtlList` 메서드는 위치 값을 사용 합니다. 이 값은 메서드가 요소를 저장 하는 실제 메모리 위치를 참조 하는 데 사용 되며 직접 계산 하거나 예측 해서는 안 됩니다. 목록에서 *n* 번째 요소에 액세스 해야 하는 경우, [다음](#findindex) 메서드는 지정 된 인덱스에 대 한 해당 위치 값을 반환 합니다. [GetNext](#getnext) 및 catllist:: [getprev](#getprev) 메서드를 사용 하 여 목록의 개체를 반복할 수 있습니다.

ATL에서 사용할 수 있는 컬렉션 클래스에 대 한 자세한 내용은 [Atl 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="catllistaddhead"></a><a name="addhead"></a> 이상 목록:: AddHead

목록의 맨 위에 요소를 추가 하려면이 메서드를 호출 합니다.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
새 요소입니다.

### <a name="return-value"></a>반환 값

새로 추가 된 요소의 위치를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 버전이 사용 되는 경우 해당 복사 생성자가 아닌 기본 생성자를 사용 하 여 빈 요소를 만듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a> 이상 목록:: Add헤드 목록

목록의 맨 위에 기존 목록을 추가 하려면이 메서드를 호출 합니다.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>매개 변수

*plNew*<br/>
추가할 목록입니다.

### <a name="remarks"></a>설명

*Plnew* 가 가리키는 목록이 기존 목록의 시작 부분에 삽입 됩니다. 디버그 빌드에서는 *Plnew* 가 NULL과 같은 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a> 가산 Llist:: AddTail

이 목록의 꼬리에 요소를 추가 하려면이 메서드를 호출 합니다.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
추가할 요소입니다.

### <a name="return-value"></a>반환 값

새로 추가 된 요소의 위치를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 버전이 사용 되는 경우 해당 복사 생성자가 아닌 기본 생성자를 사용 하 여 빈 요소를 만듭니다. 요소는 목록의 끝에 추가 되므로 이제 tail. 이 메서드는 빈 목록에 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a> 자세한 목록:: AddTailList

이 메서드를 호출 하 여이 목록의 꼬리에 기존 목록을 추가 합니다.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>매개 변수

*plNew*<br/>
추가할 목록입니다.

### <a name="remarks"></a>설명

*Plnew* 가 가리키는 목록이 목록 개체의 마지막 요소 (있는 경우) 뒤에 삽입 됩니다. 따라서 *Plnew* 목록의 마지막 요소는 tail이 됩니다. 디버그 빌드에서는 *Plnew* 가 NULL과 같은 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a> 자세한 목록:: AssertValid

목록이 유효한 지 확인 하려면이 메서드를 호출 합니다.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>설명

디버그 빌드에서는 목록 개체가 유효 하지 않을 경우 어설션 오류가 발생 합니다. 빈 목록에는 NULL을 가리키는 head와 tail이 모두 있어야 하 고 비어 있지 않은 목록에는 올바른 주소를 가리키는 head와 tail이 모두 있어야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a> CAtlList:: CAtlList

생성자입니다.

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
블록의 크기입니다.

### <a name="remarks"></a>설명

개체에 대 한 생성자 `CAtlList` 입니다. 블록 크기는 새 요소가 필요할 때 할당 된 메모리의 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a> 표시 되는 목록:: ~ Clllist

소멸자입니다.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>설명

모든 할당 된 리소스를 해제 합니다 .이를 비롯 하 여 모든 요소를 목록에서 제거 하려면 [RemoveAll::](#removeall) 에 대 한 호출을 포함 합니다.

디버그 빌드에서에 대 한 호출 후에도 목록에 일부 요소가 포함 되 면 어설션 오류가 발생 `RemoveAll` 합니다.

## <a name="catllistfind"></a><a name="find"></a> 자세한 목록:: Find

목록에서 지정 된 요소를 검색 하려면이 메서드를 호출 합니다.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
목록에서 찾을 요소입니다.

*posStartAfter*<br/>
검색의 시작 위치입니다. 값을 지정 하지 않으면 검색은 head 요소로 시작 합니다.

### <a name="return-value"></a>반환 값

요소가 있으면 요소의 위치 값을 반환 하 고, 그렇지 않으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서 목록 개체가 유효 하지 않거나 *posStartAfter* 값이 범위를 벗어난 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a> CAtlList:: FindIndex

인덱스 값이 지정 된 경우이 메서드를 호출 하 여 요소의 위치를 가져옵니다.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>매개 변수

*iElement*<br/>
필수 목록 요소의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

해당 위치 값을 반환 하거나, *iElement* 가 범위를 벗어난 경우 NULL을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 인덱스 값에 해당 하는 위치를 반환 하 여 목록의 *n* 번째 요소에 대 한 액세스를 허용 합니다.

디버그 빌드에서는 목록 개체가 유효 하지 않을 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a> 자세한 목록:: GetAt

목록의 지정 된 위치에 있는 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
특정 요소를 지정 하는 위치 값입니다.

### <a name="return-value"></a>반환 값

요소에 대 한 참조 또는의 복사본입니다.

### <a name="remarks"></a>설명

목록이 이면는 **`const`** `GetAt` 요소의 복사본을 반환 합니다. 이를 통해 메서드를 대입문의 오른쪽 에서만 사용 하 고 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이이 아니면는 **`const`** `GetAt` 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 메서드를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[Catllist:: FindIndex](#findindex)의 예제를 참조 하세요.

## <a name="catllistgetcount"></a><a name="getcount"></a> CAtlList:: GetCount

목록에 있는 개체의 수를 반환 하려면이 메서드를 호출 합니다.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>반환 값

목록에 있는 요소 수를 반환합니다.

### <a name="example"></a>예제

[Catllist:: Find](#find)의 예제를 참조 하세요.

## <a name="catllistgethead"></a><a name="gethead"></a> 자세한 목록:: GetHead

목록의 맨 위에 있는 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>반환 값

목록의 맨 위에 있는 요소의 복사본에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

목록이 인 경우 **`const`** 목록의 맨 `GetHead` 위에 있는 요소의 복사본을 반환 합니다. 이를 통해 메서드를 대입문의 오른쪽 에서만 사용 하 고 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이가 아닌 경우 **`const`** `GetHead` 목록 맨 위에 있는 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 메서드를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

디버그 빌드에서는 목록 헤드가 NULL을 가리키는 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[Catllist:: AddHead](#addhead)의 예제를 참조 하세요.

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a> Gellist:: Geadposition

목록 헤드의 위치를 가져오려면이 메서드를 호출 합니다.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>반환 값

목록 헤드의 요소에 해당 하는 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

목록이 비어 있으면 반환 되는 값은 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a> 자세한 목록:: GetNext

목록에서 다음 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
에 대 한 이전 호출에서 반환 되는 위치 값으로, `GetNext` [gellist:: Geor adposition](#getheadposition)또는 기타 `CAtlList` 메서드입니다.

### <a name="return-value"></a>반환 값

목록이 이면 목록에서 **`const`** `GetNext` 다음 요소의 복사본을 반환 합니다. 이를 통해 메서드를 대입문의 오른쪽 에서만 사용 하 고 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이이 아니면 목록에서 **`const`** `GetNext` 다음 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 메서드를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

POSITION 카운터 ( *pos*)는 목록의 다음 요소를 가리키도록 업데이트 되거나 더 이상 요소가 없는 경우 NULL입니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[Gellist:: Ge의 Adposition](#getheadposition)의 예제를 참조 하세요.

## <a name="catllistgetprev"></a><a name="getprev"></a> CAtlList:: GetPrev

목록에서 이전 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
에 대 한 이전 호출에서 반환 되는 위치 값 ( `GetPrev` [GetTailPosition](#gettailposition)) 또는 기타 `CAtlList` 메서드입니다.

### <a name="return-value"></a>반환 값

목록이 인 경우 **`const`** `GetPrev` 목록 요소의 복사본을 반환 합니다. 이를 통해 메서드를 대입문의 오른쪽 에서만 사용 하 고 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이이 아니면 **`const`** `GetPrev` 목록의 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 메서드를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

POSITION 카운터 ( *pos*)는 목록의 이전 요소를 가리키도록 업데이트 되거나 더 이상 요소가 없는 경우 NULL입니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[GetTailPosition](#gettailposition)의 예제를 참조 하세요.

## <a name="catllistgettail"></a><a name="gettail"></a> CAtlList:: GetTail

목록의 끝에 있는 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>반환 값

목록의 끝에 있는 요소 또는의 복사본에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

목록이 인 경우 **`const`** 목록의 맨 `GetTail` 위에 있는 요소의 복사본을 반환 합니다. 이를 통해 메서드를 대입문의 오른쪽 에서만 사용 하 고 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이가 아닌 경우 **`const`** `GetTail` 목록 맨 위에 있는 요소에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 메서드를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

디버그 빌드에서는 목록의 tail이 NULL을 가리키는 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[Catllist:: AddTail](#addtail)의 예제를 참조 하세요.

## <a name="catllistgettailposition"></a><a name="gettailposition"></a> 자세한 목록:: GetTailPosition

목록의 꼬리 위치를 가져오려면이 메서드를 호출 합니다.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>반환 값

목록의 끝에 있는 요소에 해당 하는 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

목록이 비어 있으면 반환 되는 값은 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a> CAtlList:: INARGTYPE

요소가 입력 인수로 전달 될 때 사용 되는 형식입니다.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a> 자세한 목록:: InsertAfter

목록에서 지정 된 위치 뒤에 새 요소를 삽입 하려면이 메서드를 호출 합니다.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
새 요소가 삽입 되는 위치 값입니다.

*요소인*<br/>
삽입할 요소입니다.

### <a name="return-value"></a>반환 값

새 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 목록이 유효 하지 않거나 삽입이 실패 한 경우 또는 꼬리 뒤에 요소를 삽입 하려고 시도 하는 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a> 자세한 목록:: InsertBefore

지정 된 위치 앞의 목록에 새 요소를 삽입 하려면이 메서드를 호출 합니다.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
새 요소는이 위치 값 앞의 목록에 삽입 됩니다.

*요소인*<br/>
삽입할 요소입니다.

### <a name="return-value"></a>반환 값

새 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 목록이 유효 하지 않거나 삽입이 실패 한 경우 또는 head 앞에 요소를 삽입 하려고 시도 하는 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a> 자세한 목록:: IsEmpty

목록이 비어 있는지 확인 하려면이 메서드를 호출 합니다.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>반환 값

목록에 개체가 포함 되어 있지 않으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a> 자세한 목록:: MoveToHead

지정 된 요소를 목록의 헤드로 이동 하려면이 메서드를 호출 합니다.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
이동할 요소의 위치 값입니다.

### <a name="remarks"></a>설명

지정 된 요소가 현재 위치에서 목록 헤드로 이동 합니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a> 자세한 목록:: MoveToTail

지정 된 요소를 목록의 꼬리 부분으로 이동 하려면이 메서드를 호출 합니다.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
이동할 요소의 위치 값입니다.

### <a name="remarks"></a>설명

지정 된 요소가 현재 위치에서 목록의 끝 부분으로 이동 합니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[MoveToHead](#movetohead)의 예제를 참조 하세요.

## <a name="catllistremoveall"></a><a name="removeall"></a> 자세한 목록:: RemoveAll

목록에서 모든 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>설명

이 메서드는 목록에서 모든 요소를 제거 하 고 할당 된 메모리를 해제 합니다. 디버그 빌드에서는 모든 요소가 삭제 되지 않거나 목록 구조가 손상 된 경우에는 해당 어설션이 발생 합니다.

### <a name="example"></a>예제

[IsEmpty](#isempty)의 예제를 참조 하세요.

## <a name="catllistremoveat"></a><a name="removeat"></a> CAtlList:: RemoveAt

목록에서 단일 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
제거할 요소의 위치 값입니다.

### <a name="remarks"></a>설명

*Pos* 에서 참조 하는 요소가 제거 되 고 메모리가 해제 됩니다. 를 사용 하 여 `RemoveAt` 목록의 헤드 또는 꼬리를 제거할 수 있습니다.

디버그 빌드에서는 목록이 유효 하지 않거나 요소를 제거 하 여 목록 구조에 속하지 않는 메모리에 액세스 하는 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a> CAtlList:: RemoveHead

목록의 맨 위에 있는 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>반환 값

목록의 맨 위에 있는 요소를 반환 합니다.

### <a name="remarks"></a>설명

헤드 요소가 목록에서 삭제 되 고 메모리가 해제 됩니다. 요소의 복사본이 반환 됩니다. 디버그 빌드에서 목록이 비어 있으면 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a> 자세한 목록:: RemoveHeadNoReturn

값을 반환 하지 않고 목록 맨 위에 있는 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>설명

헤드 요소가 목록에서 삭제 되 고 메모리가 해제 됩니다. 디버그 빌드에서 목록이 비어 있으면 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[IsEmpty](#isempty)의 예제를 참조 하세요.

## <a name="catllistremovetail"></a><a name="removetail"></a> 자세한 목록:: RemoveTail

목록의 끝에 있는 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>반환 값

목록의 끝에 있는 요소를 반환 합니다.

### <a name="remarks"></a>설명

Tail 요소가 목록에서 삭제 되 고 메모리가 해제 됩니다. 요소의 복사본이 반환 됩니다. 디버그 빌드에서 목록이 비어 있으면 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a> 자세한 목록:: RemoveTailNoReturn

값을 반환 하지 않고 목록 끝에 있는 요소를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>설명

Tail 요소가 목록에서 삭제 되 고 메모리가 해제 됩니다. 디버그 빌드에서 목록이 비어 있으면 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[IsEmpty](#isempty)의 예제를 참조 하세요.

## <a name="catllistsetat"></a><a name="setat"></a> CAtlList:: SetAt

목록의 지정 된 위치에 있는 요소의 값을 설정 하려면이 메서드를 호출 합니다.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
변경할 요소에 해당 하는 위치 값입니다.

*요소인*<br/>
새 요소 값입니다.

### <a name="remarks"></a>설명

기존 값을 *요소로* 바꿉니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a> CAtlList:: SwapElements

목록에서 요소를 교환 하려면이 메서드를 호출 합니다.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>매개 변수

*pos1*<br/>
첫 번째 위치 값입니다.

*pos2*<br/>
두 번째 위치 값입니다.

### <a name="remarks"></a>설명

지정 된 두 위치에 있는 요소를 바꿉니다. 디버그 빌드에서는 position 값이 NULL과 같은 경우 어설션 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>참고 항목

[CList 클래스](../../mfc/reference/clist-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

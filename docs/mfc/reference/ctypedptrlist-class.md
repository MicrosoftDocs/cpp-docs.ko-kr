---
description: '자세히 알아보기: CTypedPtrList 클래스'
title: CTypedPtrList 클래스
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 353e9af00b1366b260ce3cb3689018a8e4e370c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318535"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 클래스

클래스 `CPtrList`의 개체에 대한 형식 안전 "래퍼"를 제공합니다.

## <a name="syntax"></a>구문

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>매개 변수

*BASE_CLASS*<br/>
형식화 된 포인터 목록 클래스의 기본 클래스입니다. 포인터 목록 클래스 ( `CObList` 또는) 여야 합니다 `CPtrList` .

*TYPE*<br/>
기본 클래스 목록에 저장 된 요소의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTypedPtrList:: AddHead](#addhead)|요소 (또는 다른 목록의 모든 요소)를 목록의 헤드에 추가 합니다 (새 헤드를 만듭니다).|
|[CTypedPtrList:: AddTail](#addtail)|요소 (또는 다른 목록의 모든 요소)를 목록 끝에 추가 합니다 (새 꼬리를 만듭니다).|
|[CTypedPtrList:: GetAt](#getat)|지정 된 위치에 있는 요소를 가져옵니다.|
|[CTypedPtrList:: GetHead](#gethead)|목록의 head 요소를 반환 합니다 (비워 둘 수 없음).|
|[CTypedPtrList:: GetNext](#getnext)|반복할 다음 요소를 가져옵니다.|
|[CTypedPtrList:: GetPrev](#getprev)|반복을 위한 이전 요소를 가져옵니다.|
|[CTypedPtrList:: GetTail](#gettail)|목록의 tail 요소를 반환 합니다 (비워 둘 수 없음).|
|[CTypedPtrList:: RemoveHead](#removehead)|목록에서 요소를 제거 합니다.|
|[CTypedPtrList:: RemoveTail](#removetail)|목록의 끝에서 요소를 제거 합니다.|
|[CTypedPtrList:: SetAt](#setat)|지정 된 위치에 요소를 설정 합니다.|

## <a name="remarks"></a>설명

`CTypedPtrList`또는 대신를 사용 하 `CObList` 는 경우 `CPtrList` c + + 형식 검사 기능은 일치 하지 않는 포인터 형식으로 인 한 오류를 제거 하는 데 도움이 됩니다.

또한 `CTypedPtrList` 래퍼는 또는를 사용 하는 경우 필요한 대부분의 캐스팅을 수행 합니다 `CObList` `CPtrList` .

모든 `CTypedPtrList` 함수가 인라인 이므로이 템플릿을 사용 하면 코드의 크기나 속도가 크게 영향을 받지 않습니다.

에서 파생 된 목록을 `CObList` serialize 할 수 있지만에서 파생 된 목록을 serialize 할 수 `CPtrList` 없습니다.

`CTypedPtrList` 개체를 삭제하거나 해당 요소를 제거할 경우 참조하는 엔터티가 아니라 포인터만 제거됩니다.

사용에 대 한 자세한 내용은 `CTypedPtrList` 문서 [컬렉션](../../mfc/collections.md) 및 [템플릿 기반 클래스](../../mfc/template-based-classes.md)를 참조 하세요.

## <a name="example"></a>예제

이 예에서는의 인스턴스 `CTypedPtrList` 를 만들고, 개체를 하나 추가 하 고, 목록을 디스크에 serialize 한 다음 개체를 삭제 합니다.

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a> CTypedPtrList:: AddHead

이 멤버 함수는 `BASE_CLASS` **:: addhead** 를 호출 합니다.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
기본 클래스 목록에 저장 된 요소의 형식입니다.

*newElement*<br/>
이 목록에 추가할 개체 포인터입니다. NULL 값을 사용할 수 있습니다.

*BASE_CLASS*<br/>
형식화 된 포인터 목록 클래스의 기본 클래스입니다. 포인터 목록 클래스 ( [CObList](../../mfc/reference/coblist-class.md) 또는 [cptrlist](../../mfc/reference/cptrlist-class.md)) 여야 합니다.

*pNewList*<br/>
다른 [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) 개체에 대 한 포인터입니다. *Pnewlist* 의 요소가이 목록에 추가 됩니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 새로 삽입 된 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 버전은 목록의 헤드 앞에 새 요소를 추가 합니다. 두 번째 버전은 헤드 앞에 다른 요소 목록을 추가 합니다.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a> CTypedPtrList:: AddTail

이 멤버 함수는 `BASE_CLASS` **:: addtail** 을 호출 합니다.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
기본 클래스 목록에 저장 된 요소의 형식입니다.

*newElement*<br/>
이 목록에 추가할 개체 포인터입니다. NULL 값을 사용할 수 있습니다.

*BASE_CLASS*<br/>
형식화 된 포인터 목록 클래스의 기본 클래스입니다. 포인터 목록 클래스 ( [CObList](../../mfc/reference/coblist-class.md) 또는 [cptrlist](../../mfc/reference/cptrlist-class.md)) 여야 합니다.

*pNewList*<br/>
다른 [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) 개체에 대 한 포인터입니다. *Pnewlist* 의 요소가이 목록에 추가 됩니다.

### <a name="return-value"></a>반환 값

첫 번째 버전은 새로 삽입 된 요소의 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 버전은 목록의 꼬리 뒤에 새 요소를 추가 합니다. 두 번째 버전은 목록의 꼬리 뒤에 다른 요소 목록을 추가 합니다.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a> CTypedPtrList:: GetAt

POSITION 형식의 변수는 목록의 키입니다.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*position*<br/>
이전 `GetHeadPosition` 또는 멤버 함수 호출에서 반환 되는 위치 값 `Find` 입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터를 통해 목록에 액세스 하는 경우은 `const CTypedPtrList` `GetAt` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터를 반환 합니다. 이를 통해 함수를 대입문의 오른쪽에만 사용할 수 있으므로 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이 직접 또는에 대 한 포인터를 통해 액세스 되는 경우은 `CTypedPtrList` `GetAt` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

인덱스와 동일 하지 않으며 위치 값에 직접 작업할 수 없습니다. `GetAt` 지정 된 `CObject` 위치와 연결 된 포인터를 검색 합니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

이 인라인 함수는 `BASE_CLASS` **:: GetAt** 를 호출 합니다.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a> CTypedPtrList:: GetHead

이 목록의 head 요소를 나타내는 포인터를 가져옵니다.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터를 통해 목록에 액세스 하는 경우은 `const CTypedPtrList` `GetHead` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터를 반환 합니다. 이를 통해 함수를 대입문의 오른쪽에만 사용할 수 있으므로 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이 직접 또는에 대 한 포인터를 통해 액세스 되는 경우은 `CTypedPtrList` `GetHead` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `GetHead` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](../../mfc/reference/coblist-class.md#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a> CTypedPtrList:: GetNext

*Rposition* 으로 식별 되는 목록 요소를 가져온 다음이 목록에 있는 다음 항목의 위치 값을 *rposition* 으로 설정 합니다.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
이 목록에 포함 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*rPosition*<br/>
이전 `GetNext` , `GetHeadPosition` 또는 기타 멤버 함수 호출에서 반환 된 위치 값에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터를 통해 목록에 액세스 하는 경우은 `const CTypedPtrList` `GetNext` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터를 반환 합니다. 이를 통해 함수를 대입문의 오른쪽에만 사용할 수 있으므로 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이 직접 또는에 대 한 포인터를 통해 액세스 되는 경우은 `CTypedPtrList` `GetNext` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

`GetNext` `GetHeadPosition` 또는 [Cptrlist:: Find](../../mfc/reference/coblist-class.md#find)를 호출 하 여 초기 위치를 설정 하는 경우 전방 반복 루프에서을 사용할 수 있습니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

검색 된 요소가 목록에서 마지막 이면 *Rposition* 의 새 값이 NULL로 설정 됩니다.

반복 하는 동안 요소를 제거할 수 있습니다. [CObList:: RemoveAt](../../mfc/reference/coblist-class.md#removeat)의 예제를 참조 하세요.

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a> CTypedPtrList:: GetPrev

*Rposition* 으로 식별 되는 목록 요소를 가져온 다음 *rposition* 을 목록에 있는 이전 항목의 위치 값으로 설정 합니다.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
이 목록에 포함 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*rPosition*<br/>
이전 또는 다른 멤버 함수 호출에서 반환 된 위치 값에 대 한 참조 `GetPrev` 입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터를 통해 목록에 액세스 하는 경우은 `const CTypedPtrList` `GetPrev` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터를 반환 합니다. 이를 통해 함수를 대입문의 오른쪽에만 사용할 수 있으므로 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이 직접 또는에 대 한 포인터를 통해 액세스 되는 경우은 `CTypedPtrList` `GetPrev` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

또는에 대 한 호출을 사용 하 여 `GetPrev` 초기 위치를 설정 하는 경우 역방향 반복 루프에서를 사용할 수 있습니다 `GetTailPosition` `Find` .

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

검색 된 요소가 목록의 첫 번째 이면 *Rposition* 의 새 값이 NULL로 설정 됩니다.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a> CTypedPtrList:: GetTail

이 목록의 head 요소를 나타내는 포인터를 가져옵니다.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

에 대 한 포인터를 통해 목록에 액세스 하는 경우은 `const CTypedPtrList` `GetTail` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터를 반환 합니다. 이를 통해 함수를 대입문의 오른쪽에만 사용할 수 있으므로 목록을 수정 하지 않도록 보호할 수 있습니다.

목록이 직접 또는에 대 한 포인터를 통해 액세스 되는 경우은 `CTypedPtrList` `GetTail` 템플릿 매개 변수 *형식* 으로 지정 된 형식의 포인터에 대 한 참조를 반환 합니다. 이를 통해 대입문의 한쪽에서 함수를 사용할 수 있으므로 목록 항목을 수정할 수 있습니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `GetTail` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](../../mfc/reference/coblist-class.md#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a> CTypedPtrList:: RemoveHead

목록에서 요소를 제거 하 고 반환 합니다.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

목록의 맨 위에 있는 포인터입니다. 이 포인터는 템플릿 매개 변수 *형식* 으로 지정 된 유형입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `RemoveHead` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](../../mfc/reference/coblist-class.md#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a> CTypedPtrList:: RemoveTail

목록의 끝에서 요소를 제거 하 고 반환 합니다.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
목록에 저장 된 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

목록의 끝에 있는 포인터입니다. 이 포인터는 템플릿 매개 변수 *형식* 으로 지정 된 유형입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 목록이 비어 있지 않은지 확인 해야 합니다 `RemoveTail` . 목록이 비어 있으면 MFC 라이브러리의 디버그 버전에서 어설션 합니다. [IsEmpty](../../mfc/reference/coblist-class.md#isempty) 를 사용 하 여 목록에 요소가 포함 되어 있는지 확인 합니다.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a> CTypedPtrList:: SetAt

이 멤버 함수는 `BASE_CLASS` **:: setat** 를 호출 합니다.

```cpp
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
설정할 요소의 위치입니다.

*TYPE*<br/>
기본 클래스 목록에 저장 된 요소의 형식입니다.

*newElement*<br/>
목록에 쓸 개체 포인터입니다.

### <a name="remarks"></a>설명

POSITION 형식의 변수는 목록의 키입니다. 인덱스와 동일 하지 않으며 위치 값에 직접 작업할 수 없습니다. `SetAt` 목록에서 지정 된 위치에 개체 포인터를 씁니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

자세한 내용은 [CObList:: SetAt](../../mfc/reference/coblist-class.md#setat)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CPtrList 클래스](../../mfc/reference/cptrlist-class.md)<br/>
[CObList 클래스](../../mfc/reference/coblist-class.md)

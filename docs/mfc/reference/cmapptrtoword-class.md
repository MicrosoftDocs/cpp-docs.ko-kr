---
description: '자세히 알아보기: CMapPtrToWord 클래스'
title: CMapPtrToWord 클래스
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapPtrToWord::CMapPtrToWord
- AFXCOLL/CMapPtrToWord::GetCount
- AFXCOLL/CMapPtrToWord::GetHashTableSize
- AFXCOLL/CMapPtrToWord::GetNextAssoc
- AFXCOLL/CMapPtrToWord::GetSize
- AFXCOLL/CMapPtrToWord::GetStartPosition
- AFXCOLL/CMapPtrToWord::HashKey
- AFXCOLL/CMapPtrToWord::InitHashTable
- AFXCOLL/CMapPtrToWord::IsEmpty
- AFXCOLL/CMapPtrToWord::Lookup
- AFXCOLL/CMapPtrToWord::LookupKey
- AFXCOLL/CMapPtrToWord::RemoveAll
- AFXCOLL/CMapPtrToWord::RemoveKey
- AFXCOLL/CMapPtrToWord::SetAt
helpviewer_keywords:
- CMapPtrToWord [MFC], CMapPtrToWord
- CMapPtrToWord [MFC], GetCount
- CMapPtrToWord [MFC], GetHashTableSize
- CMapPtrToWord [MFC], GetNextAssoc
- CMapPtrToWord [MFC], GetSize
- CMapPtrToWord [MFC], GetStartPosition
- CMapPtrToWord [MFC], HashKey
- CMapPtrToWord [MFC], InitHashTable
- CMapPtrToWord [MFC], IsEmpty
- CMapPtrToWord [MFC], Lookup
- CMapPtrToWord [MFC], LookupKey
- CMapPtrToWord [MFC], RemoveAll
- CMapPtrToWord [MFC], RemoveKey
- CMapPtrToWord [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: f1b9742b6693c07b27c22a77b8c45d5b20500bb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259489"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord 클래스

void 포인터로 키가 지정된 16비트 단어 맵을 지원합니다.

## <a name="syntax"></a>구문

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CMapPtrToWord` [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CMapStringToOb` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터가 함수 매개 변수 또는 반환 값으로 표시 되는 경우에는 단어를 대체 합니다. `CString`또는 **`const`** 포인터가 **`char`** 함수 매개 변수 또는 반환 값으로 표시 되는 경우 포인터를로 대체 **`void`** 합니다.

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

예를 들어 위의 코드는

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapPtrToWord::CMapPtrToWord](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapPtrToWord:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMapPtrToWord::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|해시 테이블의 현재 요소 수를 확인 합니다.|
|[CMapPtrToWord::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMapPtrToWord:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMapPtrToWord:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapPtrToWord:: HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|지정 된 키의 해시 값을 계산 합니다.|
|[CMapPtrToWord::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|해시 테이블을 초기화 합니다.|
|[CMapPtrToWord:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMapPtrToWord:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void 포인터 키에 기반 하 여 void 포인터를 조회 합니다. 포인터가 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapPtrToWord:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapPtrToWord:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMapPtrToWord:: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapPtrToWord:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMapPtrToWord:: operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

`CMapWordToPtr` IMPLEMENT_DYNAMIC 매크로를 통합 하 여 런타임 형식 액세스를 지원 하 고 개체를 덤프 `CDumpContext` 합니다. 개별 지도 요소에 대 한 덤프가 필요한 경우 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

단어 포인터 맵이 serialize 되지 않을 수 있습니다.

`CMapPtrToWord`개체가 삭제 되거나 해당 요소가 제거 되 면 포인터와 단어가 제거 됩니다. 키 포인터가 참조 하는 엔터티는 제거 되지 않습니다.

에 대 한 자세한 내용은 `CMapPtrToWord` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

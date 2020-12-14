---
description: '자세히 알아보기: CMapWordToOb 클래스'
title: CMapWordToOb 클래스
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: da21902c3789f1547055baffae5650fcb6b8c789
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336712"
---
# <a name="cmapwordtoob-class"></a>CMapWordToOb 클래스

16비트 단어로 키가 지정된 `CObject` 포인터 맵을 지원합니다.

## <a name="syntax"></a>구문

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CMapWordToOb` [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CMapStringToOb` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CString`또는 **`const`** 포인터가 **`char`** 함수 매개 변수 또는 반환 값으로 표시 되는 경우에는 단어를 대체 합니다.

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

예를 들어 위의 코드는

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapWordToOb:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|해시 테이블의 현재 요소 수를 확인 합니다.|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMapWordToOb:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMapWordToOb:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapWordToOb:: HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|지정 된 키의 해시 값을 계산 합니다.|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|해시 테이블을 초기화 합니다.|
|[CMapWordToOb:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMapWordToOb:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void 포인터 키에 기반 하 여 void 포인터를 조회 합니다. 포인터가 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapWordToOb:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapWordToOb:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMapWordToOb:: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapWordToOb:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMapWordToOb:: operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

`CMapWordToOb` 는 IMPLEMENT_SERIAL 매크로를 통합 하 여 요소의 serialization 및 덤프를 지원 합니다. 각 요소는 맵이 오버 로드 된 삽입 ( **<<** ) 연산자를 사용 하거나 멤버 함수를 사용 하 여 보관 파일에 저장 되는 경우에 차례로 serialize 됩니다 `Serialize` .

개별 단어 요소에 대 한 덤프가 필요한 경우 `CObject` 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

`CMapWordToOb`개체가 삭제 되거나 해당 요소가 제거 되 면 `CObject` 포인터가 제거 됩니다. 포인터가 참조 하는 개체는 `CObject` 제거 되지 않습니다.

에 대 한 자세한 내용은 `CMapWordToOb` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

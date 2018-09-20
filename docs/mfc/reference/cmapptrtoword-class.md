---
title: CMapPtrToWord 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 027841e3dfd5cea101633c8e3a609ab7e55eac07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389267"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord 클래스

void 포인터로 키가 지정된 16비트 단어 맵을 지원합니다.

## <a name="syntax"></a>구문

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>멤버

멤버 함수 `CMapPtrToWord` 클래스의 멤버 함수와 비슷합니다 [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)합니다. 이처럼 두 함수가 비슷하므로 `CMapStringToOb` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. 표시 될 때마다는 `CObject` 함수 매개 변수 또는 반환 값으로 포인터 단어를 대체 합니다. 표시 될 때마다를 `CString` 또는 **const** 에 대 한 포인터 **char** 함수 매개 변수 또는 반환 값에 대 한 포인터를 대체 **void**합니다.

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

예를 들어 위의 코드는

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|이 map에서 요소 수를 반환합니다.|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|현재 해시 테이블에 있는 요소 수를 결정합니다.|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|반복에 대 한 다음 요소를 가져옵니다.|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|이 map에서 요소 수를 반환합니다.|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|지정된 된 키의 해시 값을 계산합니다.|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|해시 테이블을 초기화합니다.|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|빈 맵을 조건 (요소 없음)에 대해 테스트 합니다.|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void 포인터 키를 기반으로 void 포인터를 조회 합니다. 이것이 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|지정된 된 키 값을 사용 하 여 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|이 맵에서 모든 요소를 제거합니다.|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|맵에; 요소를 삽입합니다. 일치 하는 키가 있을 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|이름|설명|
|----------|-----------------|
|[CMapStringToOb::operator [ ]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Map에 요소를 삽입-에 대 한 연산자 대체 `SetAt`합니다.|

## <a name="remarks"></a>설명

`CMapWordToPtr` 통합 런타임 형식 액세스 및 대 한 덤핑을 지원 하기 위해 IMPLEMENT_DYNAMIC 매크로 `CDumpContext` 개체입니다. 개별 지도 요소의 덤프가 필요한 경우 덤프 컨텍스트 깊이 1 이상으로 설정 해야 합니다.

단어에 대 한 포인터-맵 직렬화 할 수 없습니다.

경우는 `CMapPtrToWord` 개체를 삭제 하거나 해당 요소를 제거 하면 포인터 및 단어 제거 됩니다. 키 포인터에서 참조 하는 엔터티는 제거 되지 않습니다.

에 대 한 자세한 `CMapPtrToWord`, 문서를 참조 하세요 [컬렉션](../../mfc/collections.md)합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)




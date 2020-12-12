---
description: '자세한 정보: CMapStringToString 클래스'
title: CMapStringToString 클래스
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: ba82647a6e81e82b4d977e4de3beee1bfd0b7c4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207815"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 클래스

`CString` 개체로 키가 지정된 `CString` 개체의 맵을 지원합니다.

## <a name="syntax"></a>구문

```
class CMapStringToString : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CMapStringToString` [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CMapStringToOb` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터가 반환 값 또는 "output" 함수 매개 변수로 표시 되는 경우 포인터를로 대체 **`char`** 합니다. `CObject`"입력" 함수 매개 변수로 포인터가 표시 되는 경우 포인터를로 대체 **`char`** 합니다.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

예를 들어 위의 코드는

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>공용 구조체

|Name|설명|
|----------|-----------------|
|[CMapStringToString:: CPair](#cpair)|키 값과 연결 된 문자열 개체의 값을 포함 하는 중첩 된 구조체입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapStringToString:: CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapStringToString:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMapStringToString:: GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|해시 테이블의 현재 요소 수를 확인 합니다.|
|[CMapStringToString:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMapStringToString:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMapStringToString:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapStringToString:: HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|지정 된 키의 해시 값을 계산 합니다.|
|[CMapStringToString:: InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|해시 테이블을 초기화 합니다.|
|[CMapStringToString:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMapStringToString:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void 포인터 키에 기반 하 여 void 포인터를 조회 합니다. 포인터가 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapStringToString:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapStringToString::P GetFirstAssoc](#pgetfirstassoc)|맵의 첫 번째에 대 한 포인터를 가져옵니다 `CString` .|
|[CMapStringToString::P GetNextAssoc](#pgetnextassoc)|반복을 위해 다음에 대 한 포인터를 가져옵니다 `CString` .|
|[CMapStringToString::P 조회](#plookup)|지정 된 값과 일치 하는 값을 갖는에 대 한 포인터를 반환 합니다 `CString` .|
|[CMapStringToString:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMapStringToString:: RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapStringToString:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMapStringToString:: operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

`CMapStringToString`는 serialization 및 요소 덤프를 지원하기 위해 `IMPLEMENT_SERIAL` 매크로를 통합합니다. 각 요소는 맵이 오버 로드 된 삽입 ( **<<** ) 연산자를 사용 하거나 멤버 함수를 사용 하 여 보관 파일에 저장 되는 경우에 차례로 serialize 됩니다 `Serialize` .

개별 요소의 덤프가 필요한 경우 `CString` -  `CString` 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

`CMapStringToString`개체가 삭제 되거나 해당 요소가 제거 되 면 `CString` 개체가 적절 하 게 제거 됩니다.

에 대 한 자세한 내용은 `CMapStringToString` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a> CMapStringToString:: CPair

연결 된 문자열 개체의 키 값과 값을 포함 합니다.

### <a name="remarks"></a>설명

[Cmapstringtostring](../../mfc/reference/cmapstringtostring-class.md)클래스 내의 중첩 된 구조입니다.

구조는 다음 두 필드로 구성 됩니다.

- `key` 키 형식의 실제 값입니다.

- `value` 연결 된 개체의 값입니다.

[Cmapstringtostring::P lookup](#plookup), [cmapstringtostring::P getfirstassoc](#pgetfirstassoc)및 [cmapstringtostring::P getnextassoc](#pgetnextassoc)의 반환 값을 저장 하는 데 사용 됩니다.

### <a name="example"></a>예제

  사용 예제를 보려면 [Cmapstringtostring::P lookup](#plookup)의 예제를 참조 하세요.

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a> CMapStringToString::P GetFirstAssoc

Map 개체의 첫 번째 항목을 반환 합니다.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>반환 값

맵의 첫 번째 항목에 대 한 포인터입니다. [Cmapstringtostring:: CPair](#cpair)를 참조 하세요. Map이 비어 있으면 값은 NULL입니다.

### <a name="remarks"></a>설명

Map 개체의 첫 번째 요소에 대 한 포인터를 반환 하려면이 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a> CMapStringToString::P GetNextAssoc

*지 수를 가리키는* 지도 요소를 검색 합니다.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>매개 변수

*이상 Soc*<br/>
이전 [PGetNextAssoc](#pgetnextassoc) 또는 [Pgetfirstassoc](#pgetfirstassoc) 호출에서 반환 되는 맵 항목을 가리킵니다.

### <a name="return-value"></a>반환 값

맵의 다음 항목에 대 한 포인터입니다. [Cmapstringtostring:: CPair](#cpair)를 참조 하세요. 요소가 맵의 마지막 인 경우 값은 NULL입니다.

### <a name="remarks"></a>설명

Map의 모든 요소를 반복 하려면이 메서드를 호출 합니다. 에 대 한 호출을 사용 하 여 첫 번째 요소를 검색 `PGetFirstAssoc` 한 다음에 대 한 후속 호출을 사용 하 여 맵을 반복 `PGetNextAssoc` 합니다.

### <a name="example"></a>예제

  [Cmapstringtostring::P GetFirstAssoc](#pgetfirstassoc)의 예제를 참조 하세요.

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a> CMapStringToString::P 조회

지정 된 키에 매핑된 값을 조회 합니다.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 요소의 키에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 키에 대 한 포인터입니다.

### <a name="remarks"></a>설명

지정 된 키와 정확 하 게 일치 하는 키를 사용 하 여 map 요소를 검색 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

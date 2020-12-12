---
description: '자세히 알아보기: CMapStringToOb 클래스'
title: CMapStringToOb 클래스
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 9bd5f47fbb85e67784e5bcb50029d9d9e48e5bb4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207867"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb 클래스

고유한 `CString` 개체를 `CObject` 포인터에 매핑하는 사전 컬렉션 클래스입니다.

## <a name="syntax"></a>구문

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMapStringToOb:: CMapStringToOb](#cmapstringtoob)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMapStringToOb:: GetCount](#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMapStringToOb:: GetHashTableSize](#gethashtablesize)|해시 테이블의 현재 요소 수를 확인 합니다.|
|[CMapStringToOb:: GetNextAssoc](#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMapStringToOb:: GetSize](#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMapStringToOb:: GetStartPosition](#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMapStringToOb:: HashKey](#hashkey)|지정 된 키의 해시 값을 계산 합니다.|
|[CMapStringToOb:: InitHashTable](#inithashtable)|해시 테이블을 초기화 합니다.|
|[CMapStringToOb:: IsEmpty](#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMapStringToOb:: Lookup](#lookup)|Void 포인터 키에 기반 하 여 void 포인터를 조회 합니다. 포인터가 가리키는 엔터티가 아닌 포인터 값은 키 비교에 사용 됩니다.|
|[CMapStringToOb:: LookupKey](#lookupkey)|지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.|
|[CMapStringToOb:: RemoveAll](#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMapStringToOb:: RemoveKey](#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMapStringToOb:: SetAt](#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMapStringToOb:: operator \[\]](#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

`CString` -  `CObject*` 지도에 쌍 (요소)을 삽입 한 후에는 문자열 또는 값을 키로 사용 하 여 쌍을 효율적으로 검색 하거나 삭제할 수 있습니다 `CString` . 맵의 모든 요소를 반복할 수도 있습니다.

POSITION 형식의 변수는 모든 지도 변형에서 대체 항목 액세스에 사용 됩니다. 위치를 사용 하 여 항목을 "기억을" 하 고 맵을 반복할 수 있습니다. 이 반복은 키 값으로 순차적 이라고 생각할 수 있습니다. 그것이 아니야. 검색 된 요소의 시퀀스는 결정 되지 않습니다.

`CMapStringToOb`는 serialization 및 요소 덤프를 지원하기 위해 `IMPLEMENT_SERIAL` 매크로를 통합합니다. 각 요소는 맵이 오버 로드 된 삽입 ( **<<** ) 연산자를 사용 하거나 멤버 함수를 사용 하 여 보관 파일에 저장 되는 경우에 차례로 serialize 됩니다 `Serialize` .

맵의 개별 요소에 대 한 진단 덤프 ( `CString` 값 및 내용)가 필요한 경우 `CObject` 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

`CMapStringToOb`개체가 삭제 되거나 해당 요소가 제거 되 면 `CString` 개체와 `CObject` 포인터가 제거 됩니다. 포인터가 참조 하는 개체는 `CObject` 제거 되지 않습니다.

맵 클래스 파생은 목록 파생과 비슷합니다. 특수 한 용도의 목록 클래스의 파생에 대 한 예시는 문서 [컬렉션](../../mfc/collections.md) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a> CMapStringToOb:: CMapStringToOb

빈 `CString` - `CObject*` 맵을 생성 합니다.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
지도 확장을 위한 메모리 할당 세분성을 지정 합니다.

### <a name="remarks"></a>설명

맵이 커지면 메모리는 *Nblocksize* 항목의 단위로 할당 됩니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb:: CMapStringToOb` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Cmapstringtostring (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a> CMapStringToOb:: GetCount

지도에 있는 요소 수를 결정 합니다.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

이 map의 요소 수입니다.

### <a name="remarks"></a>설명

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::GetCount` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () const;**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a> CMapStringToOb:: GetHashTableSize

해시 테이블의 현재 요소 수를 확인 합니다.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>반환 값

해시 테이블의 요소 수를 반환 합니다.

### <a name="remarks"></a>설명

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::GetHashTableSize` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize () const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a> CMapStringToOb:: GetNextAssoc

*Rnextposition* 에서 map 요소를 검색 한 다음 map의 다음 요소를 참조 하도록 *rnextposition* 을 업데이트 합니다.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>매개 변수

*rNextPosition*<br/>
이전 또는 호출에서 반환 된 위치 값에 대 한 참조를 지정 합니다 `GetNextAssoc` `GetStartPosition` .

*rKey*<br/>
검색 된 요소의 반환 된 키 (문자열)를 지정 합니다.

*rValue*<br/>
검색 된 요소의 반환 값을 지정 합니다 ( `CObject` 포인터). 이 매개 변수에 대 한 자세한 내용은 설명 부분을 참조 하십시오.

### <a name="remarks"></a>설명

이 함수는 맵의 모든 요소를 반복 하는 데 가장 유용 합니다. 위치 시퀀스는 키 값 시퀀스와 동일할 필요는 없습니다.

검색 된 요소가 맵의 마지막 이면 *Rnextposition* 의 새 값이 NULL로 설정 됩니다.

*RValue* 매개 변수의 경우 다음 예제와 같이 개체 형식을 **CObject \* &** 로 캐스팅 해야 합니다 .이는 컴파일러에 필요한 항목입니다.

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

이는 템플릿에 기반한 맵의 경우에는 적용 되지 않습니다 `GetNextAssoc` .

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::GetNextAssoc` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (위치&** *rnextposition* **, void \* &** *rkey* **, void \* &** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (위치&** *rnextposition* **, void \* &** *rkey* **, WORD&** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (위치&** *rnextposition* **, CString&** *rkey* **, void \* &** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void GetNextAssoc (위치&** *rnextposition* **, cstring&** *rkey* **, cstring&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (위치&** *rnextposition* **, WORD&** *rkey* **, CObject \* &** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (위치&** *rnextposition* **, WORD&** *rkey* **, void \* &** *rValue* **) const;**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a> CMapStringToOb:: GetSize

지도 요소 수를 반환 합니다.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>반환 값

Map에 있는 항목의 수입니다.

### <a name="remarks"></a>설명

Map의 요소 수를 검색 하려면이 메서드를 호출 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::GetSize` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () const;**|

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a> CMapStringToOb:: GetStartPosition

호출에 전달 될 수 있는 위치 값을 반환 하 여 지도 반복을 시작 `GetNextAssoc` 합니다.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>반환 값

지도를 반복 하기 위한 시작 위치를 나타내는 위치 값입니다. 또는 map이 비어 있으면 NULL입니다.

### <a name="remarks"></a>설명

반복 시퀀스를 예측할 수 없습니다. 따라서 "맵의 첫 번째 요소"는 특별 한 의미가 없습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::GetStartPosition` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition () const;**|

### <a name="example"></a>예제

[CMapStringToOb:: GetNextAssoc](#getnextassoc)의 예제를 참조 하세요.

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a> CMapStringToOb:: HashKey

지정 된 키의 해시 값을 계산 합니다.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
해시 값을 계산할 키입니다.

### <a name="return-value"></a>반환 값

키의 해시 값입니다.

### <a name="remarks"></a>설명

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::HashKey` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT hashkey (LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT hashkey (LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT hashkey (WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT hashkey (WORD** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a> CMapStringToOb:: InitHashTable

해시 테이블을 초기화 합니다.

```cpp
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>매개 변수

*hashSize*<br/>
해시 테이블에 있는 항목의 수입니다.

*bAllocNow*<br/>
TRUE 이면 초기화 될 때 해시 테이블을 할당 합니다. 그렇지 않으면 필요한 경우 테이블이 할당 됩니다.

### <a name="remarks"></a>설명

최상의 성능을 위해 해시 테이블 크기는 소수 여야 합니다. 충돌을 최소화 하려면 크기가 가장 큰 예상 데이터 집합 보다 약 20% 커야 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::InitHashTable` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a> CMapStringToOb:: IsEmpty

Map이 비어 있는지 여부를 확인 합니다.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

이 맵에 요소가 포함 되지 않은 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[RemoveAll](#removeall)의 예제를 참조 하세요.

### <a name="remarks"></a>설명

다음 표에서는 **CMapStringToOb:: IsEmpty** 와 유사한 다른 멤버 함수를 보여 줍니다.

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty () const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a> CMapStringToOb:: Lookup

값을 `CObject` 기준으로 포인터를 반환 `CString` 합니다.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
조회할 요소를 식별 하는 문자열 키를 지정 합니다.

*rValue*<br/>
조회 요소에서 반환 된 값을 지정 합니다.

### <a name="return-value"></a>반환 값

요소가 발견 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Lookup` 는 해싱 알고리즘을 사용 하 여 정확 하 게 일치 하는 키 (값)를 사용 하 여 map 요소를 빠르게 찾습니다 `CString` .

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::LookUp` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 조회 (void** <strong>\*</strong> `key` **, void \* &** `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 조회 (void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup (LPCTSTR** `key` **, void \* &** `rValue` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup (LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup (WORD** `key` **, CObject \* &** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup (WORD** `key` **, void \* &** `rValue` **) const;**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a> CMapStringToOb:: LookupKey

지정 된 키 값과 연결 된 키에 대 한 참조를 반환 합니다.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
조회할 요소를 식별 하는 문자열 키를 지정 합니다.

*rKey*<br/>
연결 된 키에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

키가 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

연결 된 요소가 맵에서 제거 되거나 맵이 제거 된 후에 사용 하는 경우 키에 대 한 참조를 사용 하는 것은 안전 하지 않습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb:: LookupKey` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a> CMapStringToOb:: operator []

멤버 함수를 편리 하 게 대체 합니다 `SetAt` .

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>반환 값

개체에 대 한 포인터에 대 한 참조 이거나 `CObject` , 맵이 비어 있거나 *키* 가 범위를 벗어난 경우 NULL입니다.

### <a name="remarks"></a>설명

따라서 대입문 (l-value)의 왼쪽에만 사용할 수 있습니다. 지정 된 키를 가진 지도 요소가 없으면 새 요소가 생성 됩니다.

지도에서 키를 찾을 수 없기 때문에이 연산자에 해당 하는 "right side" (r-value)가 없습니다. `Lookup`요소 검색에 멤버 함수를 사용 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::operator []` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void \*& 연산자 \[ ] (void \*</strong> `key` **\) ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD& 연산자 \[ ] (void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void \*& 연산자 \[ ] (lpctstr** `key` **\) ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString& 연산자 \[ ] (lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject \*& 연산자 \[ ] (word** `key` **\) ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void \*& 연산자 \[ ] (word** `key` **\) ;**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a> CMapStringToOb:: RemoveAll

이 맵에서 모든 요소를 제거 하 고 `CString` 키 개체를 제거 합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

`CObject`각 키에서 참조 하는 개체는 제거 되지 않습니다. `RemoveAll`참조 된 개체가 제거 되지 않도록 하는 경우 함수는 메모리 누수를 일으킬 수 있습니다 `CObject` .

Map이 이미 비어 있는 경우 함수가 제대로 작동 합니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::RemoveAll` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a> CMapStringToOb:: RemoveKey

제공 된 키에 해당 하는 맵 항목을 찾습니다. 그런 다음 키가 발견 되 면 항목을 제거 합니다.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
지도 조회에 사용 되는 문자열을 지정 합니다.

### <a name="return-value"></a>반환 값

항목이 발견 되어 성공적으로 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CObject`다른 곳에서 개체가 삭제 되지 않으면이로 인해 메모리 누수가 발생할 수 있습니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::RemoveKey` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a> CMapStringToOb:: SetAt

주는 map에 요소를 삽입 하는 것입니다.

```cpp
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
새 요소의 키인 문자열을 지정 합니다.

*newValue*<br/>
`CObject`새 요소의 값인 포인터를 지정 합니다.

### <a name="remarks"></a>설명

먼저 키가 조회 됩니다. 키가 발견 되 면 해당 값이 변경 됩니다. 그렇지 않으면 새 키-값 요소가 만들어집니다.

다음 표에서는와 유사한 다른 멤버 함수를 보여 줍니다 `CMapStringToOb::SetAt` .

|클래스|멤버 함수|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void SetAt (void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void setat (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void setat (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void setat (WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void setat (WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>예제

모든 컬렉션 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` .

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

이 프로그램의 결과는 다음과 같습니다.

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 클래스](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 클래스](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr 클래스](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString 클래스](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb 클래스](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr 클래스](../../mfc/reference/cmapwordtoptr-class.md)

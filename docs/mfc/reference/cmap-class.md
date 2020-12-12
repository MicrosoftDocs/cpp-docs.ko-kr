---
description: '자세히 알아보기: CMap 클래스'
title: CMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: ff88d205608cc87f06d28e6d2d4b647c35909efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207906"
---
# <a name="cmap-class"></a>CMap 클래스

고유 키를 값에 매핑하는 사전 컬렉션 클래스입니다.

## <a name="syntax"></a>구문

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>매개 변수

*KEY*<br/>
맵에 키로 사용 되는 개체의 클래스입니다.

*ARG_KEY*<br/>
*키* 인수에 사용 되는 데이터 형식 일반적으로 *키* 에 대 한 참조입니다.

*VALUE*<br/>
맵에 저장 된 개체의 클래스입니다.

*ARG_VALUE*<br/>
*값* 인수에 사용 되는 데이터 형식입니다. 일반적으로 *값* 에 대 한 참조입니다.

## <a name="members"></a>멤버

### <a name="public-structures"></a>공용 구조체

|Name|설명|
|----------|-----------------|
|[CMap:: Cmap](#cpair)|키 값과 연결 된 개체의 값을 포함 하는 중첩 된 구조체입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMap:: CMap](#cmap)|키를 값에 매핑하는 컬렉션을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMap:: GetCount](#getcount)|이 map의 요소 수를 반환 합니다.|
|[CMap:: GetHashTableSize](#gethashtablesize)|해시 테이블의 요소 수를 반환 합니다.|
|[CMap:: GetNextAssoc](#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[CMap:: GetSize](#getsize)|이 map의 요소 수를 반환 합니다.|
|[CMap:: GetStartPosition](#getstartposition)|첫 번째 요소의 위치를 반환 합니다.|
|[CMap:: InitHashTable](#inithashtable)|해시 테이블을 초기화 하 고 해당 테이블의 크기를 지정 합니다.|
|[CMap:: IsEmpty](#isempty)|빈 맵 조건 (요소 없음)을 테스트 합니다.|
|[CMap:: Lookup](#lookup)|지정 된 키에 매핑된 값을 조회 합니다.|
|[CMap::P GetFirstAssoc](#pgetfirstassoc)|첫 번째 요소에 대 한 포인터를 반환 합니다.|
|[CMap::P GetNextAssoc](#pgetnextassoc)|반복할 다음 요소에 대 한 포인터를 가져옵니다.|
|[CMap::P 조회](#plookup)|지정 된 값과 일치 하는 값을 가진 키에 대 한 포인터를 반환 합니다.|
|[CMap:: RemoveAll](#removeall)|이 맵에서 모든 요소를 제거 합니다.|
|[CMap:: RemoveKey](#removekey)|키로 지정 된 요소를 제거 합니다.|
|[CMap:: SetAt](#setat)|지도에 요소를 삽입 합니다. 일치 하는 키가 있는 경우 기존 요소를 바꿉니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CMap:: operator \[\]](#operator_at)|에 요소를 삽입 합니다 (에 대 한 연산자 대체) `SetAt` .|

## <a name="remarks"></a>설명

키-값 쌍 (요소)을 맵에 삽입 한 후에는 키를 사용 하 여 쌍을 효율적으로 검색 하거나 삭제 하 여 액세스할 수 있습니다. 맵의 모든 요소를 반복할 수도 있습니다.

POSITION 형식의 변수는 항목에 대 한 대체 액세스에 사용 됩니다. 위치를 사용 하 여 항목을 "기억을" 하 고 맵을 반복할 수 있습니다. 이 반복은 키 값으로 순차적 이라고 생각할 수 있습니다. 그것이 아니야. 검색 된 요소의 시퀀스는 결정 되지 않습니다.

이 클래스의 특정 멤버 함수는 대부분의 클래스 사용에 대해 사용자 지정 해야 하는 전역 도우미 함수를 호출 합니다 `CMap` . **MFC 참조** 의 매크로 및 전역 섹션에서 [컬렉션 클래스 도우미](../../mfc/reference/collection-class-helpers.md) 를 참조 하세요.

`CMap` 는 [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) 를 재정의 하 여 요소의 serialization 및 덤프를 지원 합니다. 맵이를 사용 하 여 보관 파일에 저장 된 경우 `Serialize` 각 지도 요소는 차례로 직렬화 됩니다. 도우미 함수의 기본 구현에서는 `SerializeElements` 비트 쓰기를 수행 합니다. 또는 다른 사용자 정의 형식에서 파생 된 포인터 컬렉션 항목의 serialization에 대 한 자세한 내용은 `CObject` [방법: Type-Safe 컬렉션 만들기](../../mfc/how-to-make-a-type-safe-collection.md)를 참조 하세요.

지도에 있는 개별 요소의 진단 덤프 (키 및 값)가 필요한 경우 덤프 컨텍스트의 깊이를 1 이상으로 설정 해야 합니다.

`CMap`개체가 삭제 되거나 해당 요소가 제거 되 면 키와 값이 모두 제거 됩니다.

맵 클래스 파생은 목록 파생과 비슷합니다. 특수 한 용도의 목록 클래스의 파생에 대 한 예시는 문서 [컬렉션](../../mfc/collections.md) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>요구 사항

**헤더:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a> CMap:: CMap

빈 맵을 생성 합니다.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
지도 확장을 위한 메모리 할당 세분성을 지정 합니다.

### <a name="remarks"></a>설명

맵이 커지면 메모리는 *Nblocksize* 항목의 단위로 할당 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a> CMap:: Cmap

키 값과 연결 된 개체의 값을 포함 합니다.

### <a name="remarks"></a>설명

이는 [Cmap](../../mfc/reference/cmap-class.md)클래스 내에서 중첩 된 구조입니다.

구조는 다음 두 필드로 구성 됩니다.

- `key` 키 형식의 실제 값입니다.

- `value` 연결 된 개체의 값입니다.

Cmap의 반환 값을 저장 하는 데 사용 됩니다 [::P lookup](#plookup), [cmap::P getfirstassoc](#pgetfirstassoc)및 [cmap::P getnextassoc](#pgetnextassoc).

### <a name="example"></a>예제

사용법에 대 한 예제는 [Cmap::P lookup](#plookup)의 예제를 참조 하세요.

## <a name="cmapgetcount"></a><a name="getcount"></a> CMap:: GetCount

Map의 요소 수를 검색 합니다.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>반환 값

요소의 수입니다.

### <a name="example"></a>예제

[Cmap:: Lookup](#lookup)의 예제를 참조 하세요.

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a> CMap:: GetHashTableSize

맵에 대 한 해시 테이블의 요소 수를 결정 합니다.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>반환 값

해시 테이블에 있는 요소 수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a> CMap:: GetNextAssoc

에서 지도 요소를 검색 `rNextPosition` 한 다음 `rNextPosition` map의 다음 요소를 참조 하도록 업데이트 합니다.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>매개 변수

*rNextPosition*<br/>
이전 또는 호출에서 반환 된 위치 값에 대 한 참조를 지정 합니다 `GetNextAssoc` `GetStartPosition` .

*KEY*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*rKey*<br/>
검색 된 요소의 반환 된 키를 지정 합니다.

*VALUE*<br/>
지도 값의 유형을 지정 하는 템플릿 매개 변수입니다.

*rValue*<br/>
검색 된 요소의 반환 값을 지정 합니다.

### <a name="remarks"></a>설명

이 함수는 맵의 모든 요소를 반복 하는 데 가장 유용 합니다. 위치 시퀀스는 키 값 시퀀스와 동일할 필요는 없습니다.

검색 된 요소가 맵의 마지막 이면 *Rnextposition* 의 새 값이 NULL로 설정 됩니다.

### <a name="example"></a>예제

[Cmap:: SetAt](#setat)의 예제를 참조 하세요.

## <a name="cmapgetsize"></a><a name="getsize"></a> CMap:: GetSize

지도 요소 수를 반환 합니다.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>반환 값

Map에 있는 항목의 수입니다.

### <a name="remarks"></a>설명

Map의 요소 수를 검색 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a> CMap:: GetStartPosition

호출에 전달 될 수 있는 위치 값을 반환 하 여 지도 반복을 시작 `GetNextAssoc` 합니다.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>반환 값

지도를 반복 하기 위한 시작 위치를 나타내는 위치 값입니다. 또는 map이 비어 있으면 NULL입니다.

### <a name="remarks"></a>설명

반복 시퀀스를 예측할 수 없습니다. 따라서 "맵의 첫 번째 요소"는 특별 한 의미가 없습니다.

### <a name="example"></a>예제

[Cmap:: SetAt](#setat)의 예제를 참조 하세요.

## <a name="cmapinithashtable"></a><a name="inithashtable"></a> CMap:: InitHashTable

해시 테이블을 초기화 합니다.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>매개 변수

*hashSize*<br/>
해시 테이블에 있는 항목의 수입니다.

*bAllocNow*<br/>
TRUE 이면 초기화 될 때 해시 테이블을 할당 합니다. 그렇지 않으면 필요한 경우 테이블이 할당 됩니다.

### <a name="remarks"></a>설명

최상의 성능을 위해 해시 테이블 크기는 소수 여야 합니다. 충돌을 최소화 하려면 크기가 가장 큰 예상 데이터 집합 보다 약 20% 커야 합니다.

### <a name="example"></a>예제

[Cmap:: Lookup](#lookup)의 예제를 참조 하세요.

## <a name="cmapisempty"></a><a name="isempty"></a> CMap:: IsEmpty

Map이 비어 있는지 여부를 확인 합니다.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

이 맵에 요소가 포함 되지 않은 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[Cmap:: RemoveAll](#removeall)에 대 한 예제를 참조 하세요.

## <a name="cmaplookup"></a><a name="lookup"></a> CMap:: Lookup

지정 된 키에 매핑된 값을 조회 합니다.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>매개 변수

*ARG_KEY*<br/>
*키* 값의 유형을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
조회할 요소를 식별 하는 키를 지정 합니다.

*VALUE*<br/>
조회할 값의 유형을 지정 합니다.

*rValue*<br/>
조회 값을 받습니다.

### <a name="return-value"></a>반환 값

요소가 발견 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Lookup` 는 해싱 알고리즘을 사용 하 여 지정 된 키와 정확히 일치 하는 키로 지도 요소를 빠르게 찾습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a> CMap:: operator []

멤버 함수를 편리 하 게 대체 합니다 `SetAt` .

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>매개 변수

*VALUE*<br/>
지도 값의 유형을 지정 하는 템플릿 매개 변수입니다.

*ARG_KEY*<br/>
키 값의 유형을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
맵에서 값을 검색 하는 데 사용 되는 키입니다.

### <a name="remarks"></a>설명

따라서 대입문 (l-value)의 왼쪽에만 사용할 수 있습니다. 지정 된 키를 가진 지도 요소가 없으면 새 요소가 생성 됩니다.

지도에서 키를 찾을 수 없기 때문에이 연산자에 해당 하는 "right side" (r-value)가 없습니다. `Lookup`요소 검색에 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[Cmap:: Lookup](#lookup)의 예제를 참조 하세요.

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a> CMap::P GetFirstAssoc

Map 개체의 첫 번째 항목을 반환 합니다.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>반환 값

맵의 첫 번째 항목에 대 한 포인터입니다. [Cmap:: Cmap](#cpair)를 참조 하세요. 맵에 항목이 포함 되지 않은 경우 값은 NULL입니다.

### <a name="remarks"></a>설명

Map 개체의 첫 번째 요소에 대 한 포인터를 반환 하려면이 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a> CMap::P GetNextAssoc

*지 수를 가리키는* 지도 요소를 검색 합니다.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>매개 변수

*고가*<br/>
이전 [PGetNextAssoc](#pgetnextassoc) 또는 [cmap::P getfirstassoc](#pgetfirstassoc) 호출에서 반환 되는 맵 항목을 가리킵니다.

### <a name="return-value"></a>반환 값

맵의 다음 항목에 대 한 포인터입니다. [Cmap:: Cmap](#cpair)를 참조 하세요. 요소가 맵의 마지막 인 경우 값은 NULL입니다.

### <a name="remarks"></a>설명

Map의 모든 요소를 반복 하려면이 메서드를 호출 합니다. 에 대 한 호출을 사용 하 여 첫 번째 요소를 검색 `PGetFirstAssoc` 한 다음에 대 한 후속 호출을 사용 하 여 맵을 반복 `PGetNextAssoc` 합니다.

### <a name="example"></a>예제

[Cmap::P GetFirstAssoc](#pgetfirstassoc)의 예제를 참조 하세요.

## <a name="cmapplookup"></a><a name="plookup"></a> CMap::P 조회

지정 된 키에 매핑되는 값을 찾습니다.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 요소의 키입니다.

### <a name="return-value"></a>반환 값

키 구조에 대 한 포인터입니다. [Cmap:: Cmap](#cpair)를 참조 하세요. 일치 하는 항목이 없으면 `CMap::PLookup` NULL을 반환 합니다.

### <a name="remarks"></a>설명

지정 된 키와 정확 하 게 일치 하는 키를 사용 하 여 map 요소를 검색 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a> CMap:: RemoveAll

전역 도우미 함수를 호출 하 여이 맵에서 모든 값을 제거 합니다 `DestructElements` .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

Map이 이미 비어 있는 경우 함수가 제대로 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a> CMap:: RemoveKey

제공 된 키에 해당 하는 맵 항목을 찾습니다. 그런 다음 키가 발견 되 면 항목을 제거 합니다.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>매개 변수

*ARG_KEY*<br/>
키의 유형을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
제거할 요소의 키입니다.

### <a name="return-value"></a>반환 값

항목이 발견 되어 성공적으로 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`DestructElements`도우미 함수는 항목을 제거 하는 데 사용 됩니다.

### <a name="example"></a>예제

[Cmap:: SetAt](#setat)의 예제를 참조 하세요.

## <a name="cmapsetat"></a><a name="setat"></a> CMap:: SetAt

주는 map에 요소를 삽입 하는 것입니다.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>매개 변수

*ARG_KEY*<br/>
*키* 매개 변수의 형식을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
새 요소의 키를 지정 합니다.

*ARG_VALUE*<br/>
*NewValue* 매개 변수의 형식을 지정 하는 템플릿 매개 변수입니다.

*newValue*<br/>
새 요소의 값을 지정 합니다.

### <a name="remarks"></a>설명

먼저 키가 조회 됩니다. 키가 발견 되 면 해당 값이 변경 됩니다. 그렇지 않으면 새 키-값 쌍이 만들어집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 수집](../../overview/visual-cpp-samples.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

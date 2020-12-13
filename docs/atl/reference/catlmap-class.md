---
description: '자세한 정보: CAtlMap 클래스'
title: CAtlMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 721f0f3a41afb409ec8cdc505a5f5e5324cdb9bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147253"
---
# <a name="catlmap-class"></a>CAtlMap 클래스

이 클래스는 map 개체를 만들고 관리 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>매개 변수

*K*<br/>
키 요소 형식입니다.

*V*<br/>
값 요소 형식입니다.

*KTraits*<br/>
키 요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다. 자세한 내용은 [CElementTraits 클래스](../../atl/reference/celementtraits-class.md) 를 참조 하세요.

*VTraits*<br/>
값 요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[KINARGTYPE::](#kinargtype)|키가 입력 인수로 전달 될 때 사용 되는 형식입니다.|
|[CAtlMap:: KOUTARGTYPE](#koutargtype)|키가 output 인수로 반환 될 때 사용 되는 형식입니다.|
|[VINARGTYPE::](#vinargtype)|값이 입력 인수로 전달 될 때 사용 되는 형식입니다.|
|[CAtlMap:: VOUTARGTYPE](#voutargtype)|값이 출력 인수로 전달 될 때 사용 되는 형식입니다.|

### <a name="public-classes"></a>public 클래스

|Name|설명|
|----------|-----------------|
|[CAtlMap:: CPair 클래스](#cpair_class)|키 및 값 요소를 포함 하는 클래스입니다.|

### <a name="cpair-data-members"></a>CPair 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPair:: m_key](#m_key)|키 요소를 저장 하는 데이터 멤버입니다.|
|[CPair:: m_value](#m_value)|Value 요소를 저장 하는 데이터 멤버입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlMap:: CAtlMap](#catlmap)|생성자입니다.|
|[이상 지도:: ~ CAtlMap](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[AssertValid::](#assertvalid)|이 잘못 된 경우 ASSERT를 발생 시키려면이 메서드를 호출 `CAtlMap` 합니다.|
|[이상 지도::D isableAutoRehash](#disableautorehash)|개체의 자동 rehashing을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[EnableAutoRehash::](#enableautorehash)|개체의 자동 rehashing을 사용 하도록 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[GetAt::](#getat)|Map의 지정 된 위치에 있는 요소를 반환 하려면이 메서드를 호출 합니다.|
|[CAtlMap:: GetCount](#getcount)|Map의 요소 수를 검색 하려면이 메서드를 호출 합니다.|
|[GetHashTableSize::](#gethashtablesize)|맵의 해시 테이블에 있는 bin 수를 확인 하려면이 메서드를 호출 합니다.|
|[CAtlMap:: GetKeyAt](#getkeyat)|개체의 지정 된 위치에 저장 된 키를 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[GetNext::](#getnext)|개체에 저장 된 다음 요소 쌍에 대 한 포인터를 가져오려면이 메서드를 호출 `CAtlMap` 합니다.|
|[GetNextAssoc::](#getnextassoc)|반복할 다음 요소를 가져옵니다.|
|[GetNextKey::](#getnextkey)|개체에서 다음 키를 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[GetNextValue::](#getnextvalue)|개체에서 다음 값을 가져오려면이 메서드를 호출 `CAtlMap` 합니다.|
|[CAtlMap:: GetStartPosition](#getstartposition)|지도 반복을 시작 하려면이 메서드를 호출 합니다.|
|[CAtlMap:: GetValueAt](#getvalueat)|개체의 지정 된 위치에 저장 된 값을 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[InitHashTable::](#inithashtable)|해시 테이블을 초기화 하려면이 메서드를 호출 합니다.|
|[IsEmpty::](#isempty)|빈 map 개체를 테스트 하려면이 메서드를 호출 합니다.|
|[이상 지도:: Lookup](#lookup)|개체에서 키 또는 값을 조회 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[Rehash::](#rehash)|이 메서드를 호출 하 여 `CAtlMap` 개체를 rehash 합니다.|
|[RemoveAll::](#removeall)|개체에서 모든 요소를 제거 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[CAtlMap:: RemoveAtPos](#removeatpos)|개체의 지정 된 위치에서 요소를 제거 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[CAtlMap:: RemoveKey](#removekey)|키가 지정 된 경우이 메서드를 호출 하 여 개체에서 요소를 제거 `CAtlMap` 합니다.|
|[, CAtlMap:: SetAt](#setat)|지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.|
|[SetOptimalLoad::](#setoptimalload)|개체의 최적 로드를 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.|
|[CAtlMap:: SetValueAt](#setvalueat)|개체의 지정 된 위치에 저장 된 값을 변경 하려면이 메서드를 호출 `CAtlMap` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|새 요소를로 바꾸거나 추가 `CAtlMap` 합니다.|

## <a name="remarks"></a>설명

`CAtlMap` 지정 된 형식의 매핑 배열을 지원 하 여 키 요소 및 관련 값의 순서가 지정 되지 않은 배열을 관리 합니다. 키와 값으로 구성 된 요소는 해싱 알고리즘을 사용 하 여 저장 되므로 많은 양의 데이터를 효율적으로 저장 하 고 검색할 수 있습니다.

*Ktraits* 및 *vtraits* 매개 변수는 요소를 복사 하거나 이동 하는 데 필요한 보충 코드를 포함 하는 특성 클래스입니다.

에 대 한 대안은 `CAtlMap` [Crbmap](../../atl/reference/crbmap-class.md) 클래스에서 제공 됩니다. `CRBMap` 또한는 키/값 쌍을 저장 하지만 다른 성능 특징을 보여 주는 것입니다. 항목을 삽입 하거나, 키를 조회 하거나, 개체에서 키를 삭제 하는 데 걸린 시간은 `CRBMap` *log (n)* 입니다. 여기서 *n* 은 요소 수입니다. 의 경우 `CAtlMap` 이러한 모든 작업은 일반적으로 일정 한 시간을 사용 하지만 최악의 시나리오는 주문 *n* 일 수 있습니다. 따라서 일반적인 경우 `CAtlMap` 는 더 빠릅니다.

및의 다른 차이 `CRBMap` 는 `CAtlMap` 저장 된 요소를 반복할 때 분명 하 게 드러납니다. 에서 `CRBMap` 요소는 정렬 된 순서로 방문 됩니다. 에서 `CAtlMap` 요소는 정렬 되지 않으며 순서를 유추할 수 없습니다.

적은 수의 요소를 저장 해야 하는 경우 [Csimplvalclass](../../atl/reference/csimplemap-class.md) 를 대신 사용 하는 것이 좋습니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a> AssertValid::

개체가 유효 하지 않은 경우 어설션을 발생 시키려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>설명

디버그 빌드에서이 메서드는 `CAtlMap` 개체가 유효 하지 않은 경우 어설션을 발생 시킵니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapcatlmap"></a><a name="catlmap"></a> CAtlMap:: CAtlMap

생성자입니다.

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>매개 변수

*nBins*<br/>
저장 된 요소에 대 한 포인터를 제공 하는 bin 수입니다. Bin에 대 한 설명은이 항목의 뒷부분에 나오는 주의를 참조 하세요.

*fOptimalLoad*<br/>
최적 로드 비율입니다.

*fLoThreshold*<br/>
부하 비율의 하 한 임계값입니다.

*fHiThreshold*<br/>
로드 비율의 상한 임계값입니다.

*nBlockSize*<br/>
블록의 크기입니다.

### <a name="remarks"></a>설명

`CAtlMap` 는 먼저 키에 해싱 알고리즘을 사용 하 여 인덱스를 만들어 저장 된 모든 요소를 참조 합니다. 이 인덱스는 저장 된 요소에 대 한 포인터를 포함 하는 "bin"을 참조 합니다. Bin을 이미 사용 하 고 있는 경우에는 연결 된 목록을 만들어 후속 요소에 액세스 합니다. 올바른 요소에 직접 액세스 하는 것 보다는 목록을 트래버스하는 속도가 느리므로 지도 구조는 저장소 요구 사항을 성능에 맞게 조정 해야 합니다. 대부분의 경우 좋은 결과를 제공 하기 위해 기본 매개 변수를 선택 했습니다.

로드 비율은 map 개체에 저장 된 요소 수에 대 한 bin 수의 비율입니다. 지도 구조가 다시 계산 되는 경우 *fOptimalLoad* 매개 변수 값은 필요한 bin 수를 계산 하는 데 사용 됩니다. 이 값은 [SetOptimalLoad](#setoptimalload) 메서드를 사용 하 여 변경할 수 있습니다.

*FLoThreshold* 매개 변수는 로드 비율이 도달할 수 있는 더 낮은 값으로,이 값은 `CAtlMap` 지도의 최적 크기를 다시 계산 합니다.

*Fhithreshold* 매개 변수는 `CAtlMap` 개체가 지도의 최적 크기를 다시 계산 하기 전까지 로드 비율이 도달할 수 있는 상한 값입니다.

이 다시 계산 프로세스 (rehashing 라고 함)는 기본적으로 사용 하도록 설정 되어 있습니다. 이 프로세스를 사용 하지 않도록 설정 하려는 경우에는 한 번에 많은 데이터를 입력할 때 [:D isableautorehash](#disableautorehash) 메서드를 호출 합니다. [EnableAutoRehash](#enableautorehash) 메서드를 사용 하 여 다시 활성화 합니다.

*Nblocksize* 매개 변수는 새 요소가 필요할 때 할당 된 메모리 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다.

데이터를 저장 하려면 먼저 [Catlmap:: InitHashTable](#inithashtable)에 대 한 호출을 사용 하 여 해시 테이블을 초기화 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a> 이상 지도:: ~ CAtlMap

소멸자입니다.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a> CAtlMap:: CPair 클래스

키 및 값 요소를 포함 하는 클래스입니다.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>설명

이 클래스는 요소에 저장 된 키 및 값 요소에 액세스 하는 데 사용할 수 있는 [GetNext](#getnext) 및 catlmap: [: Lookup](#lookup) 메서드에서 사용 됩니다.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a> 이상 지도::D isableAutoRehash

개체의 자동 rehashing을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>설명

자동 rehashing을 사용 하는 경우 (기본적으로), 로드 값 (배열에 저장 된 요소 수에 대 한 bin 수의 비율)이 맵이 생성 될 때 지정 된 최대값이 나 최소값을 초과 하는 경우 해시 테이블의 bin 수가 자동으로 다시 계산 됩니다.

`DisableAutoRehash` 는 한 번에 많은 수의 요소가 맵에 추가 되는 경우에 가장 유용 합니다. 제한이 초과 될 때마다 rehashing 프로세스를 트리거하는 대신,를 호출 하 `DisableAutoRehash` 고, 요소를 추가 하 고, 마지막으로 [Catlmap:: EnableAutoRehash](#enableautorehash)를 호출 하는 것이 더 효율적입니다.

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a> EnableAutoRehash::

개체의 자동 rehashing을 사용 하도록 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>설명

자동 rehashing을 사용 하는 경우 (기본적으로), 로드 값 (배열에 저장 된 요소 수에 대 한 bin 수의 비율)이 map을 만들 때 지정 된 최대값이 나 최소값을 초과 하면 해시 테이블의 bin 수가 자동으로 다시 계산 됩니다.

`EnableAutoRefresh` 는 [:D isableautorehash](#disableautorehash)를 호출 하는 경우에 가장 자주 사용 됩니다.

## <a name="catlmapgetat"></a><a name="getat"></a> GetAt::

Map의 지정 된 위치에 있는 요소를 반환 하려면이 메서드를 호출 합니다.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

*key*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*value*<br/>
지도 값의 유형을 지정 하는 템플릿 매개 변수입니다.

### <a name="return-value"></a>반환 값

Map에 저장 된 키/값 요소의 현재 쌍에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

## <a name="catlmapgetcount"></a><a name="getcount"></a> CAtlMap:: GetCount

Map의 요소 수를 검색 하려면이 메서드를 호출 합니다.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>반환 값

Map 개체의 요소 수를 반환 합니다. 단일 요소는 키/값 쌍입니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a> GetHashTableSize::

맵의 해시 테이블에 있는 bin 수를 확인 하려면이 메서드를 호출 합니다.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>반환 값

해시 테이블의 bin 수를 반환 합니다. 설명에 대 한 [자세한 내용은 다음](#catlmap) 을 참조 하세요.

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a> CAtlMap:: GetKeyAt

개체의 지정 된 위치에 저장 된 키를 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

개체의 지정 된 위치에 저장 된 키에 대 한 참조를 반환 합니다 `CAtlMap` .

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapgetnext"></a><a name="getnext"></a> GetNext::

개체에 저장 된 다음 요소 쌍에 대 한 포인터를 가져오려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

Map에 저장 된 키/값 요소의 다음 쌍에 대 한 포인터를 반환 합니다. *Pos* position 카운터는 각 호출 후에 업데이트 됩니다. 검색 된 요소가 맵의 마지막 이면 *pos* 가 NULL로 설정 됩니다.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a> GetNextAssoc::

반복할 다음 요소를 가져옵니다.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

*key*<br/>
지도 키의 유형을 지정 하는 템플릿 매개 변수입니다.

*value*<br/>
지도 값의 유형을 지정 하는 템플릿 매개 변수입니다.

### <a name="remarks"></a>설명

*Pos* position 카운터는 각 호출 후에 업데이트 됩니다. 검색 된 요소가 맵의 마지막 이면 *pos* 가 NULL로 설정 됩니다.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a> GetNextKey::

개체에서 다음 키를 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

Map의 다음 키에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

현재 위치 카운터, *pos* 를 업데이트 합니다. 지도에 더 이상 항목이 없으면 position 카운터가 NULL로 설정 됩니다.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a> GetNextValue::

개체에서 다음 값을 가져오려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

Map의 다음 값에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

현재 위치 카운터, *pos* 를 업데이트 합니다. 지도에 더 이상 항목이 없으면 position 카운터가 NULL로 설정 됩니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a> CAtlMap:: GetStartPosition

지도 반복을 시작 하려면이 메서드를 호출 합니다.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>반환 값

시작 위치를 반환 하거나 map이 비어 있는 경우 NULL이 반환 됩니다.

### <a name="remarks"></a>설명

메서드에 전달할 수 있는 위치 값을 반환 하 여 지도 반복을 시작 하려면이 메서드를 호출 `GetNextAssoc` 합니다.

> [!NOTE]
> 반복 시퀀스를 예측할 수 없습니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a> CAtlMap:: GetValueAt

개체의 지정 된 위치에 저장 된 값을 검색 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

개체의 지정 된 위치에 저장 된 값에 대 한 참조를 반환 합니다 `CAtlMap` .

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a> InitHashTable::

해시 테이블을 초기화 하려면이 메서드를 호출 합니다.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>매개 변수

*nBins*<br/>
해시 테이블에서 사용 하는 bin 수입니다. 설명에 대 한 [자세한 내용은 다음](#catlmap) 을 참조 하세요.

*bAllocNow*<br/>
메모리를 할당 해야 하는 경우 플래그를 나타냅니다.

### <a name="return-value"></a>반환 값

성공적으로 초기화 되 면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`InitHashTable` 는 해시 테이블에 요소를 저장 하기 전에 호출 해야 합니다.  이 메서드를 명시적으로 호출 하지 않으면 생성자에서 지정한 bin 수를 사용 하 여 요소를 처음 추가할 때 자동으로 호출 됩니다 `CAtlMap` .  그렇지 않으면 맵은 *nbins* 매개 변수로 지정 된 새 bin 개수를 사용 하 여 초기화 됩니다.

*BAllocNow* 매개 변수가 false 인 경우 해시 테이블에 필요한 메모리는 처음 필요할 때까지 할당 되지 않습니다. 이는 map이 사용 되는 경우에 확실 하지 않을 경우 유용할 수 있습니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapisempty"></a><a name="isempty"></a> IsEmpty::

빈 map 개체를 테스트 하려면이 메서드를 호출 합니다.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>반환 값

Map이 비어 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a> KINARGTYPE::

키가 입력 인수로 전달 될 때 사용 되는 형식입니다.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a> CAtlMap:: KOUTARGTYPE

키가 output 인수로 반환 될 때 사용 되는 형식입니다.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a> 이상 지도:: Lookup

개체에서 키 또는 값을 조회 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
조회할 요소를 식별 하는 키를 지정 합니다.

*value*<br/>
조회 값을 받는 변수입니다.

### <a name="return-value"></a>반환 값

메서드의 첫 번째 형태는 키가 있는 경우 true를 반환 하 고 그렇지 않으면 false를 반환 합니다. 두 번째 및 세 번째 폼은 [Catlmap:: GetNext](#getnext) 에 대 한 호출의 위치로 사용할 수 있는 [cpair](#cpair_class) 에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

`Lookup` 는 해싱 알고리즘을 사용 하 여 지정 된 키 매개 변수와 정확히 일치 하는 키를 포함 하는 map 요소를 빠르게 찾습니다.

## <a name="catlmapoperator-"></a><a name="operator_at"></a> CAtlMap:: operator \[\]

새 요소를로 바꾸거나 추가 `CAtlMap` 합니다.

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
추가 하거나 바꿀 요소의 키입니다.

### <a name="return-value"></a>반환 값

지정 된 키와 연결 된 값에 대 한 참조를 반환 합니다.

### <a name="example"></a>예제

키가 이미 있으면 요소가 바뀝니다. 키가 없으면 새 요소가 추가 됩니다. 자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmaprehash"></a><a name="rehash"></a> Rehash::

이 메서드를 호출 하 여 `CAtlMap` 개체를 rehash 합니다.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>매개 변수

*nBins*<br/>
해시 테이블에 사용할 새 bin 수입니다. 설명에 대 한 [자세한 내용은 다음](#catlmap) 을 참조 하세요.

### <a name="remarks"></a>설명

*Nbins* 이 0 인 경우는 `CAtlMap` 맵의 요소 수와 최적 로드 설정에 따라 적절 한 수를 계산 합니다. 일반적으로 rehashing 프로세스는 자동 이지만, [:D isableautorehash](#disableautorehash) 가 호출 된 경우이 메서드는 필요한 크기 조정을 수행 합니다.

## <a name="catlmapremoveall"></a><a name="removeall"></a> RemoveAll::

개체에서 모든 요소를 제거 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>설명

`CAtlMap`요소를 저장 하는 데 사용 되는 메모리를 확보 하 여 개체를 지웁니다.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a> CAtlMap:: RemoveAtPos

개체의 지정 된 위치에서 요소를 제거 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="remarks"></a>설명

지정 된 위치에 저장 된 키/값 쌍을 제거 합니다. 요소를 저장 하는 데 사용 되는 메모리가 해제 됩니다. *Pos* 에서 참조 하는 위치는 유효 하지 않게 되 고 맵에서 다른 요소의 위치는 유효한 상태로 유지 되지만 반드시 동일한 순서를 유지할 필요는 없습니다.

## <a name="catlmapremovekey"></a><a name="removekey"></a> CAtlMap:: RemoveKey

키가 지정 된 경우이 메서드를 호출 하 여 개체에서 요소를 제거 `CAtlMap` 합니다.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
제거 하려는 요소 쌍에 해당 하는 키입니다.

### <a name="return-value"></a>반환 값

키를 찾아서 제거 하면 TRUE를 반환 하 고, 실패 하면 FALSE를 반환 합니다.

### <a name="example"></a>예제

자세한 내용은 [Catlmap:: catlmap](#catlmap)의 예제를 참조 하세요.

## <a name="catlmapsetat"></a><a name="setat"></a> , CAtlMap:: SetAt

지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
개체에 추가할 키 값 `CAtlMap` 입니다.

*value*<br/>
개체에 추가할 값 `CAtlMap` 입니다.

### <a name="return-value"></a>반환 값

개체에 있는 키/값 요소 쌍의 위치를 반환 합니다 `CAtlMap` .

### <a name="remarks"></a>설명

`SetAt` 일치 하는 키가 있는 경우 기존 요소를 바꿉니다. 키를 찾을 수 없는 경우 새 키/값 쌍이 만들어집니다.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a> SetOptimalLoad::

개체의 최적 로드를 설정 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>매개 변수

*fOptimalLoad*<br/>
최적 로드 비율입니다.

*fLoThreshold*<br/>
부하 비율의 하 한 임계값입니다.

*fHiThreshold*<br/>
로드 비율의 상한 임계값입니다.

*bRehashNow*<br/>
해시 테이블을 다시 계산 해야 하는지 여부를 나타내는 플래그입니다.

### <a name="remarks"></a>설명

이 메서드는 개체에 대 한 최적의 로드 값을 다시 정의 합니다 `CAtlMap` . 다양 한 매개 변수에 대 한 설명은 [catlmap:: CAtlMap](#catlmap) 을 참조 하세요. *BRehashNow* 가 true이 고 요소 수가 최소값과 최대값을 벗어나면 해시 테이블이 다시 계산 됩니다.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a> CAtlMap:: SetValueAt

개체의 지정 된 위치에 저장 된 값을 변경 하려면이 메서드를 호출 `CAtlMap` 합니다.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[GetNextAssoc](#getnextassoc) 또는 catlmap: [: getstartposition](#getstartposition)에 대 한 이전 호출에서 반환 된 position 카운터입니다.

*value*<br/>
개체에 추가할 값 `CAtlMap` 입니다.

### <a name="remarks"></a>설명

개체의 지정 된 위치에 저장 된 값 요소를 변경 합니다 `CAtlMap` .

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a> VINARGTYPE::

값이 입력 인수로 전달 될 때 사용 되는 형식입니다.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a> CAtlMap:: VOUTARGTYPE

값이 출력 인수로 전달 될 때 사용 되는 형식입니다.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a> CAtlMap:: CPair:: m_key

키 요소를 저장 하는 데이터 멤버입니다.

```cpp
const K m_key;
```

### <a name="parameters"></a>매개 변수

*K*<br/>
키 요소 형식입니다.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a> CAtlMap:: CPair:: m_value

Value 요소를 저장 하는 데이터 멤버입니다.

```cpp
V  m_value;
```

### <a name="parameters"></a>매개 변수

*V*<br/>
값 요소 형식입니다.

## <a name="see-also"></a>참고 항목

[Marquee 샘플](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

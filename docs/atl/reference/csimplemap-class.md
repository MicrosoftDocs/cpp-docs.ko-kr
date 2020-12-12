---
description: '자세히 알아보기: CSimpleMap 클래스'
title: CSimpleMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: 66640e3fcd325d59b82a10d98188a6fcd74ca79d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140623"
---
# <a name="csimplemap-class"></a>CSimpleMap 클래스

이 클래스는 간단한 매핑 배열을 지원 합니다.

## <a name="syntax"></a>구문

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>매개 변수

*TKey*<br/>
키 요소 형식입니다.

*TVal*<br/>
값 요소 형식입니다.

*Te Al*<br/>
형식 요소에 대 한 같음 테스트를 정의 하는 특성 개체 `T` 입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CSimpleMap: _ArrayElementType](#_arrayelementtype)|값 형식에 대 한 Typedef입니다.|
|[CSimpleMap: _ArrayKeyType](#_arraykeytype)|키 형식에 대 한 Typedef입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Csimplemap: CSimpleMap](#csimplemap)|생성자입니다.|
|[Csimplemap: ~ CSimpleMap](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleMap:: Add](#add)|지도 배열에 키 및 연결 된 값을 추가 합니다.|
|[CSimpleMap:: FindKey](#findkey)|특정 키를 찾습니다.|
|[CSimpleMap: FindVal](#findval)|특정 값을 찾습니다.|
|[CSimpleMap:: GetKeyAt](#getkeyat)|지정 된 키를 검색 합니다.|
|[CSimpleMap: GetSize](#getsize)|매핑 배열의 항목 수를 반환 합니다.|
|[CSimpleMap: GetValueAt](#getvalueat)|지정 된 값을 검색 합니다.|
|[CSimpleMap: Lookup](#lookup)|지정 된 키와 연결 된 값을 반환 합니다.|
|[CSimpleMap:: Remove](#remove)|키와 일치 하는 값을 제거 합니다.|
|[CSimpleMap::](#removeall)|모든 키와 값을 제거 합니다.|
|[CSimpleMap: RemoveAt](#removeat)|특정 키와 일치 하는 값을 제거 합니다.|
|[CSimpleMap::](#reverselookup)|지정 된 값과 연결 된 키를 반환 합니다.|
|[Csimpl\at:: SetAt](#setat)|지정 된 키와 연결 된 값을 설정 합니다.|
|[CSimpleMap::](#setatindex)|특정 키와 값을 설정 합니다.|

## <a name="remarks"></a>설명

`CSimpleMap` 지정 된 형식의 간단한 매핑 배열을 지원 `T` 하 여 키 요소 및 관련 값의 순서가 지정 되지 않은 배열을 관리 합니다.

매개 변수는 `TEqual` 형식의 두 요소에 대해 같음 함수를 정의 하는 방법을 제공 합니다 `T` . [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)와 유사한 클래스를 만들면 지정 된 배열에 대 한 같음 테스트의 동작을 변경할 수 있습니다. 예를 들어 포인터의 배열을 처리할 때 포인터가 참조 하는 값에 따라 같음을 정의 하는 것이 유용할 수 있습니다. 기본 구현에서는 **operator = = ()** 를 활용 합니다.

`CSimpleMap`및 [CSimpleArray](../../atl/reference/csimplearray-class.md) 모두 이전 ATL 릴리스와의 호환성을 위해 제공 되며, 더 완전 하 고 효율적인 컬렉션 구현은 [CAtlArray](../../atl/reference/catlarray-class.md) 및 [catlmap](../../atl/reference/catlmap-class.md)에서 제공 됩니다.

ATL 및 MFC의 다른 맵 컬렉션과 달리이 클래스는 단순 배열을 사용 하 여 구현 되 고 조회 검색에는 선형 검색이 필요 합니다. `CAtlMap` 배열에 많은 수의 요소가 포함 된 경우를 사용 해야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a> CSimpleMap:: Add

지도 배열에 키 및 연결 된 값을 추가 합니다.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키입니다.

*짧은*<br/>
연결 된 값입니다.

### <a name="return-value"></a>반환 값

키와 값이 성공적으로 추가 되었으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

각 키와 값 쌍을 추가 하면 매핑 배열 메모리를 해제 하 고 다시 할당 하 여 각에 대 한 데이터가 항상 연속적으로 저장 되도록 합니다. 즉, 두 번째 키 요소가 항상 메모리의 첫 번째 키 요소 바로 다음에 옵니다.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a> CSimpleMap: _ArrayElementType

키 형식에 대 한 typedef입니다.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a> CSimpleMap: _ArrayKeyType

값 형식에 대 한 typedef입니다.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a> Csimplemap: CSimpleMap

생성자입니다.

```
CSimpleMap();
```

### <a name="remarks"></a>설명

데이터 멤버를 초기화 합니다.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a> Csimplemap: ~ CSimpleMap

소멸자입니다.

```
~CSimpleMap();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="csimplemapfindkey"></a><a name="findkey"></a> CSimpleMap:: FindKey

특정 키를 찾습니다.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
검색할 키입니다.

### <a name="return-value"></a>반환 값

키가 있으면 해당 인덱스를 반환 하 고, 그렇지 않으면-1을 반환 합니다.

## <a name="csimplemapfindval"></a><a name="findval"></a> CSimpleMap: FindVal

특정 값을 찾습니다.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>매개 변수

*짧은*<br/>
검색할 값입니다.

### <a name="return-value"></a>반환 값

값이 발견 되 면 값의 인덱스를 반환 하 고, 그렇지 않으면-1을 반환 합니다.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a> CSimpleMap:: GetKeyAt

지정 된 인덱스에 있는 키를 검색 합니다.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
반환할 키의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 에서 참조 하는 키를 반환 합니다.

### <a name="remarks"></a>설명

*Nindex* 로 전달 되는 인덱스는 반환 값이 의미가 되려면 유효 해야 합니다.

## <a name="csimplemapgetsize"></a><a name="getsize"></a> CSimpleMap: GetSize

매핑 배열의 항목 수를 반환 합니다.

```
int GetSize() const;
```

### <a name="return-value"></a>반환 값

매핑 배열의 항목 수 (키 및 값은 한 항목)를 반환 합니다.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a> CSimpleMap: GetValueAt

특정 인덱스에서 값을 검색 합니다.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
반환할 값의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 에서 참조 하는 값을 반환 합니다.

### <a name="remarks"></a>설명

*Nindex* 로 전달 되는 인덱스는 반환 값이 의미가 되려면 유효 해야 합니다.

## <a name="csimplemaplookup"></a><a name="lookup"></a> CSimpleMap: Lookup

지정 된 키와 연결 된 값을 반환 합니다.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키입니다.

### <a name="return-value"></a>반환 값

연결 된 값을 반환 합니다. 일치 하는 키가 없는 경우 NULL이 반환 됩니다.

## <a name="csimplemapremove"></a><a name="remove"></a> CSimpleMap:: Remove

키와 일치 하는 값을 제거 합니다.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키입니다.

### <a name="return-value"></a>반환 값

키와 일치 하는 값이 성공적으로 제거 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="csimplemapremoveall"></a><a name="removeall"></a> CSimpleMap::

모든 키와 값을 제거 합니다.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>설명

매핑 배열 개체에서 모든 키와 값을 제거 합니다.

## <a name="csimplemapremoveat"></a><a name="removeat"></a> CSimpleMap: RemoveAt

지정 된 인덱스에서 키와 연결 된 값을 제거 합니다.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
제거할 키 및 연결 된 값의 인덱스입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고, 지정 된 인덱스가 잘못 된 인덱스인 경우 FALSE를 반환 합니다.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a> CSimpleMap::

지정 된 값과 연결 된 키를 반환 합니다.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>매개 변수

*짧은*<br/>
값입니다.

### <a name="return-value"></a>반환 값

연결 된 키를 반환 합니다. 일치 하는 키가 없는 경우 NULL이 반환 됩니다.

## <a name="csimplemapsetat"></a><a name="setat"></a> Csimpl\at:: SetAt

지정 된 키와 연결 된 값을 설정 합니다.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키입니다.

*짧은*<br/>
할당할 새 값입니다.

### <a name="return-value"></a>반환 값

키를 찾았지만 값이 성공적으로 변경 되었으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a> CSimpleMap::

지정 된 인덱스에 있는 키와 값을 설정 합니다.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
변경할 키 및 값 쌍을 참조 하는 인덱스입니다.

*key*<br/>
새 키입니다.

*짧은*<br/>
새 값입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 인덱스가 유효 하지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

*N 인덱스* 에 의해 가리키는 키와 값을 모두 업데이트 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

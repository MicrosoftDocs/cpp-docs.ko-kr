---
description: '자세히 알아보기: CRBMultiMap 클래스'
title: CRBMultiMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 8dfe644521cb7ec4135c5c1f71d36371ac1706ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141026"
---
# <a name="crbmultimap-class"></a>CRBMultiMap 클래스

이 클래스는 Red-Black 이진 트리를 사용 하 여 각 키를 둘 이상의 값에 연결할 수 있도록 하는 매핑 구조를 나타냅니다.

## <a name="syntax"></a>구문

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>매개 변수

*K*<br/>
키 요소 형식입니다.

*V*<br/>
값 요소 형식입니다.

*KTraits*<br/>
키 요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다. 자세한 내용은 [CElementTraits 클래스](../../atl/reference/celementtraits-class.md) 를 참조 하세요.

*VTraits*<br/>
값 요소를 복사 하거나 이동 하는 데 사용 되는 코드입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|생성자입니다.|
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|지정 된 키를 사용 하 여 첫 번째 요소의 위치를 확인 하려면이 메서드를 호출 합니다.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|지정 된 키와 연결 된 값을 가져오고 위치 값을 업데이트 하려면이 메서드를 호출 합니다.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|지정 된 키와 연결 된 요소를 가져오고 위치 값을 업데이트 하려면이 메서드를 호출 합니다.|
|[CRBMultiMap:: Insert](#insert)|지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.|
|[CRBMultiMap:: RemoveKey](#removekey)|지정 된 키에 대 한 키/값 요소를 모두 제거 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

`CRBMultiMap` 지정 된 형식의 매핑 배열을 지원 하 여 키 요소 및 값의 정렬 된 배열을 관리 합니다. [Crbmap](../../atl/reference/crbmap-class.md) 클래스와 달리 각 키를 둘 이상의 값에 연결할 수 있습니다.

키와 값으로 구성 된 요소는 [CRBMultiMap:: Insert](#insert) 메서드를 사용 하 여 이진 트리 구조에 저장 됩니다. [CRBMultiMap:: removekey](#removekey) 메서드를 사용 하 여 요소를 제거할 수 있으며,이 메서드는 지정 된 키와 일치 하는 모든 요소를 삭제 합니다.

[CRBTree:: Gethe Adposition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree:: GetNext](../../atl/reference/crbtree-class.md#getnext), [CRBTree:: GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)와 같은 메서드를 사용 하 여 트리를 트래버스할 수 있습니다. [CRBMultiMap:: FindFirstWithKey](#findfirstwithkey), [CRBMultiMap:: GetNextValueWithKey](#getnextvaluewithkey)및 [CRBMultiMap:: GetNextWithKey](#getnextwithkey) 메서드를 사용 하 여 키 당 잠재적으로 여러 값에 액세스할 수 있습니다. 이에 대 한 설명은 [CRBMultiMap:: CRBMultiMap](#crbmultimap) 의 예제를 참조 하세요.

*Ktraits* 및 *vtraits* 매개 변수는 요소를 복사 하거나 이동 하는 데 필요한 보충 코드를 포함 하는 특성 클래스입니다.

`CRBMultiMap` 는 Red-Black 알고리즘을 사용 하 여 이진 트리를 구현 하는 [CRBTree](../../atl/reference/crbtree-class.md)에서 파생 됩니다. 및에 대 한 대안 `CRBMultiMap` `CRBMap` 은 [catlmap](../../atl/reference/catlmap-class.md) 클래스에서 제공 됩니다. 적은 수의 요소만 저장 해야 하는 경우 [Csimplvalclass](../../atl/reference/csimplemap-class.md) 를 대신 사용 하는 것이 좋습니다.

다양 한 컬렉션 클래스와 해당 기능 및 성능 특성에 대 한 자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a> CRBMultiMap::CRBMultiMap

생성자입니다.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
블록의 크기입니다.

### <a name="remarks"></a>설명

*Nblocksize* 매개 변수는 새 요소가 필요할 때 할당 된 메모리 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다. 기본값은 한 번에 10 개의 요소에 대 한 공간을 할당 합니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a> CRBMultiMap:: ~ CRBMultiMap

소멸자입니다.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a> CRBMultiMap::FindFirstWithKey

지정 된 키를 사용 하 여 첫 번째 요소의 위치를 확인 하려면이 메서드를 호출 합니다.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
찾을 요소를 식별 하는 키를 지정 합니다.

### <a name="return-value"></a>반환 값

키가 있는 경우 첫 번째 키/값 요소의 위치를 반환 하 고, 그렇지 않으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

의 키에는 `CRBMultiMap` 하나 이상의 연결 된 값이 있을 수 있습니다. 이 메서드는 특정 키와 연결 된 첫 번째 값 (실제로 유일한 값일 수 있음)의 위치 값을 제공 합니다. 반환 된 위치 값은 [CRBMultiMap:: GetNextValueWithKey](#getnextvaluewithkey) 또는 [CRBMultiMap:: GetNextWithKey](#getnextwithkey) 와 함께 사용 하 여 값을 가져오고 위치를 업데이트할 수 있습니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[CRBMultiMap:: CRBMultiMap](#crbmultimap)의 예제를 참조 하세요.

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a> CRBMultiMap::GetNextValueWithKey

지정 된 키와 연결 된 값을 가져오고 위치 값을 업데이트 하려면이 메서드를 호출 합니다.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBMultiMap:: FindFirstWithKey](#findfirstwithkey) 또는 [CRBMultiMap:: GetNextWithKey](#getnextwithkey)에 대 한 호출 또는에 대 한 이전 호출로 얻은 position 값 `GetNextValueWithKey` 입니다.

*key*<br/>
찾을 요소를 식별 하는 키를 지정 합니다.

### <a name="return-value"></a>반환 값

지정 된 키와 연결 된 요소 쌍을 반환 합니다.

### <a name="remarks"></a>설명

위치 값은 키와 연결 된 다음 값을 가리키도록 업데이트 됩니다. 더 이상 값이 없으면 position 값이 NULL로 설정 됩니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[CRBMultiMap:: CRBMultiMap](#crbmultimap)의 예제를 참조 하세요.

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a> CRBMultiMap::GetNextWithKey

지정 된 키와 연결 된 요소를 가져오고 위치 값을 업데이트 하려면이 메서드를 호출 합니다.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBMultiMap:: FindFirstWithKey](#findfirstwithkey) 또는 [CRBMultiMap:: GetNextValueWithKey](#getnextvaluewithkey)에 대 한 호출 또는에 대 한 이전 호출로 얻은 position 값 `GetNextWithKey` 입니다.

*key*<br/>
찾을 요소를 식별 하는 키를 지정 합니다.

### <a name="return-value"></a>반환 값

지정 된 키와 연결 된 다음 [CRBTree:: CPair 클래스](crbtree-class.md#cpair_class) 요소를 반환 합니다.

### <a name="remarks"></a>설명

위치 값은 키와 연결 된 다음 값을 가리키도록 업데이트 됩니다. 더 이상 값이 없으면 position 값이 NULL로 설정 됩니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

## <a name="crbmultimapinsert"></a><a name="insert"></a> CRBMultiMap:: Insert

지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
개체에 추가할 키 값 `CRBMultiMap` 입니다.

*value*<br/>
`CRBMultiMap` *키* 와 연결 된 개체에 추가할 값입니다.

### <a name="return-value"></a>반환 값

개체에 있는 키/값 요소 쌍의 위치를 반환 합니다 `CRBMultiMap` .

### <a name="remarks"></a>설명

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[CRBMultiMap:: CRBMultiMap](#crbmultimap)의 예제를 참조 하세요.

## <a name="crbmultimapremovekey"></a><a name="removekey"></a> CRBMultiMap:: RemoveKey

지정 된 키에 대 한 키/값 요소를 모두 제거 하려면이 메서드를 호출 합니다.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
삭제할 요소를 식별 하는 키를 지정 합니다.

### <a name="return-value"></a>반환 값

지정 된 키와 연결 된 값의 수를 반환 합니다.

### <a name="remarks"></a>설명

`RemoveKey`*키와 일치 하* 는 키가 있는 키/값 요소를 모두 삭제 합니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[CRBMultiMap:: CRBMultiMap](#crbmultimap)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CRBTree 클래스](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 클래스](../../atl/reference/catlmap-class.md)<br/>
[CRBMap 클래스](../../atl/reference/crbmap-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

---
description: '자세한 정보: CRBMap 클래스'
title: CRBMap 클래스
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 55d96bfd2c7b043bdbdc4c1ee1f329c9b77b9ca9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141052"
---
# <a name="crbmap-class"></a>CRBMap 클래스

이 클래스는 Red-Black 이진 트리를 사용 하 여 매핑 구조를 나타냅니다.

## <a name="syntax"></a>구문

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap:: CRBMap](#crbmap)|생성자입니다.|
|[CRBMap:: ~ CRBMap](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRBMap:: Lookup](#lookup)|개체에서 키 또는 값을 조회 하려면이 메서드를 호출 `CRBMap` 합니다.|
|[CRBMap:: RemoveKey](#removekey)|키가 지정 된 경우이 메서드를 호출 하 여 개체에서 요소를 제거 `CRBMap` 합니다.|
|[CRBMap:: SetAt](#setat)|지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

`CRBMap` 지정 된 형식의 매핑 배열을 지원 하 여 키 요소 및 관련 값의 정렬 된 배열을 관리 합니다. 각 키에는 연결 된 값이 하나만 있을 수 있습니다. 키와 값으로 구성 된 요소는 [Crbmap:: SetAt](#setat) 메서드를 사용 하 여 이진 트리 구조에 저장 됩니다. 요소는 지정 된 키 값이 있는 요소를 삭제 하는 [Crbmap:: RemoveKey](#removekey) 메서드를 사용 하 여 제거할 수 있습니다.

[CRBTree:: Gethe Adposition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree:: GetNext](../../atl/reference/crbtree-class.md#getnext), [CRBTree:: GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)와 같은 메서드를 사용 하 여 트리를 트래버스할 수 있습니다.

*Ktraits* 및 *vtraits* 매개 변수는 요소를 복사 하거나 이동 하는 데 필요한 보충 코드를 포함 하는 특성 클래스입니다.

`CRBMap` 는 Red-Black 알고리즘을 사용 하 여 이진 트리를 구현 하는 [CRBTree](../../atl/reference/crbtree-class.md)에서 파생 됩니다. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) 는 각 키에 대해 여러 값을 허용 하는 변형입니다. 에서 파생 되므로 `CRBTree` 와 많은 기능을 공유 `CRBMap` 합니다.

및 둘 다에 대 한 대체 항목 `CRBMap` `CRBMultiMap` 은 [](../../atl/reference/catlmap-class.md) 지 수 클래스에서 제공 됩니다. 적은 수의 요소만 저장 해야 하는 경우 [Csimplvalclass](../../atl/reference/csimplemap-class.md) 를 대신 사용 하는 것이 좋습니다.

다양 한 컬렉션 클래스와 해당 기능 및 성능 특성에 대 한 자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="crbmapcrbmap"></a><a name="crbmap"></a> CRBMap:: CRBMap

생성자입니다.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>매개 변수

*nBlockSize*<br/>
블록의 크기입니다.

### <a name="remarks"></a>설명

*Nblocksize* 매개 변수는 새 요소가 필요할 때 할당 된 메모리 양을 측정 한 것입니다. 블록 크기가 클수록 메모리 할당 루틴에 대 한 호출이 줄어들지만 더 많은 리소스를 사용 합니다. 기본값은 한 번에 10 개의 요소에 대 한 공간을 할당 합니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a> CRBMap:: ~ CRBMap

소멸자입니다.

```
~CRBMap() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

## <a name="crbmaplookup"></a><a name="lookup"></a> CRBMap:: Lookup

개체에서 키 또는 값을 조회 하려면이 메서드를 호출 `CRBMap` 합니다.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
조회할 요소를 식별 하는 키를 지정 합니다.

*value*<br/>
조회 값을 받는 변수입니다.

### <a name="return-value"></a>반환 값

메서드의 첫 번째 형태는 키가 있는 경우 true를 반환 하 고 그렇지 않으면 false를 반환 합니다. 두 번째와 세 번째 폼은 [Cpair](crbtree-class.md#cpair_class)에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a> CRBMap:: RemoveKey

키가 지정 된 경우이 메서드를 호출 하 여 개체에서 요소를 제거 `CRBMap` 합니다.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
제거 하려는 요소 쌍에 해당 하는 키입니다.

### <a name="return-value"></a>반환 값

키를 찾아서 제거 하면 true를 반환 하 고, 실패 하면 false를 반환 합니다.

### <a name="remarks"></a>설명

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a> CRBMap:: SetAt

지도에 요소 쌍을 삽입 하려면이 메서드를 호출 합니다.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>매개 변수

*key*<br/>
개체에 추가할 키 값 `CRBMap` 입니다.

*value*<br/>
개체에 추가할 값 `CRBMap` 입니다.

### <a name="return-value"></a>반환 값

개체에 있는 키/값 요소 쌍의 위치를 반환 합니다 `CRBMap` .

### <a name="remarks"></a>설명

`SetAt` 일치 하는 키가 있는 경우 기존 요소를 바꿉니다. 키를 찾을 수 없는 경우 새 키/값 쌍이 만들어집니다.

사용 가능한 다른 방법에 대 한 자세한 내용은 기본 클래스 [CRBTree](../../atl/reference/crbtree-class.md) 설명서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>참고 항목

[CRBTree 클래스](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 클래스](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap 클래스](../../atl/reference/crbmultimap-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

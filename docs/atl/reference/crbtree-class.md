---
description: '자세히 알아보기: CRBTree 클래스'
title: CRBTree 클래스
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 3c45c8b05429ba75905912d76f87605a07ff49e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140974"
---
# <a name="crbtree-class"></a>CRBTree 클래스

이 클래스는 Red-Black 트리를 만들고 활용 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
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

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|키가 입력 인수로 전달 될 때 사용 되는 형식입니다.|
|[CRBTree:: KOUTARGTYPE](#koutargtype)|키가 output 인수로 반환 될 때 사용 되는 형식입니다.|
|[CRBTree::VINARGTYPE](#vinargtype)|값이 입력 인수로 전달 될 때 사용 되는 형식입니다.|
|[CRBTree:: VOUTARGTYPE](#voutargtype)|값이 출력 인수로 전달 될 때 사용 되는 형식입니다.|

### <a name="public-classes"></a>public 클래스

|Name|설명|
|----------|-----------------|
|[CRBTree:: CPair 클래스](#cpair_class)|키 및 값 요소를 포함 하는 클래스입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRBTree:: ~ CRBTree](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)|이 메서드를 호출 하 여 사용 가능한 다음 키를 사용 하는 요소의 위치를 찾습니다.|
|[CRBTree:: GetAt](#getat)|트리의 지정 된 위치에 있는 요소를 가져오려면이 메서드를 호출 합니다.|
|[CRBTree:: GetCount](#getcount)|트리의 요소 수를 가져오려면이 메서드를 호출 합니다.|
|[CRBTree:: Geadposition](#getheadposition)|트리 헤드의 요소에 대 한 위치 값을 가져오려면이 메서드를 호출 합니다.|
|[CRBTree:: GetKeyAt](#getkeyat)|트리의 지정 된 위치에서 키를 가져오려면이 메서드를 호출 합니다.|
|[CRBTree:: GetNext](#getnext)|개체에 저장 된 요소에 대 한 포인터를 가져오고 `CRBTree` 위치를 다음 요소로 이동 하려면이 메서드를 호출 합니다.|
|[CRBTree::GetNextAssoc](#getnextassoc)|맵에 저장 된 요소의 키 및 값을 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.|
|[CRBTree::GetNextKey](#getnextkey)|트리에 저장 된 요소의 키를 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.|
|[CRBTree::GetNextValue](#getnextvalue)|트리에 저장 된 요소의 값을 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.|
|[CRBTree:: GetPrev](#getprev)|개체에 저장 된 요소에 대 한 포인터를 가져온 `CRBTree` 다음 위치를 이전 요소로 업데이트 하려면이 메서드를 호출 합니다.|
|[CRBTree::GetTailPosition](#gettailposition)|트리의 꼬리에서 요소에 대 한 위치 값을 가져오려면이 메서드를 호출 합니다.|
|[CRBTree:: GetValueAt](#getvalueat)|개체의 지정 된 위치에 저장 된 값을 검색 하려면이 메서드를 호출 `CRBTree` 합니다.|
|[CRBTree:: IsEmpty](#isempty)|빈 트리 개체를 테스트 하려면이 메서드를 호출 합니다.|
|[CRBTree:: RemoveAll](#removeall)|개체에서 모든 요소를 제거 하려면이 메서드를 호출 `CRBTree` 합니다.|
|[CRBTree:: RemoveAt](#removeat)|개체의 지정 된 위치에서 요소를 제거 하려면이 메서드를 호출 `CRBTree` 합니다.|
|[CRBTree:: SetValueAt](#setvalueat)|개체의 지정 된 위치에 저장 된 값을 변경 하려면이 메서드를 호출 `CRBTree` 합니다.|

## <a name="remarks"></a>설명

Red-Black 트리는 노드당 추가 비트 정보를 사용 하는 이진 검색 트리로, 트리 높이가 불균형 하 게 크게 증가 하 고 성능에 영향을 줄 수 있도록 하기 위해 노드당 추가 비트 정보를 사용 합니다.

이 템플릿 클래스는 [Crbmap](../../atl/reference/crbmap-class.md) 및 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)에서 사용 하도록 설계 되었습니다. 이러한 파생 클래스를 구성 하는 메서드는 대부분에서 제공 됩니다 `CRBTree` .

다양 한 컬렉션 클래스와 해당 기능 및 성능 특성에 대 한 자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a> CRBTree:: CPair 클래스

키 및 값 요소를 포함 하는 클래스입니다.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>설명

이 클래스는 [CRBTree:: GetAt](#getat), [CRBTree:: GetNext](#getnext)및 [CRBTree:: getprev](#getprev) 메서드에서 트리 구조에 저장 된 키 및 값 요소에 액세스 하는 데 사용 됩니다.

멤버는 다음과 같습니다.

|데이터 멤버|설명|
|-|-|
|`m_key`|키 요소를 저장 하는 데이터 멤버입니다.|
|`m_value`|Value 요소를 저장 하는 데이터 멤버입니다.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a> CRBTree:: ~ CRBTree

소멸자입니다.

```
~CRBTree() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다. [CRBTree:: RemoveAll](#removeall) 를 호출 하 여 모든 요소를 삭제 합니다.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a> CRBTree:: FindFirstKeyAfter

이 메서드를 호출 하 여 사용 가능한 다음 키를 사용 하는 요소의 위치를 찾습니다.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
키 값입니다.

### <a name="return-value"></a>반환 값

사용 가능한 다음 키를 사용 하는 요소의 위치 값을 반환 합니다. 요소가 더 이상 없으면 NULL이 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하면 위치 값을 미리 계산 하지 않고도 트리를 쉽게 트래버스할 수 있습니다.

## <a name="crbtreegetat"></a><a name="getat"></a> CRBTree:: GetAt

트리의 지정 된 위치에 있는 요소를 가져오려면이 메서드를 호출 합니다.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
위치 값입니다.

*key*<br/>
키를 받는 변수입니다.

*value*<br/>
값을 받는 변수입니다.

### <a name="return-value"></a>반환 값

처음 두 폼은 [Cpair](#cpair_class)에 대 한 포인터를 반환 합니다. 세 번째 폼은 지정 된 위치에 대 한 키 및 값을 가져옵니다.

### <a name="remarks"></a>설명

Position 값은 [CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: GetTailPosition](#gettailposition)와 같은 메서드를 호출 하 여 이전에 결정할 수 있습니다.

디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

## <a name="crbtreegetcount"></a><a name="getcount"></a> CRBTree:: GetCount

트리의 요소 수를 가져오려면이 메서드를 호출 합니다.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>반환 값

트리에 저장 된 요소 수 (각 키/값 쌍은 하나의 요소)를 반환 합니다.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a> CRBTree:: Geadposition

트리 헤드의 요소에 대 한 위치 값을 가져오려면이 메서드를 호출 합니다.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>반환 값

트리 헤드의 요소에 대 한 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

에서 반환 되는 값은 `GetHeadPosition` [CRBTree:: GetKeyAt](#getkeyat) 또는 [CRBTree:: GetNext](#getnext) 와 같은 메서드와 함께 사용 하 여 트리를 트래버스 하 고 값을 검색할 수 있습니다.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a> CRBTree:: GetKeyAt

트리의 지정 된 위치에서 키를 가져오려면이 메서드를 호출 합니다.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
위치 값입니다.

### <a name="return-value"></a>반환 값

트리의 위치 *pos* 에 저장 된 키를 반환 합니다.

### <a name="remarks"></a>설명

*Pos* 가 유효한 위치 값이 아닌 경우 결과를 예측할 수 없습니다. 디버그 빌드에서는 *pos* 가 NULL 인 경우 어설션 오류가 발생 합니다.

## <a name="crbtreegetnext"></a><a name="getnext"></a> CRBTree:: GetNext

개체에 저장 된 요소에 대 한 포인터를 가져오고 `CRBTree` 위치를 다음 요소로 이동 하려면이 메서드를 호출 합니다.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

트리의 다음 [Cpair](#cpair_class) 값에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

*Pos* position 카운터는 각 호출 후에 업데이트 됩니다. 검색 된 요소가 트리에서 마지막 이면 *pos* 가 NULL로 설정 됩니다.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a> CRBTree::GetNextAssoc

맵에 저장 된 요소의 키 및 값을 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

*key*<br/>
트리 키의 형식을 지정 하는 템플릿 매개 변수입니다.

*value*<br/>
트리 값의 형식을 지정 하는 템플릿 매개 변수입니다.

### <a name="remarks"></a>설명

*Pos* position 카운터는 각 호출 후에 업데이트 됩니다. 검색 된 요소가 트리에서 마지막 이면 *pos* 가 NULL로 설정 됩니다.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a> CRBTree::GetNextKey

트리에 저장 된 요소의 키를 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

트리의 다음 키에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

현재 위치 카운터, *pos* 를 업데이트 합니다. 트리에 항목이 더 이상 없으면 position 카운터가 NULL로 설정 됩니다.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a> CRBTree::GetNextValue

트리에 저장 된 요소의 값을 가져오고 다음 요소로 이동 하려면이 메서드를 호출 합니다.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

트리의 다음 값에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

현재 위치 카운터, *pos* 를 업데이트 합니다. 트리에 항목이 더 이상 없으면 position 카운터가 NULL로 설정 됩니다.

## <a name="crbtreegetprev"></a><a name="getprev"></a> CRBTree:: GetPrev

개체에 저장 된 요소에 대 한 포인터를 가져온 `CRBTree` 다음 위치를 이전 요소로 업데이트 하려면이 메서드를 호출 합니다.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

트리에 저장 된 이전 [Cpair](#cpair_class) 값에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

현재 위치 카운터, *pos* 를 업데이트 합니다. 트리에 항목이 더 이상 없으면 position 카운터가 NULL로 설정 됩니다.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a> CRBTree::GetTailPosition

트리의 꼬리에서 요소에 대 한 위치 값을 가져오려면이 메서드를 호출 합니다.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>반환 값

트리의 꼬리 부분에 있는 요소에 대 한 위치 값을 반환 합니다.

### <a name="remarks"></a>설명

에서 반환 되는 값은 `GetTailPosition` [CRBTree:: GetKeyAt](#getkeyat) 또는 [CRBTree:: getprev](#getprev) 와 같은 메서드와 함께 사용 하 여 트리를 트래버스 하 고 값을 검색할 수 있습니다.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a> CRBTree:: GetValueAt

개체의 지정 된 위치에 저장 된 값을 검색 하려면이 메서드를 호출 `CRBTree` 합니다.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="return-value"></a>반환 값

개체의 지정 된 위치에 저장 된 값에 대 한 참조를 반환 합니다 `CRBTree` .

## <a name="crbtreeisempty"></a><a name="isempty"></a> CRBTree:: IsEmpty

빈 트리 개체를 테스트 하려면이 메서드를 호출 합니다.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>반환 값

트리가 비어 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a> CRBTree::KINARGTYPE

키가 입력 인수로 전달 될 때 사용 되는 형식입니다.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a> CRBTree:: KOUTARGTYPE

키가 output 인수로 반환 될 때 사용 되는 형식입니다.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a> CRBTree:: RemoveAll

개체에서 모든 요소를 제거 하려면이 메서드를 호출 `CRBTree` 합니다.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>설명

`CRBTree`요소를 저장 하는 데 사용 되는 메모리를 확보 하 여 개체를 지웁니다.

## <a name="crbtreeremoveat"></a><a name="removeat"></a> CRBTree:: RemoveAt

개체의 지정 된 위치에서 요소를 제거 하려면이 메서드를 호출 `CRBTree` 합니다.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

### <a name="remarks"></a>설명

지정 된 위치에 저장 된 키/값 쌍을 제거 합니다. 요소를 저장 하는 데 사용 되는 메모리가 해제 됩니다. *Pos* 에서 참조 하는 위치는 유효 하지 않게 되 고 트리에서 다른 요소의 위치는 유효한 상태로 유지 되지만 반드시 동일한 순서를 유지할 필요는 없습니다.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a> CRBTree:: SetValueAt

개체의 지정 된 위치에 저장 된 값을 변경 하려면이 메서드를 호출 `CRBTree` 합니다.

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
[CRBTree:: Gethe Adposition](#getheadposition) 또는 [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter)와 같은 메서드에 대 한 이전 호출에서 반환 된 position 카운터입니다.

*value*<br/>
개체에 추가할 값 `CRBTree` 입니다.

### <a name="remarks"></a>설명

개체의 지정 된 위치에 저장 된 값 요소를 변경 합니다 `CRBTree` .

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a> CRBTree::VINARGTYPE

값이 입력 인수로 전달 될 때 사용 되는 형식입니다.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a> CRBTree:: VOUTARGTYPE

값이 출력 인수로 전달 될 때 사용 되는 형식입니다.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

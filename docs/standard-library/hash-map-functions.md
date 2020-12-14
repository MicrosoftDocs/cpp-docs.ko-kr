---
description: '&lt;Hash_map 함수에 대해 자세히 알아보세요. &gt;'
title: '&lt;hash_map&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 50f9150bc79a3ffdc586ba420d6e3dc280784767
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231903"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt; 함수

[스왑을](#swap)\
[swap(hash_map)](#swap_hash_map)

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a> swap (hash_map)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_map 클래스](../standard-library/unordered-map-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_map의 요소를 교환합니다.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
해당 요소를 *왼쪽* 맵의 시그니처와 교환할 hash_map입니다.

*비어*\
지도 *오른쪽* 의 요소와 교환할 요소를 포함 하는 hash_map입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수 `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*)을 실행하기 위해 컨테이너 클래스 hash_map에서 특수화된 알고리즘입니다. 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 헤더 파일에서 템플릿 함수, **템플릿 \<class T> void Swap (t&, t&)** 의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

## <a name="swap"></a><a name="swap"></a> 스왑을

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. 다른 방법은 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)입니다.

두 hash_multimap의 요소를 교환합니다.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
해당 요소를 *왼쪽* 맵의 시그니처와 교환할 hash_multimap입니다.

*비어*\
지도 *오른쪽* 의 요소와 교환할 요소를 포함 하는 hash_multimap입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수 `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`을 실행하기 위해 컨테이너 클래스 hash_multimap에서 특수화된 알고리즘입니다. 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 헤더 파일에서 템플릿 함수, **템플릿 \<class T> void Swap (t&, t&)** 의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

## <a name="see-also"></a>참고 항목

[<hash_map>](../standard-library/hash-map.md)

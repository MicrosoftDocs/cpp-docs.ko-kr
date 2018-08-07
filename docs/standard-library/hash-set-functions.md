---
title: '&lt;hash_set&gt; 함수 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: ad8041ff6a4abab84272d2bbbdee290bfce4eff6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961879"
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set&gt; 함수

|||
|-|-|
|[swap](#swap)|[swap(hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  swap

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_set의 요소를 교환합니다.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽* 교환할 요소를 제공 하는 hash_set 또는 hash_set의와 교환할 요소가 들어 있는 hash_set *왼쪽*합니다.

*왼쪽* 요소를 교환할 hash_set의 hash_set *오른쪽*합니다.

### <a name="remarks"></a>설명

합니다 `swap` 템플릿 함수는 멤버 함수를 실행 하는 컨테이너 클래스 hash_set에서 특수화 된 알고리즘 `left.` [스왑](../standard-library/hash-set-class.md#swap)(`right`). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스 내 템플릿 함수의 일반 버전

**template \<class T> void swap(T&, T&),**

는 할당을 통해 작동하며 속도가 느린 작업입니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예

`swap`의 템플릿 버전 사용 예제를 보려면 멤버 클래스 [hash_set::swap](../standard-library/hash-set-class.md#swap)에 대한 코드 예제를 참조하세요.

## <a name="swap_hash_multiset"></a>  swap(hash_multiset)

> [!NOTE]
> 이 API는 더 이상 사용되지 않습니다. [unordered_set 클래스](../standard-library/unordered-set-class.md)를 대신 사용하는 것이 좋습니다.

두 hash_multiset의 요소를 교환합니다.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽* 교환할 요소를 제공 하는 hash_multiset 또는 hash_multiset과 교환할 요소가 들어 있는 hash_multiset *왼쪽*합니다.

*왼쪽* 요소가 들어 있는 hash_multiset과 교환할 hash_multiset *오른쪽*합니다.

### <a name="remarks"></a>설명

합니다 `swap` 템플릿 함수는 멤버 함수를 실행 하려면 컨테이너 클래스 hash_multiset에서 특수화 된 알고리즘 `left.` [스왑](../standard-library/hash-multiset-class.md#swap)(`right`). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스 내 템플릿 함수의 일반 버전

**template \<class T> void swap(T&, T&),**

는 할당을 통해 작동하며 속도가 느린 작업입니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예

`swap`의 템플릿 버전 사용 예제를 보려면 멤버 클래스 [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap)에 대한 코드 예제를 참조하세요.

## <a name="see-also"></a>참고자료

[<hash_set>](../standard-library/hash-set.md)<br/>

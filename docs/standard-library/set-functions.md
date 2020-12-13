---
description: '자세히 알아보기: &lt; 함수 설정 &gt;'
title: '&lt;set&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 14f8eac3f725f88d98cdba133dace06993e5c089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154138"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt; 함수

## <a name="swap-map"></a><a name="swap"></a> swap (map)

두 set의 요소를 교환합니다.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 집합 이거나, *왼쪽* 집합의 요소와 교환할 요소를 포함 하는 집합입니다.

*비어*\
설정 된 *오른쪽* 의 요소와 교환할 요소를 포함 하는 집합입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수 `left.` [swap](../standard-library/set-class.md#swap)()을 실행 하기 위해 컨테이너 클래스 집합에서 특수화 된 알고리즘입니다 `right` . 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스 내 템플릿 함수의 일반 버전

`template`\< **classT**> **void swap**( **t&**, **t&**)

는 할당을 통해 작동하며 속도가 느린 작업입니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

`swap`의 템플릿 버전 사용 예제를 보려면 구성원 클래스 [set::swap](../standard-library/set-class.md#swap)에 대한 코드 예제를 참조하세요.

## <a name="swap-multiset"></a><a name="swap_multiset"></a> 교환 (multiset)

두 multiset의 요소를 교환합니다.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 multiset 이거나, 해당 요소를 multiset *왼쪽* 의 해당 요소와 교환할 multiset입니다.

*비어*\
Multiset *오른쪽* 의 요소와 교환할 요소를 포함 하는 multiset입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수 `left.` [swap](../standard-library/multiset-class.md#swap)()을 실행 하기 위해 컨테이너 클래스 multiset에서 특수화 된 알고리즘입니다 `right` . 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스 내 템플릿 함수의 일반 버전

`template`\< **classT**> **void swap**( **t&**, **t&**)

는 할당을 통해 작동하며 속도가 느린 작업입니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

`swap`의 템플릿 버전 사용 예제를 보려면 구성원 클래스 [multiset::swap](../standard-library/multiset-class.md#swap)에 대한 코드 예제를 참조하세요.

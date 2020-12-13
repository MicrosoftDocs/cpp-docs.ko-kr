---
description: '자세한 정보: &lt; map &gt; 함수'
title: '&lt;map&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: dded58c4af44bca08a5cb9e2cd0436974f48f6c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149515"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 함수

## <a name="swap-map"></a><a name="swap_multimap"></a> swap (map)

두 map의 요소를 교환합니다.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 맵 또는 요소를 *왼쪽* 맵과 교환할 지도입니다.

*비어*\
지도 *오른쪽* 의 요소와 교환할 요소를 포함 하는 맵입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수를 실행 하기 위해 컨테이너 클래스 맵에서 특수화 된 알고리즘입니다 `left` .[ swap](../standard-library/map-class.md#swap)( `right` ). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. **`template`** \< **class T**> 알고리즘 클래스에서 템플릿 함수 **void swap**( **t&**, **t&**)의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

`swap`의 템플릿 버전을 사용하는 예제는 멤버 함수 [map::swap](../standard-library/map-class.md#swap)에 대한 코드 예제를 참조하세요.

## <a name="swap-multimap"></a><a name="swap"></a> swap (multimap)

두 multimap의 요소를 교환합니다.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 multimap 이거나, multimap *left* 의 요소와 교환할 요소를 포함 하는 multimap입니다.

*비어*\
Multimap *right* 의 요소와 교환할 요소를 포함 하는 multimap입니다.

### <a name="remarks"></a>설명

템플릿 함수는 멤버 함수를 실행 하기 위해 컨테이너 클래스 multimap에서 실행 되는 컨테이너 클래스 맵에서 특수화 된 알고리즘입니다 `left` .[ swap](../standard-library/multimap-class.md#swap) ( `right` ). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 함수를 호출할 때 템플릿이 고유하게 일치하지 않는 방식으로 템플릿 함수가 오버로드되면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. **`template`** \< **class T**> 알고리즘 클래스에서 템플릿 함수 **void swap**( **t&**, **t&**)의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

`swap`의 템플릿 버전을 사용하는 예제는 멤버 함수 [multimap::swap](../standard-library/multimap-class.md#swap)에 대한 코드 예제를 참조하세요.

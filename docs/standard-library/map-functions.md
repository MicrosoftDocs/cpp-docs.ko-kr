---
title: '&lt;map&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883964"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 함수

## <a name="swap_multimap"></a>swap (map)

두 map의 요소를 교환합니다.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 맵 또는 요소를 *왼쪽*맵과 교환할 지도입니다.

*왼쪽*\
지도 *오른쪽*의 요소와 교환할 요소를 포함 하는 맵입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left`멤버 함수를 실행 하기 위해 컨테이너 클래스 맵에서 특수화 된 알고리즘입니다. [swap](../standard-library/map-class.md#swap)(`right`). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 템플릿 함수가 이러한 방식으로 오버로드되어 함수를 호출할 때 템플릿이 고유하게 일치하지 않으면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스에서 템플릿 함수, **템플릿** \< **클래스 t**> **void swap**( **t &** , **t &** )의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

[의 템플릿 버전을 사용하는 예제는 멤버 함수 ](../standard-library/map-class.md#swap)map::swap`swap`에 대한 코드 예제를 참조하세요.

## <a name="swap"></a>swap (multimap)

두 multimap의 요소를 교환합니다.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
교환할 요소를 제공 하는 multimap 이거나, multimap *left*의 요소와 교환할 요소를 포함 하는 multimap입니다.

*왼쪽*\
Multimap *right*의 요소와 교환할 요소를 포함 하는 multimap입니다.

### <a name="remarks"></a>설명

템플릿 함수는 `left`멤버 함수를 실행 하기 위해 컨테이너 클래스 맵에서 특수화 된 알고리즘입니다. [swap](../standard-library/multimap-class.md#swap) (`right`). 이 함수는 컴파일러에서 지정하는 함수 템플릿의 부분 순서 인스턴스입니다. 템플릿 함수가 이러한 방식으로 오버로드되어 함수를 호출할 때 템플릿이 고유하게 일치하지 않으면 컴파일러는 템플릿 함수의 가장 특수화된 버전을 선택합니다. 알고리즘 클래스에서 템플릿 함수, **템플릿** \< **클래스 t**> **void swap**( **t &** , **t &** )의 일반 버전은 할당에 따라 작동 하 고 속도가 느립니다. 각 컨테이너의 특수화된 버전은 컨테이너 클래스의 내부 표현을 사용할 수 있으므로 속도가 훨씬 빠릅니다.

### <a name="example"></a>예제

[의 템플릿 버전을 사용하는 예제는 멤버 함수 ](../standard-library/multimap-class.md#swap)multimap::swap`swap`에 대한 코드 예제를 참조하세요.

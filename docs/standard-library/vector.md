---
description: '자세한 정보: &lt; 벡터&gt;'
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 1f787afb00a3f94ba6b5148fe064badbc5d373ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187860"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

컨테이너 클래스 템플릿 벡터와 여러 지원 템플릿을 정의 합니다.

`vector`는 선형 시퀀스에서 지정된 유형의 요소를 구성하는 컨테이너입니다. 이 컨테이너를 사용하면 모든 요소에 빠르게 임의 액세스할 수 있으며 시퀀스에 대한 동적 추가와 제거를 수행할 수 있습니다. 임의 액세스 성능이 가장 중요할 때는 `vector`를 시퀀스에 대한 기본 컨테이너로 사용합니다.

> [!NOTE]
> \<vector>또한 라이브러리는 문을 사용 `#include <initializer_list>` 합니다.

`vector` 클래스에 대한 자세한 내용은 [vector 클래스](../standard-library/vector-class.md)를 참조하세요. 특수화에 대 한 자세한 내용은 `vector<bool>` [vector \<bool> 클래스](../standard-library/vector-bool-class.md)를 참조 하세요.

## <a name="syntax"></a>구문

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>매개 변수

*입력할*\
벡터에 저장되는 데이터 형식에 대한 템플릿 매개 변수입니다.

*할당자*\
메모리 할당 및 할당 취소를 수행하는 저장된 할당자 개체에 대한 템플릿 매개 변수입니다.

*비어*\
비교 작업의 첫 번째(왼쪽) 벡터입니다.

*오른쪽*\
비교 작업의 두 번째(오른쪽) 벡터입니다.

## <a name="members"></a>멤버

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자! =](../standard-library/vector-operators.md#op_neq)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체와 같지 않은지 테스트합니다.|
|[연산자<](../standard-library/vector-operators.md#op_lt)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체보다 작은지 테스트합니다.|
|[연산자\<=](../standard-library/vector-operators.md#op_gt_eq)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체보다 작거나 같은지 테스트합니다.|
|[연산자 = =](../standard-library/vector-operators.md#op_eq_eq)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체와 같은지 테스트합니다.|
|[연산자>](../standard-library/vector-operators.md#op_gt)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체보다 큰지 테스트합니다.|
|[연산자>=](../standard-library/vector-operators.md#op_gt_eq)|연산자의 왼쪽에 있는 벡터 개체가 오른쪽에 있는 벡터 개체보다 크거나 같은지 테스트합니다.|

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[vector 클래스](../standard-library/vector-class.md)|선형 정렬에서 지정된 형식의 요소를 정렬하고 모든 요소에 대한 빠른 임의 액세스를 허용하는 시퀀스 컨테이너의 클래스 템플릿입니다.|

### <a name="specializations"></a>특수화

|Name|설명|
|-|-|
|hash|벡터의 해시를 반환 합니다.|
|[vector \<bool> 클래스](../standard-library/vector-bool-class.md)|**`bool`** 특수화에서 사용 하는 기본 형식에 대 한 할당자를 포함 하는 형식의 요소에 대 한 클래스 템플릿 벡터의 전체 특수화입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<vector>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)

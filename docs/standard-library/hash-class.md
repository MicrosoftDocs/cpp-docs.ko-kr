---
description: '자세히 알아보기: hash 클래스'
title: hash 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: 124740486482722ec065c01f0d71e9bbc413f8f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324163"
---
# <a name="hash-class"></a>hash 클래스

값에 대한 해시 코드를 계산합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>설명

함수 개체는 *Ty* 형식의 값을 인덱스 값의 분포에 매핑하는 데 적합한 해시 함수를 정의합니다. 멤버는 `operator()` 클래스 템플릿,, 및에서 사용 하기에 적합 한 *val* 의 해시 코드를 반환 합니다 `unordered_map` `unordered_multimap` `unordered_set` `unordered_multiset` . 표준 라이브러리는 기본 형식에 대한 특수화를 제공합니다. *Ty* 는 포인터 형식 및 열거형 형식을 비롯한 스칼라 형식일 수 있습니다. 도한 라이브러리 형식 `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant` 및 `vector<bool>`에 대한 특수화가 있습니다.

## <a name="example"></a>예제

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>요구 사항

**헤더:**\<functional>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<unordered_map>](../standard-library/unordered-map.md)\
[unordered_multimap 클래스](../standard-library/unordered-multimap-class.md)\
[unordered_multiset 클래스](../standard-library/unordered-multiset-class.md)\
[<unordered_set>](../standard-library/unordered-set.md)

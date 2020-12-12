---
description: '자세한 정보: vector &lt; bool &gt; :: reference:: flip'
title: vector&lt;bool&gt;::reference::flip
ms.date: 11/04/2016
f1_keywords:
- vector/std::vector<bool>::reference::flip
helpviewer_keywords:
- reference::flip method
ms.assetid: ef940365-cbe4-4a87-a3e2-1f3cfa357e29
ms.openlocfilehash: fc07fada718e440d6e2ae76c75e7e5b24c6644d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280419"
---
# <a name="vectorltboolgtreferenceflip"></a>vector&lt;bool&gt;::reference::flip

참조 된 [vector \<bool> ](../standard-library/vector-bool-class.md) 요소의 부울 값을 반전 합니다.

## <a name="syntax"></a>구문

```cpp
void flip();
```

## <a name="example"></a>예제

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="output"></a>출력

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

## <a name="requirements"></a>요구 사항

**헤더:**\<vector>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[vector \<bool> :: Reference 클래스](../standard-library/vector-bool-reference-class.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)

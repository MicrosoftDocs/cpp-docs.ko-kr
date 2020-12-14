---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4456'
title: 컴파일러 경고 (수준 4) C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: f066de07b0c6bf7a7b5de3143909e402b0fedde3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241315"
---
# <a name="compiler-warning-level-4-c4456"></a>컴파일러 경고 (수준 4) C4456

> '*identifier*' 선언이 이전 로컬 선언을 숨깁니다.

로컬 범위에서 *식별자* 를 선언 하면 이름이 같은 이전 로컬 선언의 선언이 숨겨집니다. 이 경고를 사용 하면 로컬 범위의 *식별자* 에 대 한 참조가 이전 로컬이 아닌 로컬로 선언 된 버전으로 확인 되 고 의도 하지 않을 수도 있습니다. 이 문제를 해결 하려면 다른 로컬 이름과 충돌 하지 않는 로컬 변수 이름을 지정 하는 것이 좋습니다.

## <a name="example"></a>예제

다음 샘플에서는 루프 제어 변수와 `int x` 의 지역 변수가 `double x` 동일한 이름을 C4456 생성 합니다 `member_fn` . 이 문제를 해결 하려면 지역 변수에 다른 이름을 사용 합니다.

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```

---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4458'
title: 컴파일러 경고 (수준 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: f631fe4086c69732c972161ae7bb6096232b2740
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241263"
---
# <a name="compiler-warning-level-4-c4458"></a>컴파일러 경고 (수준 4) C4458

> '*identifier*' 선언이 클래스 멤버를 숨깁니다.

로컬 범위에서 *식별자* 를 선언 하면 클래스 범위에서 이름이 같은 *식별자* 의 선언이 숨겨집니다. 이 경고를 사용 하면이 범위의 *식별자* 에 대 한 참조가 클래스 멤버 버전이 아니라 로컬로 선언 된 버전으로 확인 되 고 의도 하지 않을 수도 있습니다. 이 문제를 해결 하려면 클래스 멤버 이름과 충돌 하지 않는 로컬 변수 이름을 지정 하는 것이 좋습니다.

## <a name="example"></a>예제

다음 샘플에서는의 매개 변수와 `x` 지역 변수가 `y` `member_fn` 클래스의 데이터 멤버와 동일한 이름을 C4458 생성 합니다. 이 문제를 해결 하려면 매개 변수 및 지역 변수에 다른 이름을 사용 합니다.

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```

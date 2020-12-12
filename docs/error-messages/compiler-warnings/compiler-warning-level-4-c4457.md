---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4457'
title: 컴파일러 경고 (수준 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 8898189668eba95619e6bd0d0ccf1cb8ca3afdfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251416"
---
# <a name="compiler-warning-level-4-c4457"></a>컴파일러 경고 (수준 4) C4457

> '*identifier*' 선언에서 함수 매개 변수를 숨깁니다.

로컬 범위에서 *식별자* 를 선언 하면 동일한 이름의 함수 매개 변수 선언이 숨겨집니다. 이 경고를 사용 하면 로컬 범위의 *식별자* 에 대 한 참조가 매개 변수가 아니라 로컬로 선언 된 버전으로 확인 되 고 의도 하지 않을 수도 있습니다. 이 문제를 해결 하려면 매개 변수 이름과 충돌 하지 않는 로컬 변수 이름을 지정 하는 것이 좋습니다.

## <a name="example"></a>예제

다음 샘플에서는의 매개 변수와 `x` 지역 변수가 `x` 동일한 이름을 C4457 생성 합니다 `member_fn` . 이 문제를 해결 하려면 매개 변수 및 지역 변수에 다른 이름을 사용 합니다.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```

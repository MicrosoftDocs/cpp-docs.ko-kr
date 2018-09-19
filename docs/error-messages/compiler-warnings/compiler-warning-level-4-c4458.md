---
title: 컴파일러 경고 (수준 4) C4458 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 873aa94db899ae6620e2bbb1f24277c6e7c841c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094548"
---
# <a name="compiler-warning-level-4-c4458"></a>컴파일러 경고 (수준 4) C4458

> 선언의 '*식별자*' 클래스 멤버를 숨깁니다

선언의 *식별자* 로컬 범위에 같은 이름의 선언을 숨깁니다 *식별자* 클래스 범위에 있습니다. 이 경고를 사용 하면에 대 한 참조는 알고 *식별자* 이 범위에 클래스 멤버 버전이 아닌, 의도 하지 않을 수도 있고는 로컬로 선언 된 버전을 확인 합니다. 이 문제를 해결 하려면 클래스 멤버 이름과 충돌 하지 않는 지역 변수 이름을 지정 해야 하는 것이 좋습니다.

## <a name="example"></a>예제

때문에 다음 샘플에서는 C4458 매개 변수 `x` 및 지역 변수 `y` 에서 `member_fn` 클래스의 데이터 멤버와 동일한 이름이 있습니다. 이 문제를 해결 하려면 다른 이름을 매개 변수 및 지역 변수를 사용 합니다.

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

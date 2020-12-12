---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4459'
title: 컴파일러 경고 (수준 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: cc074c0624a392ce058a284eb21661d7d34ae11f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251403"
---
# <a name="compiler-warning-level-4-c4459"></a>컴파일러 경고 (수준 4) C4459

> '*identifier*' 선언이 전역 선언을 숨깁니다.

로컬 범위에서 *식별자* 를 선언 하면 전역 범위에서 이름이 같은 *식별자* 의 선언이 숨겨집니다. 이 경고를 사용 하면이 범위의 *식별자* 에 대 한 참조가 전역 버전이 아니라 로컬로 선언 된 버전으로 확인 되 고 사용자가 의도 하거나 의도 하지 않을 수 있습니다. 일반적으로 좋은 엔지니어링 사례로 전역 변수의 사용을 최소화 하는 것이 좋습니다. 전역 네임 스페이스의 오염을 최소화 하려면 전역 변수에 대해 명명 된 네임 스페이스를 사용 하는 것이 좋습니다.

이 경고는 Microsoft c + + 컴파일러 버전 18.00에서 Visual Studio 2015의 새로운 경고입니다. 코드를 마이그레이션하는 동안 해당 버전의 컴파일러에서 경고를 표시 하지 않으려면 [/Wv: 18](../../build/reference/compiler-option-warning-level.md) 컴파일러 옵션을 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4459를 생성 합니다.

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

이 문제를 해결 하는 한 가지 방법은 전역에 대 한 네임 스페이스를 만들지만 지시문을 사용 하 여 **`using`** 해당 네임 스페이스를 범위에 가져오는 것이 아니므로 모든 참조는 명확한 정규화 된 이름을 사용 해야 합니다.

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```

---
description: '자세한 정보: 컴파일러 오류 C2653'
title: 컴파일러 오류 C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: f3be7ade8a6dcfc6aa8c5a83cc8a055fc230789d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286152"
---
# <a name="compiler-error-c2653"></a>컴파일러 오류 C2653

> '*identifier*': 클래스 또는 네임 스페이스 이름이 아닙니다.

언어 구문에는 여기에 클래스, 구조체, 공용 구조체 또는 네임 스페이스 이름이 필요 합니다.

이 오류는 범위 연산자 앞에 클래스, 구조체, 공용 구조체 또는 네임 스페이스로 선언 되지 않은 이름을 사용 하는 경우에 발생할 수 있습니다. 이 문제를 해결 하려면 이름을 선언 하거나 사용 하기 전에 이름을 선언 하는 헤더를 포함 합니다.

C2653는 하나 이상의 범위에 중첩 된 네임 스페이스 이름을 포함 하는 네임 스페이스인 *복합 네임* 스페이스를 정의 하려고 하는 경우에도 가능 합니다. C + + 17 이전에는 c + +에서 복합 네임 스페이스 정의를 사용할 수 없습니다. Visual Studio 2015 업데이트 3부터 [/prod: c + + 최신](../../build/reference/std-specify-language-standard-version.md) 컴파일러 옵션을 지정 하면 복합 네임 스페이스를 사용할 수 있습니다. Visual Studio 2017 버전 15.5부터 [/std: c + + 17](../../build/reference/std-specify-language-standard-version.md) 옵션이 지정 된 경우 컴파일러는 복합 네임 스페이스 정의를 지원 합니다.

## <a name="examples"></a>예제

범위 이름이 사용 되지만 선언 되지 않았으므로이 샘플은 C2653를 생성 합니다. 컴파일러는 범위 연산자 (::) 앞에 클래스, 구조체, 공용 구조체 또는 네임 스페이스 이름을 예상 합니다.

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

C + + 17 이상 표준에 대해 컴파일되지 않은 코드에서 중첩 된 네임 스페이스는 각 중첩 수준에서 명시적 네임 스페이스 선언을 사용 해야 합니다.

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual Studio 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```

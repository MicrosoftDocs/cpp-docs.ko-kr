---
title: 컴파일러 경고(수준 4) C4255
ms.date: 11/04/2016
f1_keywords:
- C4255
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
ms.openlocfilehash: 7b64da554d6afbac4422c79ff593429ba90a4378
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541706"
---
# <a name="compiler-warning-level-4-c4255"></a>컴파일러 경고(수준 4) C4255

' function ': 함수 프로토타입이 지정 되지 않았습니다. ' () '에서 ' (void) '로 변환 합니다.

컴파일러에서 함수에 대 한 명시적 인수 목록을 찾지 못했습니다. 이 경고는 C 컴파일러에만 해당 됩니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4255를 생성 합니다.

```c
// C4255.c
// compile with: /W4 /WX
#pragma warning (default : 4255)

void f()  { // C4255
// try the following line instead
//void f(void) {
}

int main(int argc, char *argv[]) {
   f();
}
```
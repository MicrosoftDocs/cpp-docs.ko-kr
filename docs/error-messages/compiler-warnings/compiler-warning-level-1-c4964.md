---
title: 컴파일러 경고 (수준 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 2a75a1b7d3738794046ac697113c3c746bb6fcff
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052240"
---
# <a name="compiler-warning-level-1-c4964"></a>컴파일러 경고 (수준 1) C4964

최적화 옵션을 지정 하지 않았습니다. 프로필 정보가 수집 되지 않습니다.

[/Gl](../../build/reference/gl-whole-program-optimization.md) 및 [/ltcg](../../build/reference/ltcg-link-time-code-generation.md) 가 지정 되었지만 최적화가 요청 되지 않았으므로 .pgc 파일이 생성 되지 않으므로 프로필 기반 최적화가 불가능 합니다.

응용 프로그램을 실행할 때 .pgc 파일을 생성 하려면 [/o](../../build/reference/o-options-optimize-code.md) 컴파일러 옵션 중 하나를 지정 합니다.

다음 샘플에서는 C4964를 생성 합니다.

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```
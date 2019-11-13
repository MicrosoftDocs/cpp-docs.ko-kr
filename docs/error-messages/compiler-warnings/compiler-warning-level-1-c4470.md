---
title: 컴파일러 경고 (수준 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: dc1efad7f18310727e2fdb756e49b95294357c4d
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965407"
---
# <a name="compiler-warning-level-1-c4470"></a>컴파일러 경고 (수준 1) C4470

/clr에서 부동 소수점 컨트롤 pragma가 무시 되었습니다.

Float 컨트롤 pragma는 다음과 같습니다.

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)에는 영향을 주지 않습니다.

다음 샘플에서는 C4470를 생성 합니다.

```cpp
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```
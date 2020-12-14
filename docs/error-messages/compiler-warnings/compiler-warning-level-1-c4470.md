---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4470'
title: 컴파일러 경고(수준 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: 6fe01782fbd2151175bc1da59afa8bd73fa5648d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310982"
---
# <a name="compiler-warning-level-1-c4470"></a>컴파일러 경고(수준 1) C4470

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

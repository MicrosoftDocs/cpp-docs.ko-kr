---
title: 컴파일러 경고(수준 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538538"
---
# <a name="compiler-warning-level-1-c4939"></a>컴파일러 경고(수준 1) C4939

\#pragma vtordisp는 사용 되지 않으며 Visual c + +의 이후 릴리스에서 제거 될 예정

[vtordisp](../../preprocessor/vtordisp.md) pragma는 이후 Visual C++ 릴리스에서 제거될 예정입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4939를 생성합니다.

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```
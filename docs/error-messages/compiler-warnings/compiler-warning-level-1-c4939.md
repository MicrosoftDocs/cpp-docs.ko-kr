---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4939'
title: 컴파일러 경고(수준 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: e31d59321ee5c2f6f154ebcaac4b74054db2604e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328030"
---
# <a name="compiler-warning-level-1-c4939"></a>컴파일러 경고(수준 1) C4939

\#pragma vtordisp는 더 이상 사용 되지 않으며 이후 릴리스에서 제거 될 예정 Visual C++

[vtordisp](../../preprocessor/vtordisp.md) pragma는 이후 Visual C++ 릴리스에서 제거될 예정입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4939를 생성합니다.

```cpp
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```

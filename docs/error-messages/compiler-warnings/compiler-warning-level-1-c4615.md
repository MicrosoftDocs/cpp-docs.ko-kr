---
title: 컴파일러 경고 (수준 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 8c682b309cbabbaf97346e37038806d331f949ac
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052604"
---
# <a name="compiler-warning-level-1-c4615"></a>컴파일러 경고 (수준 1) C4615

\#pragma warning: 알 수 없는 사용자 경고 유형

**Pragma** [warning](../../preprocessor/warning.md)에 잘못 된 경고 지정자를 사용 했습니다. 오류를 해결 하려면 유효한 경고 지정자를 사용 합니다.

다음 샘플에서는 C4615를 생성 합니다.

```cpp
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```
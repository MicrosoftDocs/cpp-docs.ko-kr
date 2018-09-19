---
title: 컴파일러 경고 (수준 1) C4615 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4615
dev_langs:
- C++
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd260e37fb3f98f3e23d1c99c9ff53cae4f0198f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073709"
---
# <a name="compiler-warning-level-1-c4615"></a>컴파일러 경고(수준 1) C4615

\#pragma 경고: 알 수 없는 사용자 경고 형식

잘못 된 경고 지정자를 사용한 **pragma** [경고](../../preprocessor/warning.md)합니다. 오류를 해결 하려면 올바른 경고 지정자를 사용 합니다.

다음 샘플에서는 C4615 오류가 생성 됩니다.

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```
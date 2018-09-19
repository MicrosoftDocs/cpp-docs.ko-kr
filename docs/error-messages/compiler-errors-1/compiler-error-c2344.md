---
title: 컴파일러 오류 C2344 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2344
dev_langs:
- C++
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c560d1fcd250a83501579ec80768b4ba2de57f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110221"
---
# <a name="compiler-error-c2344"></a>컴파일러 오류 C2344

align(#): 맞춤은 2의 거듭제곱이어야 합니다.

[align](../../cpp/align-cpp.md) 키워드를 사용하는 경우 전달하는 값이 2의 거듭제곱이어야 합니다.

예를 들어 3은 2의 거듭제곱이 아니므로 다음 코드는 C2344를 생성합니다.

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```
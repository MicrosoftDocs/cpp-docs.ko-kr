---
description: '자세한 정보: 컴파일러 오류 C2344'
title: 컴파일러 오류 C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: 1ad4f1808f407a9f654f5bbf3a022c2dc7b0b3ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234763"
---
# <a name="compiler-error-c2344"></a>컴파일러 오류 C2344

align(#): 맞춤은 2의 거듭제곱이어야 합니다.

[align](../../cpp/align-cpp.md) 키워드를 사용하는 경우 전달하는 값이 2의 거듭제곱이어야 합니다.

예를 들어 3은 2의 거듭제곱이 아니므로 다음 코드는 C2344를 생성합니다.

```cpp
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```

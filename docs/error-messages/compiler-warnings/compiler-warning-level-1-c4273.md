---
title: 컴파일러 경고 (수준 1) C4273
ms.date: 11/04/2016
f1_keywords:
- C4273
helpviewer_keywords:
- C4273
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
ms.openlocfilehash: fb24f195c6a8a0b0b2a221e57508a558b50a2b96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626682"
---
# <a name="compiler-warning-level-1-c4273"></a>컴파일러 경고 (수준 1) C4273

' function ': DLL 링크가 일치 하지 않습니다.

파일의 두 정의는 [dllimport](../../cpp/dllexport-dllimport.md)를 사용 하는 경우와 다릅니다.

## <a name="example"></a>예제

다음 샘플에서는 C4273를 생성 합니다.

```cpp
// C4273.cpp
// compile with: /W1 /c
char __declspec(dllimport) c;
char c;   // C4273, delete this line or the line above to resolve
```

## <a name="example"></a>예제

다음 샘플에서는 C4273를 생성 합니다.

```cpp
// C4273_b.cpp
// compile with: /W1 /clr /c
#include <stdio.h>
extern "C" int printf_s(const char *, ...);   // C4273
```
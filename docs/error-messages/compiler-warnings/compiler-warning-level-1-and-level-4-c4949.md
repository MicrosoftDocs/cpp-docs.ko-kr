---
title: 컴파일러 경고 (수준 1 및 수준 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627407"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>컴파일러 경고 (수준 1 및 수준 4) C4949

pragma ' managed ' 및 ' unmanaged '는 '/clr [: option] '로 컴파일된 경우에만 의미가 있습니다.

소스 코드가 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일되지 않은 경우 컴파일러는 [관리 되](../../preprocessor/managed-unmanaged.md) 는 및 관리 되지 않는 pragma를 무시 합니다. 이 경고는 정보 제공용입니다.

다음 샘플에서는 C4949를 생성 합니다.

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

**/Clr**을 사용 하지 않고 **#pragma 비관리** 를 사용 하는 경우 C4949는 수준 4 경고입니다.

다음 샘플에서는 C4949를 생성 합니다.

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```
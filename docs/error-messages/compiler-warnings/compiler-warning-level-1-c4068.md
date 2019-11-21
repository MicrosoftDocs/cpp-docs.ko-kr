---
title: 컴파일러 경고(수준 1) C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: ba6e57fb954e0331e8eede5e7859fbeed5ce6424
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626926"
---
# <a name="compiler-warning-level-1-c4068"></a>컴파일러 경고(수준 1) C4068

알 수 없는 pragma입니다.

컴파일러가 인식할 수 없는 [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)를 무시했습니다. 사용하는 컴파일러에서 **pragma** 가 허용되는지 확인합니다. 다음 샘플에서는 C4068을 생성합니다.

```cpp
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```
---
title: 컴파일러 오류 C2710
ms.date: 11/04/2016
f1_keywords:
- C2710
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
ms.openlocfilehash: eea836f3508d750701b694421f660ce455d6f1f7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757451"
---
# <a name="compiler-error-c2710"></a>컴파일러 오류 C2710

' 구문 ': ' __declspec (한정자) '은 (는) 포인터를 반환 하는 함수에만 적용할 수 있습니다.

반환 값이 포인터인 함수는 `modifier` 적용할 수 있는 유일한 구문입니다.

다음 샘플에서는 C2710를 생성 합니다.

```cpp
// C2710.cpp
__declspec(restrict) void f();   // C2710
// try the following line instead
__declspec(restrict) int * g();
```

---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4212'
title: 컴파일러 경고(수준 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: 3c557e5fa11e2a6fb1f15e5389901ede537755af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297358"
---
# <a name="compiler-warning-level-4-c4212"></a>컴파일러 경고(수준 4) C4212

비표준 확장이 사용 됨: 함수 선언에서 줄임표를 사용 했습니다.

함수 프로토타입에는 다양 한 수의 인수가 있습니다. 함수 정의는 그렇지 않습니다.

다음 샘플에서는 C4212를 생성 합니다.

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```

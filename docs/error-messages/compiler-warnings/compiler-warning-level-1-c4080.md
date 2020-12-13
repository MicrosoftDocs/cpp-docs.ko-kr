---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4080'
title: 컴파일러 경고(수준 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: 05dcb119d0c028446f038a2cbd796432c688a8c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344291"
---
# <a name="compiler-warning-level-1-c4080"></a>컴파일러 경고(수준 1) C4080

세그먼트 이름에 대한 식별자가 있어야 하는데 'symbol'이 있습니다.

[#pragma alloc_text](../../preprocessor/alloc-text.md) 의 세그먼트 이름은 문자열 또는 식별자여야 합니다. 유효한 식별자가 없으면 컴파일러가 pragma를 무시합니다.

다음 샘플에서는 C4080을 생성합니다.

```cpp
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```

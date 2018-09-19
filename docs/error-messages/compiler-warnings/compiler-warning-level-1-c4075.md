---
title: 컴파일러 경고 (수준 1) C4075 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5056c4bbca66b47ca991daf4c65485e80e43e0db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073033"
---
# <a name="compiler-warning-level-1-c4075"></a>컴파일러 경고(수준 1) C4075

이니셜라이저가 인식할 수 없는 초기화 영역에 있습니다.

[#pragma init_seg](../../preprocessor/init-seg.md) 에서는 인식할 수 없는 섹션 이름을 사용합니다. 컴파일러는 **pragma** 명령을 무시합니다.

다음 샘플에서는 C4075를 생성합니다.

```
// C4075.cpp
// compile with: /W1
#pragma init_seg("mysegg")   // C4075

// try..
// #pragma init_seg(user)

int main() {
}
```
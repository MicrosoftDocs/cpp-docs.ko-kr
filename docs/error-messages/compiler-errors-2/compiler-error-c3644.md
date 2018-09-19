---
title: 컴파일러 오류 C3644 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3644
dev_langs:
- C++
helpviewer_keywords:
- C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63e48b944bd5b828ece1110240c462584703ba73
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099488"
---
# <a name="compiler-error-c3644"></a>컴파일러 오류 C3644

'function': 관리 코드를 생성 하는 함수를 컴파일할 수 없습니다.

함수에서 일부 키워드의 현재 상태를 사용 하면 함수가를 네이티브로 컴파일하도록 합니다.

다음 샘플에서는 C3644 오류가 생성 됩니다.

```
// C3644.cpp
// compile with: /clr
// processor: x86

void __clrcall Func2(int i) {
   __asm {}   // C3644
}
```
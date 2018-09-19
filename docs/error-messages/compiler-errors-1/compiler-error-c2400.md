---
title: 컴파일러 오류 C2400 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2400
dev_langs:
- C++
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 303a0aacbcde0fcf495469ed9cb9310ddb7710e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115166"
---
# <a name="compiler-error-c2400"></a>컴파일러 오류 C2400

인라인 어셈블러 구문 오류가 '컨텍스트'; 'token'을 찾을 수합니다

토큰이 지정 된 컨텍스트에서 구문 오류가 발생 했습니다.

다음 샘플에서는 C2400를 생성합니다.

```
// C2400.cpp
// processor: x86
int main() {
   __asm {
      heh ax,bx;   // C2400, heh is not a valid x86 instruction
      mov ax,bx;   // OK
   }
}
```
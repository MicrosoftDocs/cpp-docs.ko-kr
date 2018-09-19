---
title: 컴파일러 오류 C2745 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2745
dev_langs:
- C++
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d08e89fe3dbcfbff8c947b432bda94e9ac15ef99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099873"
---
# <a name="compiler-error-c2745"></a>컴파일러 오류 C2745

'token':이 토큰을 식별자로 변환할 수 없습니다

식별자는 유효한 문자 구성 해야 합니다.

다음 샘플에서는 C2745 오류가 생성 됩니다.

```
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```
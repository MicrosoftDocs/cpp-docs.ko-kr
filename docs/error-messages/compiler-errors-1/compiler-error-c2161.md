---
title: 컴파일러 오류 C2161 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2161
dev_langs:
- C++
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac32776c954974f0f2f81789c6e78de894786b73
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051825"
---
# <a name="compiler-error-c2161"></a>컴파일러 오류 C2161

매크로 정의 끝에 '##'이 올 수 없습니다.

매크로 정의가 토큰 붙여넣기 연산자(##)로 종료되었습니다.

다음 샘플에서는 C2161 오류가 발생하는 경우를 보여 줍니다.

```
// C2161.cpp
// compile with: /c
#define mac(a,b) a   // OK
#define mac(a,b) a##   // C2161
```
---
title: 컴파일러 오류 C2160
ms.date: 11/04/2016
f1_keywords:
- C2160
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
ms.openlocfilehash: bd0c49f44bce09958541a47db0c66bc22d7f2b76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454511"
---
# <a name="compiler-error-c2160"></a>컴파일러 오류 C2160

매크로 정의 시작에 '##'이 올 수 없습니다.

매크로 정의가 토큰 붙여넣기 연산자(##)로 시작되었습니다.

다음 샘플에서는 C2160을 생성합니다.

```
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```
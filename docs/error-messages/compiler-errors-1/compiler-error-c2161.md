---
description: '자세한 정보: 컴파일러 오류 C2161'
title: 컴파일러 오류 C2161
ms.date: 11/04/2016
f1_keywords:
- C2161
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
ms.openlocfilehash: bafbcceee5f09f6d0d29d3a501dc94929d69b9eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177980"
---
# <a name="compiler-error-c2161"></a>컴파일러 오류 C2161

매크로 정의 끝에 '##'이 올 수 없습니다.

매크로 정의가 토큰 붙여넣기 연산자(##)로 종료되었습니다.

다음 샘플에서는 C2161 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2161.cpp
// compile with: /c
#define mac(a,b) a   // OK
#define mac(a,b) a##   // C2161
```

---
description: '자세한 정보: 컴파일러 오류 C2372'
title: 컴파일러 오류 C2372
ms.date: 03/23/2020
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: 9cf94e63e673ca226f3f9c3f1b4c3aa0a6bf8016
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174912"
---
# <a name="compiler-error-c2372"></a>컴파일러 오류 C2372

> '*identifier*': 재정의 서로 다른 유형의 간접 참조

식별자가 이미 다른 파생 형식으로 정의 되어 있습니다.

다음 샘플에서는 C2372를 생성 합니다.

```cpp
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```

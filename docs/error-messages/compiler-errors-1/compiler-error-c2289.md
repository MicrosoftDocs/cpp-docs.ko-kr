---
description: '자세한 정보: 컴파일러 오류 C2289'
title: 컴파일러 오류 C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: ba9af908af6defaccd6825ce3dad412ad6914c77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185962"
---
# <a name="compiler-error-c2289"></a>컴파일러 오류 C2289

동일한 형식 한정자를 두 번 이상 사용했습니다.

형식 선언 또는 정의에서 형식 한정자 (,, **`const`** 또는)를 두 번 이상 사용 하 여 **`volatile`** **`signed`** **`unsigned`** ANSI 호환성 (**/za**)에서 오류를 발생 시킵니다.

다음 샘플에서는 C2286을 생성합니다.

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```

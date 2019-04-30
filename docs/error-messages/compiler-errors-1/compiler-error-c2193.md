---
title: 컴파일러 오류 C2193
ms.date: 11/04/2016
f1_keywords:
- C2193
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
ms.openlocfilehash: 1eb1145b7927733ab82253632847da90542250fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302620"
---
# <a name="compiler-error-c2193"></a>컴파일러 오류 C2193

'identifier': 세그먼트에 이미

함수를 사용 하 여 두 개의 서로 다른 세그먼트에 배치 되었습니다 `alloc_text` 고 `code_seg` pragma입니다.

다음 샘플에서는 C2193 오류가 생성 됩니다.

```
// C2193.cpp
// compile with: /c
extern "C" void MYFUNCTION();
#pragma alloc_text(MYCODE, MYFUNCTION)
#pragma code_seg("MYCODE2")
extern "C" void MYFUNCTION() {}   // C2193
extern "C" void MYFUNCTION2() {}
```
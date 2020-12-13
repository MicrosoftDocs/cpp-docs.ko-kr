---
description: '자세한 정보: 컴파일러 오류 C2193'
title: 컴파일러 오류 C2193
ms.date: 11/04/2016
f1_keywords:
- C2193
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
ms.openlocfilehash: 63fc345e2898c3fe2bf222bf83ce0d703be97972
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337654"
---
# <a name="compiler-error-c2193"></a>컴파일러 오류 C2193

' identifier ': 세그먼트에 이미 있습니다.

및 pragma를 사용 하 여 두 개의 서로 다른 세그먼트에 함수를 배치 했습니다 `alloc_text` `code_seg` .

다음 샘플에서는 C2193를 생성 합니다.

```cpp
// C2193.cpp
// compile with: /c
extern "C" void MYFUNCTION();
#pragma alloc_text(MYCODE, MYFUNCTION)
#pragma code_seg("MYCODE2")
extern "C" void MYFUNCTION() {}   // C2193
extern "C" void MYFUNCTION2() {}
```

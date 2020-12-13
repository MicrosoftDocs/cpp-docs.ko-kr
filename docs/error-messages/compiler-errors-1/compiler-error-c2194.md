---
description: '자세한 정보: 컴파일러 오류 C2194'
title: 컴파일러 오류 C2194
ms.date: 11/04/2016
f1_keywords:
- C2194
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
ms.openlocfilehash: fefdfbc434dce1347ff4a46a56040219f64feb47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337637"
---
# <a name="compiler-error-c2194"></a>컴파일러 오류 C2194

' identifier ': 텍스트 세그먼트입니다.

`data_seg`Pragma는와 함께 사용 된 세그먼트 이름을 사용 `code_seg` 합니다.

다음 샘플에서는 C2194를 생성 합니다.

```cpp
// C2194.cpp
// compile with: /c
#pragma code_seg("MYCODE")
#pragma data_seg("MYCODE")   // C2194
#pragma data_seg("MYCODE2")   // OK
```

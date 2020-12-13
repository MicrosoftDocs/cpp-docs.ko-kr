---
description: '자세한 정보: 컴파일러 오류 C2195'
title: 컴파일러 오류 C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: dbae1b48b5dc8d7c04e103dc15ca66f0183f0dbb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337630"
---
# <a name="compiler-error-c2195"></a>컴파일러 오류 C2195

' identifier ': 데이터 세그먼트입니다.

`code_seg`Pragma는 pragma와 함께 사용 된 세그먼트 이름을 사용 합니다 `data_seg` .

다음 샘플에서는 C2195를 생성 합니다.

```cpp
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```

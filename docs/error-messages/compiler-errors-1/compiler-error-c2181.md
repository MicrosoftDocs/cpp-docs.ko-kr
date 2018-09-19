---
title: 컴파일러 오류 C2181 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2181
dev_langs:
- C++
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d449bb011b63034df49fe4e3d13b373e0ca2c827
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062282"
---
# <a name="compiler-error-c2181"></a>컴파일러 오류 C2181

if와 짝을 이루지 않는 잘못된 else문입니다.

각 `else` 에는 해당하는 `if`가 있어야 합니다.

다음 샘플에서는 C2181을 생성합니다.

```
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

해결 방법:

```
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```
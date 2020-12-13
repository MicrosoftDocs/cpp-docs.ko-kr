---
description: '자세한 정보: 컴파일러 오류 C2181'
title: 컴파일러 오류 C2181
ms.date: 11/04/2016
f1_keywords:
- C2181
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
ms.openlocfilehash: f251575d22c27ca7b0e2339a987f42303546a721
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335193"
---
# <a name="compiler-error-c2181"></a>컴파일러 오류 C2181

if와 짝을 이루지 않는 잘못된 else문입니다.

각 **`else`** 에 일치 하는가 있어야 합니다 **`if`** .

다음 샘플에서는 C2181을 생성합니다.

```cpp
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

해결 방법:

```cpp
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```

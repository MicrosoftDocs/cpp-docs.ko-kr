---
description: '자세한 정보: 컴파일러 오류 C2166'
title: 컴파일러 오류 C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 195782fca62b9bf69d17fa1aa382df2127b594e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145519"
---
# <a name="compiler-error-c2166"></a>컴파일러 오류 C2166

l-value가 const 개체를 지정합니다.

코드는 선언 된 항목을 수정 하려고 **`const`** 합니다.

다음 샘플에서는 C2166을 생성합니다.

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```

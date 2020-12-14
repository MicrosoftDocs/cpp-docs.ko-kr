---
description: '자세한 정보: 컴파일러 오류 C2673'
title: 컴파일러 오류 C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 1b7d634e4c1b62860a648ef5327ffd8b888c7d7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282070"
---
# <a name="compiler-error-c2673"></a>컴파일러 오류 C2673

' function ': 전역 함수에는 ' this ' 포인터가 없습니다.

전역 함수에서 액세스 하려고 했습니다 **`this`** .

다음 샘플에서는 C2673를 생성 합니다.

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```

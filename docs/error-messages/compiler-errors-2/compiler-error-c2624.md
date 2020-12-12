---
description: '자세한 정보: 컴파일러 오류 C2624'
title: 컴파일러 오류 C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: 4fa52e5192bd71c9fcdd3608b4161d1e5da57bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174678"
---
# <a name="compiler-error-c2624"></a>컴파일러 오류 C2624

지역 클래스는 ' extern ' 변수를 선언 하는 데 사용할 수 없습니다.

로컬 클래스 또는 구조체는 변수를 선언 하는 데 사용할 수 없습니다 **`extern`** .

다음 샘플에서는 C2624를 생성 합니다.

```cpp
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```

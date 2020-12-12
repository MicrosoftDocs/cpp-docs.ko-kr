---
description: '자세한 정보: 컴파일러 오류 C2619'
title: 컴파일러 오류 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 2ca9a8379901703299e89e71671ec0270c1ff1e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123550"
---
# <a name="compiler-error-c2619"></a>컴파일러 오류 C2619

'identifier': 익명 구조체 또는 집합체에는 정적 데이터 멤버가 허용되지 않습니다.

익명 구조체 또는 공용 구조체의 멤버가 선언 됩니다 **`static`** .

다음 샘플에서는 C2619 오류가 발생하는 경우 및 static 키워드를 제거하여 오류를 해결하는 방법을 보여 줍니다.

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```

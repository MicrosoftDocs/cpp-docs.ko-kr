---
title: 컴파일러 오류 C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: b45ec25f1ed516ae73b242fdcc7c66f68c92f724
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387112"
---
# <a name="compiler-error-c2040"></a>컴파일러 오류 C2040

'operator' : 'identifier1'의 간접 참조 수준이 'identifier2'와 다릅니다.

지정 피연산자가 포함된 식에 호환되지 않는 피연산자 형식이나 암시적으로 변환된 피연산자 형식이 있습니다. 두 피연산자 모두가 산술이거나 모두가 비산술(예: 배열 또는 포인터)인 경우 변경 없이 사용됩니다. 한 피연산자는 산술이고 다른 피연산자는 아닌 경우 산술 피연산자가 비산술 피연산자의 형식으로 변환됩니다.

다음 샘플에서는 C2040 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
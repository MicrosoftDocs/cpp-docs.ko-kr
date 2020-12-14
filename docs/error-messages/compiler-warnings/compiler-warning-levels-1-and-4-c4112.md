---
description: '자세한 정보: 컴파일러 경고 (수준 1 및 4) C4112'
title: 컴파일러 경고(수준 1 및 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: a4958cbd4537ab9c1f5686383f27414ae366e72b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234555"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>컴파일러 경고(수준 1 및 4) C4112

\#줄에 1과 숫자 사이의 정수가 필요 합니다.

[#line](../../preprocessor/hash-line-directive-c-cpp.md) 지시문에 허용 범위를 벗어난 정수 매개 변수를 지정합니다.

지정된 매개 변수가 1보다 작은 경우 라인 카운터가 1로 다시 설정됩니다. 지정된 매개 변수가 컴파일러에 정의된 한도인 *number* 보다 큰 경우 라인 카운터가 변경되지 않습니다. 이는 ANSI 호환성([/Za](../../build/reference/za-ze-disable-language-extensions.md))에서는 수준 1 경고이며 Microsoft 확장([/Ze](../../build/reference/za-ze-disable-language-extensions.md))에서는 수준 4 경고입니다.

다음 샘플에서는 C4112를 생성합니다.

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```

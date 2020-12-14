---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4130'
title: 컴파일러 경고(수준 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: e7096f471405b0b22bcb0a825dd9ccd0de4e3510
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261816"
---
# <a name="compiler-warning-level-4-c4130"></a>컴파일러 경고(수준 4) C4130

'operator': 문자열 상수의 주소에서 논리 연산을 수행했습니다.

문자열 리터럴의 주소와 함께 연산자를 사용하면 예기치 않은 코드가 생성됩니다.

다음 샘플에서는 C4130을 생성합니다.

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

**`if`** 문은 포인터에 저장 된 값을 `pc` 코드에서 문자열이 발생할 때마다 개별적으로 할당 되는 "Hello" 문자열의 주소와 비교 합니다. **`if`** 문은가 가리키는 문자열을 `pc` "Hello" 문자열과 비교 하지 않습니다.

문자열을 비교하려면 `strcmp` 함수를 사용합니다.

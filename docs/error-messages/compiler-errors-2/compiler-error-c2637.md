---
description: '자세한 정보: 컴파일러 오류 C2637'
title: 컴파일러 오류 C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: 1f42a732d5dfa3f7c94e0cc755bd1db00c8ff56b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208725"
---
# <a name="compiler-error-c2637"></a>컴파일러 오류 C2637

' identifier ': 데이터 멤버에 대 한 포인터를 수정할 수 없습니다.

데이터 멤버에 대 한 포인터는 호출 규칙을 가질 수 없습니다. 이 문제를 해결 하려면 호출 규칙을 제거 하거나 멤버 함수에 대 한 포인터를 선언 합니다.

다음 샘플에서는 C2637를 생성 합니다.

```cpp
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```

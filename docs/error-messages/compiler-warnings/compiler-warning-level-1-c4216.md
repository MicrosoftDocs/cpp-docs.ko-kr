---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4216'
title: 컴파일러 경고(수준 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: b570863653ea64d159cbb2f4a11138b2361ce149
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266483"
---
# <a name="compiler-warning-level-1-c4216"></a>컴파일러 경고(수준 1) C4216

비표준 확장이 사용 됨: float long입니다.

기본 Microsoft 확장 (/Ze)은 **float long** 을로 처리 **`double`** 합니다. ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))은 그렇지 않습니다. **`double`** 를 사용 하 여 호환성을 유지 합니다. 다음 샘플에서는 C4216를 생성 합니다.

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```

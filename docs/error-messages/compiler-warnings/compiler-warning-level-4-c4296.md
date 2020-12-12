---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4296'
title: 컴파일러 경고(수준 4) C4296
ms.date: 11/04/2016
f1_keywords:
- C4296
helpviewer_keywords:
- C4296
ms.assetid: 9d99aafe-f6bd-4ee0-b8d0-98ce5712274d
ms.openlocfilehash: 995c332a0f1ee46c9df7081dd34a97b51de40ac6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294537"
---
# <a name="compiler-warning-level-4-c4296"></a>컴파일러 경고(수준 4) C4296

' operator ': 식이 항상 false입니다.

부호 없는 변수가 0 인 비교 연산에 사용 되었습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4296를 생성 합니다.

```cpp
// C4296.cpp
// compile with: /W4
#pragma warning(default : 4296)
int main()
{
   unsigned int u = 9;
   if (u < 0)    // C4296
      u++;
   if (u >= 0)   // C4296
      u++;
}
```

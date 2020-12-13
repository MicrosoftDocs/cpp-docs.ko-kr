---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4918'
title: 컴파일러 경고(수준 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 268fbff753ff5ed0cc2d63df6ba8422cdf073662
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330445"
---
# <a name="compiler-warning-level-4-c4918"></a>컴파일러 경고(수준 4) C4918

'character': pragma 최적화 목록에 잘못된 문자가 있습니다.

[optimize](../../preprocessor/optimize.md) pragma 문의 최적화 목록에 알 수 없는 문자가 있습니다.

예를 들어 다음 문은 C4918을 생성합니다.

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```

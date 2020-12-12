---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4618'
title: 컴파일러 경고(수준 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: 824a55dab68fe45a94cacb1924bed46b87b7c0eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208686"
---
# <a name="compiler-warning-level-1-c4618"></a>컴파일러 경고(수준 1) C4618

pragma 매개 변수에 빈 문자열이 포함 되어 있습니다. pragma가 무시 되었습니다.

**#Pragma** 에 대 한 인수로 null 문자열이 지정 되었습니다.

Pragma가 인수 없이 처리 되었습니다.

다음 샘플에서는 C4618를 생성 합니다.

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```

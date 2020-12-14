---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4806'
title: 컴파일러 경고(수준 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 3e4aaa67c2a979afde2d1a7643d0c5ab1b879418
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238247"
---
# <a name="compiler-warning-level-1-c4806"></a>컴파일러 경고(수준 1) C4806

'operation': 안전하지 않은 연산입니다. 'type' 형식의 값('type' 형식으로 확장)이 주어진 상수와 같을 수 없습니다.

이 메시지는와 같은 코드에 대해 경고 `b == 3` `b` 합니다. 여기서는 형식 **`bool`** 입니다. 승격 규칙으로 인해이 **`bool`** 로 승격 됩니다 **`int`** . 이는 유효 하지만 일 수 없습니다 **`true`** . 다음 샘플에서는 C4806을 생성합니다.

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```

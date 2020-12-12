---
description: '자세한 정보: 컴파일러 오류 C2389'
title: 컴파일러 오류 C2389
ms.date: 11/04/2016
f1_keywords:
- C2389
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
ms.openlocfilehash: 1f9d34be47376564bf7c6fc221cf6f5b01e7850f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123970"
---
# <a name="compiler-error-c2389"></a>컴파일러 오류 C2389

'operator': 'nullptr'는 잘못된 피연산자입니다.

**`nullptr`** 는 피연산자 일 수 없습니다.

다음 샘플에서는 C2389를 생성합니다.

```cpp
// C2389.cpp
// compile with: /clr
int main() {
   throw nullptr;   // C2389
}
```

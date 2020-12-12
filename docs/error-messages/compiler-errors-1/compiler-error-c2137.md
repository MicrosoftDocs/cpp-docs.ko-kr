---
description: '자세한 정보: 컴파일러 오류 C2137'
title: 컴파일러 오류 C2137
ms.date: 11/04/2016
f1_keywords:
- C2137
helpviewer_keywords:
- C2137
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
ms.openlocfilehash: 053c933b3ee650d1d49c230d9bfc23c656f9a709
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323079"
---
# <a name="compiler-error-c2137"></a>컴파일러 오류 C2137

문자 상수가 비어 있습니다.

빈 문자 상수(' ')는 허용되지 않습니다.

다음 샘플에서는 C2137을 생성합니다.

```cpp
// C2137.cpp
int main() {
   char c = '';   // C2137
   char d = ' ';   // OK
}
```

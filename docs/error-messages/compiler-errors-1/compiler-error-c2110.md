---
description: '자세한 정보: 컴파일러 오류 C2110'
title: 컴파일러 오류 C2110
ms.date: 11/04/2016
f1_keywords:
- C2110
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
ms.openlocfilehash: 76bb05ceda7eaae6887e4bfd82ee7d1917598f12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278495"
---
# <a name="compiler-error-c2110"></a>컴파일러 오류 C2110

'+': 두 포인터를 더할 수 없습니다.

더하기( `+` ) 연산자를 사용하여 두 포인터 값을 더하려고 했습니다.

다음 샘플에서는 C2110을 생성합니다.

```cpp
// C2110.cpp
int main() {
   int a = 0;
   int *pa;
   int *pb;
   a = pa + pb;   // C2110
}
```

---
description: '자세한 정보: 컴파일러 오류 C2657'
title: 컴파일러 오류 C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: dfec399c4b65615310263aa58db145b87c42594d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286074"
---
# <a name="compiler-error-c2657"></a>컴파일러 오류 C2657

문의 시작 부분에 ' class::* '이 (가) 있습니다. 형식을 지정 해야 합니다.

줄은 멤버 포인터 식별자로 시작 합니다.

멤버에 대 한 포인터 선언에서 형식 지정 자가 누락 되어이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2657를 생성 합니다.

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```

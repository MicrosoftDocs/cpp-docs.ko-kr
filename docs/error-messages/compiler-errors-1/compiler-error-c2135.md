---
description: '자세한 정보: 컴파일러 오류 C2135'
title: 컴파일러 오류 C2135
ms.date: 11/04/2016
f1_keywords:
- C2135
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
ms.openlocfilehash: 85b8dce9bd735ec7e4e17ce86cd8a03c1a2778c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323114"
---
# <a name="compiler-error-c2135"></a>컴파일러 오류 C2135

'비트 연산자': 비트 필드 연산이 잘못되었습니다.

address-of 연산자(`&`)는 비트 필드에 적용할 수 없습니다.

다음 샘플에서는 C2135를 생성합니다.

```cpp
// C2135.cpp
struct S {
   int i : 1;
};

struct T {
   int j;
};
int main() {
   &S::i;   // C2135 address of a bit field
   &T::j;   // OK
}
```

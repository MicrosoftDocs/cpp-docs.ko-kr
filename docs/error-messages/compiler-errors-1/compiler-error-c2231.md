---
description: '자세한 정보: 컴파일러 오류 C2231'
title: 컴파일러 오류 C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 159f29529fdcf7253fa1af51951c402df1b21823
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194958"
---
# <a name="compiler-error-c2231"></a>컴파일러 오류 C2231

'. ': 왼쪽 피연산자가 ' 클래스-키 '를 가리킵니다. '-> '를 사용 하십시오.

멤버 선택 작업 (.)의 왼쪽에 있는 피연산자는 클래스, 구조체 또는 공용 구조체가 아니라 포인터입니다.

다음 샘플에서는 C2231을 생성합니다.

```c
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```

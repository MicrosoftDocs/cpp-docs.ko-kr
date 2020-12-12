---
description: '자세한 정보: 컴파일러 오류 C2082'
title: 컴파일러 오류 C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 957699338d253ee2438060b27a0089a654fc4f9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316624"
---
# <a name="compiler-error-c2082"></a>컴파일러 오류 C2082

'identifier' 정식 매개 변수 재정의

함수의 정식 매개 변수가 함수 본문 내에서 다시 선언됩니다. 이 오류를 해결하려면 재정의를 제거합니다.

다음 샘플에서는 C2082를 생성합니다.

```cpp
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```

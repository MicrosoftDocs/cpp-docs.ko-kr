---
description: '자세한 정보: 컴파일러 오류 C2198'
title: 컴파일러 오류 C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: 60c07bdaa422a3844bf17355fd88e7924ce05dc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170037"
---
# <a name="compiler-error-c2198"></a>컴파일러 오류 C2198

'function': 호출에 매개 변수가 너무 적습니다.

컴파일러가 함수 호출 매개 변수를 너무 적게 발견했거나 잘못된 함수 선언을 발견했습니다.

다음 샘플에서는 C2198 오류가 발생하는 경우를 보여 줍니다.

```c
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```

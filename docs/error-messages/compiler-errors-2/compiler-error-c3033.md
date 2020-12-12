---
description: '자세한 정보: 컴파일러 오류 C3033'
title: 컴파일러 오류 C3033
ms.date: 11/04/2016
f1_keywords:
- C3033
helpviewer_keywords:
- C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
ms.openlocfilehash: 999cedd270470bde27a57be0159eedda61297092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270240"
---
# <a name="compiler-error-c3033"></a>컴파일러 오류 C3033

'var': 'clause' 절의 변수는 const 한정 형식이 될 수 없습니다.

특정 절에 전달 된 값은 변수가 될 수 없습니다 **`const`** .

다음 샘플에서는 C3033을 생성합니다.

```cpp
// C3033.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   const int val = 1;
   int val2 = 1;

   #pragma omp parallel reduction(+ : val)   // C3033
   ;

   #pragma omp parallel reduction(+ : val2)   // OK
   ;
}
```

---
description: '자세한 정보: 컴파일러 오류 C2197'
title: 컴파일러 오류 C2197
ms.date: 11/04/2016
f1_keywords:
- C2197
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
ms.openlocfilehash: a82a39eba23cae617cf910101f5550fd0f9f0ad4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341921"
---
# <a name="compiler-error-c2197"></a>컴파일러 오류 C2197

'function': 호출에 매개 변수가 너무 많습니다.

컴파일러가 함수 호출 매개 변수를 너무 많이 발견했거나 잘못된 함수 선언을 발견했습니다.

다음 샘플에서는 C2197을 생성합니다.

```c
// C2197.c
// compile with: /Za /c
void func( int );
int main() {
   func( 1, 2 );   // C2197 two actual parameters
   func( 2 );   // OK
}
```

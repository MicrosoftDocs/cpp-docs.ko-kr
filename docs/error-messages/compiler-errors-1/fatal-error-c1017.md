---
title: 심각한 오류 C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756944"
---
# <a name="fatal-error-c1017"></a>심각한 오류 C1017

정수 계열 상수 식이 잘못되었습니다.

`#if` 지시문의 식이 없거나 상수로 계산 되지 않았습니다.

`#define`를 사용 하 여 정의 된 상수는 `#if`, `#elif`또는 `#else` 지시문에서 사용 되는 경우 정수 상수로 계산 되는 값을 가져야 합니다.

다음 샘플에서는 C1017를 생성 합니다.

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

가능한 해결 방법:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

`CONSTANT_NAME`은 정수가 아니라 문자열로 계산 되기 때문에 `#if` 지시문은 심각한 오류 C1017를 생성 합니다.

다른 경우에 전처리기는 정의 되지 않은 상수를 0으로 계산 합니다. 다음 샘플에 표시 된 것 처럼이로 인해 의도 하지 않은 결과가 발생할 수 있습니다. `YES`은 정의 되지 않으므로 0으로 계산 됩니다. 식 `#if` `CONSTANT_NAME`이 false로 평가 되 고 `YES`에 사용 되는 코드가 전처리기에 의해 제거 됩니다. `NO`은 정의 되지 않으므로 (0) `#elif` `CONSTANT_NAME==NO` true (`0 == 0`)로 계산 되어 전처리기가 문의 `#elif` 부분에 코드를 그대로 두기 때문에 의도 된 동작의 반대입니다.

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

컴파일러가 전처리기 지시문을 처리 하는 방식을 정확 하 게 확인 하려면 [/p](../../build/reference/p-preprocess-to-a-file.md), [/e](../../build/reference/e-preprocess-to-stdout.md)또는 [/ep](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)를 사용 합니다.

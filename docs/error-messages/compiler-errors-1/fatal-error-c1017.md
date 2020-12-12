---
description: '자세한 정보: 심각한 오류 C1017'
title: 심각한 오류 C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: a36a5cb11b10ca3ecca00d0379595060918d6a45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262388"
---
# <a name="fatal-error-c1017"></a>심각한 오류 C1017

정수 계열 상수 식이 잘못되었습니다.

지시문의 식이 `#if` 없거나 상수로 계산 되지 않았습니다.

를 사용 하 여 정의 된 상수는 `#define` `#if` , 또는 지시문에서 사용 되는 경우 정수 상수로 계산 되는 값을 가져야 합니다 `#elif` `#else` .

다음 샘플에서는 C1017를 생성 합니다.

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

해결 방법:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

`CONSTANT_NAME`는 정수가 아니라 문자열로 계산 되기 때문에 `#if` 지시문은 심각한 오류 C1017를 생성 합니다.

다른 경우에 전처리기는 정의 되지 않은 상수를 0으로 계산 합니다. 다음 샘플에 표시 된 것 처럼이로 인해 의도 하지 않은 결과가 발생할 수 있습니다. `YES` 은 (는) 정의 되지 않으므로 0으로 계산 됩니다. 식이 `#if` `CONSTANT_NAME` false로 계산 되 고에 사용할 코드가 `YES` 전처리기에 의해 제거 됩니다. `NO` 또한은 (는) 정의 되지 않음 (0)으로 계산 되므로가 `#elif` `CONSTANT_NAME==NO` true ()로 계산 되어 `0 == 0` 전처리기가 문의 부분에 있는 코드를 그대로 유지 하 게 됩니다 `#elif` . 즉, 의도 된 동작과 정확히 반대입니다.

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

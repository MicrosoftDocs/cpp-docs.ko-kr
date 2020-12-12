---
description: '자세한 정보: 컴파일러 오류 C2019'
title: 컴파일러 오류 C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 5b30bdb8eace513572152d0f33da5f591e21bd6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283929"
---
# <a name="compiler-error-c2019"></a>컴파일러 오류 C2019

전처리기 지시문이 있어야 하는데 'character'가 있습니다.

문자는 부호 뒤에 `#` 있지만 전처리기 지시문의 첫 번째 문자가 아닙니다.

다음 샘플에서는 C2019를 생성 합니다.

```cpp
// C2019.cpp
#!define TRUE 1   // C2019
```

해결 방법:

```cpp
// C2019b.cpp
// compile with: /c
#define TRUE 1
```

---
description: '자세한 정보: 컴파일러 오류 C2014'
title: 컴파일러 오류 C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 2f8de1d2b9ea8ef680826cfbfc189dbe2617c9f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220983"
---
# <a name="compiler-error-c2014"></a>컴파일러 오류 C2014

전처리기 명령은 first 공백 아닌 space로 시작 해야 합니다.

`#`전처리기 지시문의 부호는 공백이 아닌 줄의 첫 번째 문자 여야 합니다.

다음 샘플에서는 C2014를 생성 합니다.

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

해결 방법:

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```

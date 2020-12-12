---
description: '자세한 정보: 컴파일러 오류 C2006'
title: 컴파일러 오류 C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 5747f5417db60bd3c1f7bc1420c257552a9b42c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298515"
---
# <a name="compiler-error-c2006"></a>컴파일러 오류 C2006

' 지시어 '에 파일 이름이 필요 하지만 ' token '이 있습니다.

[#Include](../../preprocessor/hash-include-directive-c-cpp.md) 또는 [#import](../../preprocessor/hash-import-directive-cpp.md) 와 같은 지시문에는 파일 이름이 필요 합니다. 오류를 해결 하려면 *token* 이 올바른 파일 이름 인지 확인 합니다. 또한 파일 이름에 큰따옴표 또는 꺾쇠 괄호를 추가 합니다.

다음 샘플에서는 C2006를 생성 합니다.

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

해결 방법:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```

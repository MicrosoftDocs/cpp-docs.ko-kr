---
description: '자세한 정보: 컴파일러 오류 C2008'
title: 컴파일러 오류 C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 3fcde1885fd752a03a1285470a232f1daaa27df2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298528"
---
# <a name="compiler-error-c2008"></a>컴파일러 오류 C2008

'character': 매크로 정의에 사용할 수 없습니다.

문자는 매크로 이름 바로 뒤에 표시 됩니다. 오류를 해결 하려면 매크로 이름 뒤에 공백이 있어야 합니다.

다음 샘플에서는 C2008를 생성 합니다.

```cpp
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

해결 방법:

```cpp
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```

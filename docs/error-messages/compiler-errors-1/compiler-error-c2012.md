---
description: '자세한 정보: 컴파일러 오류 C2012'
title: 컴파일러 오류 C2012
ms.date: 11/04/2016
f1_keywords:
- C2012
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
ms.openlocfilehash: 82f2a5660ec3920c9ff3db57c6ed0b70516c4531
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221009"
---
# <a name="compiler-error-c2012"></a>컴파일러 오류 C2012

' < ' 뒤에 이름이 없습니다.

`#include` 지시문에 필요한 파일 이름이 없습니다.

다음 샘플에서는 C2012를 생성합니다.

```cpp
// C2012.cpp
#include <   // C2012 include the filename to resolve
```

해결 방법:

```cpp
// C2012b.cpp
// compile with: /c
#include <stdio.h>
```

---
title: 컴파일러 오류 C2133 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2133
dev_langs:
- C++
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169b24787f1b180c7ba70c5d779e341e60ea2150
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025193"
---
# <a name="compiler-error-c2133"></a>컴파일러 오류 C2133

'identifier': 알 수 없는 크기

크기가 지정 되지 않은 배열은 클래스, 구조체, 공용 구조체 또는 열거형의 멤버로 선언 됩니다. /Za (ANSI C) 옵션에는 크기가 지정 되지 않은 멤버 배열 허용 하지 않습니다.

다음 샘플에서는 C2133 오류가 생성 됩니다.

```
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

해결 방법:

```
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```
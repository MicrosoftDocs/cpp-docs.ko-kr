---
description: '자세한 정보: 컴파일러 오류 C2199'
title: 컴파일러 오류 C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: e3c1daefb8a8b14c49b42e48c0d46d5a8e638953
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278425"
---
# <a name="compiler-error-c2199"></a>컴파일러 오류 C2199

구문 오류: 전역 범위에 ' identifier '가 있습니다. (선언이 의도 된 것 입니까?)

지정 된 컨텍스트에 구문 오류가 발생 했습니다. 잘못 된 선언 구문이 있을 수 있습니다.

다음 샘플에서는 C2199를 생성 합니다.

```cpp
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```

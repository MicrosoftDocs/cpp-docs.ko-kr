---
description: '자세한 정보: 컴파일러 오류 C2090'
title: 컴파일러 오류 C2090
ms.date: 11/04/2016
f1_keywords:
- C2090
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
ms.openlocfilehash: 224f900a20d57a35a6a6c6dcc2dc95b09c596403
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251910"
---
# <a name="compiler-error-c2090"></a>컴파일러 오류 C2090

함수가 배열을 반환 합니다.

함수는 배열을 반환할 수 없습니다. 대신 배열에 대 한 포인터를 반환 합니다.

다음 샘플에서는 C2090를 생성 합니다.

```cpp
// C2090.cpp
int func1(void)[] {}   // C2090
```

해결 방법:

```cpp
// C2090b.cpp
// compile with: /c
int* func2(int * i) {
   return i;
}
```

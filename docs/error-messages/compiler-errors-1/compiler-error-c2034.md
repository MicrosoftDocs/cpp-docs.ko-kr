---
description: '자세한 정보: 컴파일러 오류 C2034'
title: 컴파일러 오류 C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: cbc3f8788e495a95b1eb5fb848322815b6f78d57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175419"
---
# <a name="compiler-error-c2034"></a>컴파일러 오류 C2034

' identifier ': 비트 필드의 형식이 비트 수에 비해 너무 작습니다.

비트 필드 선언의 비트 수가 기본 형식의 크기를 초과 합니다.

다음 샘플에서는 C2034를 생성 합니다.

```cpp
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

해결 방법:

```cpp
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```

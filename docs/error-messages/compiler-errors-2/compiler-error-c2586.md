---
description: '자세한 정보: 컴파일러 오류 C2586'
title: 컴파일러 오류 C2586
ms.date: 11/04/2016
f1_keywords:
- C2586
helpviewer_keywords:
- C2586
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
ms.openlocfilehash: bcf0c374936c994773f0c2d2afa56924d6ca9f4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177616"
---
# <a name="compiler-error-c2586"></a>컴파일러 오류 C2586

사용자 정의 변환 구문이 잘못 되었습니다. 간접 참조가 잘못 되었습니다.

변환 연산자의 간접 참조는 허용 되지 않습니다.

다음 샘플에서는 C2586를 생성 합니다.

```cpp
// c2586.cpp
// compile with: /c
struct C {
   * operator int();   // C2586
   operator char();   // OK
};
```

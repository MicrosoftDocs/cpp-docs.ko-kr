---
description: '자세한 정보: 컴파일러 오류 C2277'
title: 컴파일러 오류 C2277
ms.date: 11/04/2016
f1_keywords:
- C2277
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
ms.openlocfilehash: e5113587b22373eae4a197b5913430659447810a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344434"
---
# <a name="compiler-error-c2277"></a>컴파일러 오류 C2277

' identifier ':이 멤버 함수의 주소를 가져올 수 없습니다.

멤버 함수의 주소를 가져올 수 없습니다.

다음 샘플에서는 C2277를 생성 합니다.

```cpp
// C2277.cpp
class A {
public:
   A();
};
(*pctor)() = &A::A;   // C2277
```

---
description: '자세한 정보: 컴파일러 오류 C2807'
title: 컴파일러 오류 C2807
ms.date: 11/04/2016
f1_keywords:
- C2807
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
ms.openlocfilehash: 8ce98ee69bf3c41e822a5ecc40dc794b443b6ff0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320625"
---
# <a name="compiler-error-c2807"></a>컴파일러 오류 C2807

후 위 ' operator operator '의 두 번째 형식 매개 변수는 ' i n t ' 여야 합니다.

후 위 연산자에 대 한 두 번째 매개 변수의 형식이 잘못 되었습니다.

다음 샘플에서는 C2807를 생성 합니다.

```cpp
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```

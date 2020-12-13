---
description: '자세한 정보: 컴파일러 오류 C2186'
title: 컴파일러 오류 C2186
ms.date: 11/04/2016
f1_keywords:
- C2186
helpviewer_keywords:
- C2186
ms.assetid: 284bfb7e-ab85-4fcb-9864-1ddf7f6c94ae
ms.openlocfilehash: 2a6348993ee096bc3cadaaf87838fd81091225f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335118"
---
# <a name="compiler-error-c2186"></a>컴파일러 오류 C2186

'operator': 'void' 형식의 피연산자가 잘못되었습니다.

연산자에 피연산자가 **`void`** 있습니다.

다음 샘플에서는 C2186을 생성합니다.

```cpp
// C2186.cpp
// compile with: /c
void func1( void );
int  func2( void );
int i = 2 + func1();   // C2186 func1() is type void
int j = 2 + func2();   // OK both operands are type int
```

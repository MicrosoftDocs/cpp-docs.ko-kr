---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4674'
title: 컴파일러 경고(수준 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: 1df7dd982f52a6987e06e888130953c1a9deb330
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334975"
---
# <a name="compiler-warning-level-1-c4674"></a>컴파일러 경고(수준 1) C4674

'method'는 'static'으로 선언해야 하며 하나의 매개 변수만 가져야 합니다.

변환 연산자의 서명이 잘못되었습니다. 메서드는 사용자 정의 변환으로 간주되지 않습니다. 연산자를 정의 하는 방법에 대 한 자세한 내용은 [사용자 정의 연산자 (c + +/cli)](../../dotnet/user-defined-operators-cpp-cli.md) 및 [사용자 정의 변환 (c + +/cli)](../../dotnet/user-defined-conversions-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4674를 생성합니다.

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```

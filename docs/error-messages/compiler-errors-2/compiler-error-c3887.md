---
description: '자세한 정보: 컴파일러 오류 C3887'
title: 컴파일러 오류 C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: 8c80a1ff54f56e111934ebc370fee28f011bd37b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274348"
---
# <a name="compiler-error-c3887"></a>컴파일러 오류 C3887

' var ': 리터럴 데이터 멤버에 대 한 이니셜라이저는 상수 식 이어야 합니다.

[리터럴](../../extensions/literal-cpp-component-extensions.md) 데이터 멤버는 상수 식 초기화할 수 있습니다.

다음 샘플에서는 C3887를 생성 합니다.

```cpp
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

해결 방법:

```cpp
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```

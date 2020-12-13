---
description: '자세한 정보: 컴파일러 오류 C3320'
title: 컴파일러 오류 C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 2dde804792dec4f7a1564c680a45c78adf60eedf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337371"
---
# <a name="compiler-error-c3320"></a>컴파일러 오류 C3320

'type': 형식은 모듈의 'name' 속성과 같은 이름을 사용할 수 없습니다.

구조체, 클래스, 열거형 또는 공용 구조체 일 수 있는 내보낸 UDT (사용자 정의 형식)는 [module](../../windows/attributes/module-cpp.md) 특성의 이름 속성에 전달 된 매개 변수와 동일한 이름을 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3320을 생성합니다.

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```

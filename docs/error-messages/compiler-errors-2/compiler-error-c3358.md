---
description: '자세한 정보: 컴파일러 오류 C3358'
title: 컴파일러 오류 C3358
ms.date: 11/04/2016
f1_keywords:
- C3358
helpviewer_keywords:
- C3358
ms.assetid: 180b93df-e78f-441a-91fb-1594c681f7f0
ms.openlocfilehash: 44f72336f150f55cb8338fdeaa3edef4e81a601d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150880"
---
# <a name="compiler-error-c3358"></a>컴파일러 오류 C3358

'symbol': 기호를 찾을 수 없습니다.

필요한 기호를 찾을 수 없습니다.

다음 샘플에서는 C3358을 생성합니다.

```cpp
// C3358.cpp
#define __ATLEVENT_H__ 1   // remove this line to resolve the error
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[event_receiver(com)]
struct A   // C3358
{
   void func();
};

int main()
{
}
```

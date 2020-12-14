---
description: '자세한 정보: 컴파일러 오류 C3136'
title: 컴파일러 오류 C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 4203eaa1f41603075bbb8162b7156783c8f2680a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239378"
---
# <a name="compiler-error-c3136"></a>컴파일러 오류 C3136

' interface ': COM 인터페이스는 다른 COM 인터페이스 에서만 상속할 수 있습니다. ' interface '는 COM 인터페이스가 아닙니다.

[인터페이스 특성](../../windows/attributes/interface-attributes.md) 을 적용 한 인터페이스는 COM 인터페이스가 아닌 인터페이스에서 상속 됩니다. COM 인터페이스는 궁극적으로에서 상속 `IUnknown` 됩니다. 인터페이스 특성 뒤에 오는 모든 인터페이스는 COM 인터페이스입니다.

다음 예제에서는 C3136를 생성 합니다.

```cpp
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```

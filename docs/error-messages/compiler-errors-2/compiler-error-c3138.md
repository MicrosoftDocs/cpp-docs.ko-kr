---
description: '자세한 정보: 컴파일러 오류 C3138'
title: 컴파일러 오류 C3138
ms.date: 11/04/2016
f1_keywords:
- C3138
helpviewer_keywords:
- C3138
ms.assetid: 364ee9e8-9358-410e-bd35-9c4a226a3753
ms.openlocfilehash: 07fa48cc4c14773eeb41420eb63d659028de8caf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304261"
---
# <a name="compiler-error-c3138"></a>컴파일러 오류 C3138

' interface ': ' attribute ' 인터페이스는 IDispatch에서 상속 하거나 IDispatch에서 상속 하는 인터페이스에서 상속 해야 합니다.

[Dual](../../windows/attributes/dual.md) [또는 특성이 있는](../../windows/attributes/dispinterface.md) 인터페이스에는 `IDispatch` 직접 또는 간접 기본 인터페이스가 없습니다.

다음 예제에서는 C3138를 생성 합니다.

```cpp
// C3138.cpp
#include <unknwn.h>

[ object, uuid("77ac9240-6e9a-11d2-97de-0000f805d73b") ]
__interface IMyCustomInterface
{
   HRESULT mf1(void);
};

[ dispinterface, uuid("3536f8a0-6e9a-11d2-97de-0000f805d73b") ]
__interface IMyDispInterface : IUnknown
{
   [id(1)] HRESULT mf2(void);
};

[ object, dual, uuid("34e90a10-6e9a-11d2-97de-0000f805d73b") ]
__interface IMyDualInterface : IMyCustomInterface  // C3138 expected
{
   HRESULT mf3(void);
};
```

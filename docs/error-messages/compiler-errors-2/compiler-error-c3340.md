---
description: '자세한 정보: 컴파일러 오류 C3340'
title: 컴파일러 오류 C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: 3c944d8d61a93fb3985e85e946f147eecd56624a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337314"
---
# <a name="compiler-error-c3340"></a>컴파일러 오류 C3340

'interface': 인터페이스는 coclass 'class'에서 'restricted'이면서 'default'일 수 없습니다.

[restricted](../../windows/attributes/restricted.md) 특성 및 [default](../../windows/attributes/default-cpp.md) 특성은 함께 사용할 수 없습니다.

다음 샘플에서는 C3340을 생성합니다.

```cpp
// C3340.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   HRESULT f1();
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),
default(IMyIface),
source(IMyIface),restricted(IMyIface) ]
class CmyClass // C3340
{
};

int main()
{
}
```

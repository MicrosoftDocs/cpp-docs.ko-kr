---
title: 컴파일러 오류 C3340 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3340
dev_langs:
- C++
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7630e8fb647e52a1b6e355d413c8fb666277e82
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066091"
---
# <a name="compiler-error-c3340"></a>컴파일러 오류 C3340

'interface': 인터페이스는 coclass 'class'에서 'restricted'이면서 'default'일 수 없습니다.

[restricted](../../windows/restricted.md) 특성 및 [default](../../windows/default-cpp.md) 특성은 함께 사용할 수 없습니다.

다음 샘플에서는 C3340을 생성합니다.

```
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
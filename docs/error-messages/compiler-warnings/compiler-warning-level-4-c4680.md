---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4680'
title: 컴파일러 경고(수준 4) C4680
ms.date: 11/04/2016
f1_keywords:
- C4680
helpviewer_keywords:
- C4680
ms.assetid: 6e043f4c-c601-4b77-8130-920cff1d912e
ms.openlocfilehash: 85f14273efb2b7d91a6b663e69918b77bcb7c597
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133876"
---
# <a name="compiler-warning-level-4-c4680"></a>컴파일러 경고(수준 4) C4680

' class ': coclass가 기본 인터페이스를 지정 하지 않습니다.

[Coclass](../../windows/attributes/coclass.md) 특성으로 표시 된 클래스에 대해 [기본](../../windows/attributes/default-cpp.md) 인터페이스를 지정 하지 않았습니다. 개체를 유용 하 게 적용 하려면 인터페이스를 구현 해야 합니다.

다음 샘플에서는 C4680를 생성 합니다.

```cpp
// C4680.cpp
// compile with: /W4
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface1
{
   HRESULT f1();
};

[ object, uuid(37331a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface2
{
   HRESULT f1();
};

// to resolve C4680, specify a source interface also
// for example, default(IMyIface1, IMyface2)
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), default(IMyIface1), source(IMyIface1) ]
class CMyClass : public IMyIface1
{   // C4680
};

int main()
{
}
```

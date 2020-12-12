---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4912'
title: 컴파일러 경고(수준 1) C4912
ms.date: 11/04/2016
f1_keywords:
- C4912
helpviewer_keywords:
- C4912
ms.assetid: ba1f1a66-8c20-4792-9ac8-43e49f729ae2
ms.openlocfilehash: 85300716894f9c69815bf40ebb7d93ee29d8684b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291443"
---
# <a name="compiler-warning-level-1-c4912"></a>컴파일러 경고(수준 1) C4912

'attribute': 특성의 중첩 UDT에 정의되지 않은 동작이 있습니다.

중첩 UDT(typedef, 공용 구조체 또는 구조체일 수 있는 사용자 정의 형식)에 적용되는 특성을 무시할 수 있습니다.

다음 코드에서는 이 경고를 생성하는 방법을 보여 줍니다.

```cpp
// C4912.cpp
// compile with: /W1
#include <windows.h>
[emitidl, module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMy
{
};

[coclass, default(IMy), appobject, uuid("00000000-0000-0000-0000-000000000001")]
class CMy : public IMy
{
   [export, v1_enum] typedef enum myEnum { k3_1 = 1, k3_2 = 2 } myEnumv;   // C4912
};
int main()
{
}
```

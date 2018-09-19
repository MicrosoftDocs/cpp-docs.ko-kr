---
title: 컴파일러 경고 (수준 1) C4912 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4912
dev_langs:
- C++
helpviewer_keywords:
- C4912
ms.assetid: ba1f1a66-8c20-4792-9ac8-43e49f729ae2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c80e7d3a6f9e3f97b05e1ec9e966de7f6d8a388d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047111"
---
# <a name="compiler-warning-level-1-c4912"></a>컴파일러 경고(수준 1) C4912

'attribute': 특성의 중첩 UDT에 정의되지 않은 동작이 있습니다.

중첩 UDT(typedef, 공용 구조체 또는 구조체일 수 있는 사용자 정의 형식)에 적용되는 특성을 무시할 수 있습니다.

다음 코드에서는 이 경고를 생성하는 방법을 보여 줍니다.

```
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
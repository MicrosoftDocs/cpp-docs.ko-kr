---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4096'
title: 컴파일러 경고 (수준 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 2d787a2de5974b16fb962c17530532480d993fd6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278040"
---
# <a name="compiler-warning-level-1-c4096"></a>컴파일러 경고 (수준 1) C4096

' a ': 인터페이스가 COM 인터페이스가 아닙니다. IDL로 내보내지 않습니다.

COM 인터페이스로 사용 했을 수 있는 인터페이스 정의가 COM 인터페이스로 정의 되지 않았으므로 IDL 파일로 내보내지 않습니다.

인터페이스를 COM 인터페이스로 지정 하는 목록 특성에 대 한 [인터페이스 특성](../../windows/attributes/interface-attributes.md) 을 참조 하세요.

다음 샘플에서는 C4096를 생성 합니다.

```cpp
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```

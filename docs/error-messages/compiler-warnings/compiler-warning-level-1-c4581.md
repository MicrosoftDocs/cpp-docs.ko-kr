---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4581'
title: 컴파일러 경고(수준 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 6fffa3f7ea74cb17eae7fe4af2575e1d574084fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332223"
---
# <a name="compiler-warning-level-1-c4581"></a>컴파일러 경고(수준 1) C4581

사용 되지 않는 동작: ' "string1" '이 (가) ' n a l l '로 바뀌어 특성을 처리

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. Visual C++ 특성에 대 한 매개 변수 검사입니다.

이전 버전에서 특성 값은 따옴표로 묶여 있는지 여부에 관계 없이 수락 되었습니다. 값이 열거형 인 경우 따옴표로 묶지 않아야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4581를 생성 합니다.

```cpp
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```

---
description: '자세한 정보: 컴파일러 오류 C2490'
title: 컴파일러 오류 C2490
ms.date: 11/04/2016
f1_keywords:
- C2490
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
ms.openlocfilehash: 9638b65eb453fcc957ac2e9a947138ba1f7ac745
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339347"
---
# <a name="compiler-error-c2490"></a>컴파일러 오류 C2490

' t o k e n '은 ' naked ' 특성이 있는 함수에 사용할 수 없습니다.

[Naked](../../cpp/naked-cpp.md) 로 정의 된 함수는 구조적 예외 처리를 사용할 수 없습니다.

다음 샘플에서는 C2490를 생성 합니다.

```cpp
// C2490.cpp
// processor: x86
__declspec( naked ) int func() {
   __try{}   // C2490, structured exception handling
}
```

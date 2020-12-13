---
description: '자세한 정보: 컴파일러 오류 C2867'
title: 컴파일러 오류 C2867
ms.date: 11/04/2016
f1_keywords:
- C2867
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
ms.openlocfilehash: 81ccb96e60a412a84c76ba542fab980b9210a054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333808"
---
# <a name="compiler-error-c2867"></a>컴파일러 오류 C2867

' identifier ': 네임 스페이스가 아닙니다.

**`using`** 지시문은 네임 스페이스 이외의 다른 항목에 적용 됩니다.

다음 샘플에서는 C2867를 생성 합니다.

```cpp
// C2867.cpp
// compile with: /c
namespace N {
   class X {};
}
using namespace N::X;   // C2867
```

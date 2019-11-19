---
title: 컴파일러 경고 (수준 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: 3c13eb28981779e2d089575660d8968c54e4e75f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051474"
---
# <a name="compiler-warning-level-1-c4616"></a>컴파일러 경고 (수준 1) C4616

\#pragma warning: 경고 번호 ' number '은 (는) 올바른 컴파일러 경고가 아닙니다.

[경고](../../preprocessor/warning.md) pragma에 지정 된 경고 번호를 다시 할당할 수 없습니다. Pragma가 무시 되었습니다.

다음 샘플에서는 C4616를 생성 합니다.

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```
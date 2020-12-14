---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4440'
title: 컴파일러 경고(수준 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: 9e0a126ea1461e0b98bcef5117b893ea232fe262
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311047"
---
# <a name="compiler-warning-level-1-c4440"></a>컴파일러 경고(수준 1) C4440

' calling_convention1 '에서 ' calling_convention2 ' (으)로의 규칙 재정의 호출이 무시 되었습니다.

호출 규칙을 변경 하려는 시도가 무시 되었습니다.

다음 샘플에서는 C4440를 생성 합니다.

```cpp
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```

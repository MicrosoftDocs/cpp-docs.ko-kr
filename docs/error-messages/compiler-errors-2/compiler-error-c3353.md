---
description: '자세한 정보: 컴파일러 오류 C3353'
title: 컴파일러 오류 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 50ff7a6b104f3e16ce17f1398da49a146c0d41a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335038"
---
# <a name="compiler-error-c3353"></a>컴파일러 오류 C3353

'delegate': 대리자는 전역 함수 또는 관리되는 또는 WinRT 형식의 멤버 함수에서만 만들어질 수 있습니다.

[Delegate](../../extensions/delegate-cpp-component-extensions.md) 키워드로 선언 된 대리자는 전역 범위 에서만 선언할 수 있습니다.

다음 샘플에서는 C3353을 생성합니다.

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```

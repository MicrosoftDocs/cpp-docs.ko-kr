---
description: '자세한 정보: 컴파일러 오류 C3865'
title: 컴파일러 오류 C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 956cbfeb5bac97cae7e9a9a411c29326062e15b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222881"
---
# <a name="compiler-error-c3865"></a>컴파일러 오류 C3865

' calling_convention ': 네이티브 멤버 함수에만 사용할 수 있습니다.

호출 규칙은 전역 함수 또는 관리 되는 멤버 함수에 대 한 함수에서 사용 되었습니다. 호출 규칙은 네이티브 (관리 되지 않는) 멤버 함수 에서만 사용할 수 있습니다.

자세한 내용은 [호출 규칙](../../cpp/calling-conventions.md)을 참조 하세요.

다음 샘플에서는 C3865를 생성 합니다.

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```

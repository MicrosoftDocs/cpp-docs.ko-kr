---
description: '자세한 정보: 컴파일러 오류 C2582'
title: 컴파일러 오류 C2582
ms.date: 11/04/2016
f1_keywords:
- C2582
helpviewer_keywords:
- C2582
ms.assetid: ee1b9378-8bcd-4792-b87e-6d7a466d29ed
ms.openlocfilehash: 97020c7ea9209da6524d5a0a7c8c05aa1c76d37d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177720"
---
# <a name="compiler-error-c2582"></a>컴파일러 오류 C2582

' function ' 함수는 ' type '에서 사용할 수 없습니다.

할당 연산자가 없는 개체에 할당 하려고 한 경우

다음 샘플에서는 C2582를 생성 합니다.

```cpp
// C2582.cpp
// compile with: /clr
using namespace System;

struct N {};
ref struct O {};
ref struct R {
   property O prop;   // C2582
   property O ^ prop2;   // OK
};

int main() {
   String ^ st1 = gcnew String("");
   ^st1 = gcnew String("");   // C2582
   st1 = "xxx";   // OK
}
```

---
description: '자세한 정보: 컴파일러 오류 C3623'
title: 컴파일러 오류 C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: 042e530dc1529307c90b05771d662aaed4b60775
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222985"
---
# <a name="compiler-error-c3623"></a>컴파일러 오류 C3623

'variable': 관리되는 형식 또는 WinRT 형식에서는 비트 필드가 지원되지 않습니다.

'variable': 관리되는 클래스 또는 WinRT 클래스의 변수에서는 비트 필드를 사용할 수 없습니다.

다음 샘플에서는 C3623 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```

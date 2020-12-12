---
description: '자세한 정보: 컴파일러 오류 C3842'
title: 컴파일러 오류 C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: dd5cff7b4a381ca976138720d8af192d594c7836
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255420"
---
# <a name="compiler-error-c3842"></a>컴파일러 오류 C3842

'function': WinRT 또는 관리되는 형식의 멤버 함수에 'const' 및 'volatile' 한정자를 사용할 수 없습니다.

[const](../../cpp/const-cpp.md) 및 [volatile](../../cpp/volatile-cpp.md) 은 Windows 런타임 또는 관리 되는 형식의 멤버 함수에서 지원 되지 않습니다.

다음 샘플에서는 C3842를 생성합니다.

```cpp
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```

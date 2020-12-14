---
description: '자세한 정보: 컴파일러 오류 C3192'
title: 컴파일러 오류 C3192
ms.date: 11/04/2016
f1_keywords:
- C3192
helpviewer_keywords:
- C3192
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
ms.openlocfilehash: fc88480a7ef799ced07dc52491b394b432e6525e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241913"
---
# <a name="compiler-error-c3192"></a>컴파일러 오류 C3192

구문 오류: ' ^ '은 (는) 전위 연산자가 아닙니다 (' * '를 의미 함).

핸들은 역참조 연산자로 사용할 수 없습니다.

다음 샘플에서는 C3192를 생성 합니다.

```cpp
// C3192.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   MyClass () {}
   MyClass(MyClass%) {}
};

int main() {
   MyClass ^ s = gcnew MyClass;
   MyClass b = ^s;   // C3192

   // OK
   MyClass b2 = *s;
}
```

---
description: '자세한 정보: 컴파일러 오류 C3379'
title: 컴파일러 오류 C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 622a1327eb84d83fa24d8a084e3266183c669120
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220736"
---
# <a name="compiler-error-c3379"></a>컴파일러 오류 C3379

' class ': 중첩 된 클래스는 해당 선언의 일부로 어셈블리 액세스 지정자를 사용할 수 없습니다.

클래스 또는 구조체와 같은 관리 되는 형식에 적용 하는 경우 [public](../../cpp/public-cpp.md) 및 [private](../../cpp/private-cpp.md) 키워드는 클래스가 어셈블리 메타 데이터를 통해 노출 되는지 여부를 나타냅니다. `public` 또는는 `private` 바깥쪽 클래스의 어셈블리 액세스를 상속 하는 중첩 된 클래스에 적용할 수 없습니다.

[/Clr](../../build/reference/clr-common-language-runtime-compilation.md)과 함께 사용 하는 경우 `ref` 및 키워드는 클래스가 관리 됨을 나타내고, 클래스 `value` [및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3379를 생성 합니다.

```cpp
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```

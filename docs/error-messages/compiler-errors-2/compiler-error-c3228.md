---
title: 컴파일러 오류 C3228 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3228
dev_langs:
- C++
helpviewer_keywords:
- C3228
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1818cbae07af904a468447e16fcb95384e5dcd17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054690"
---
# <a name="compiler-error-c3228"></a>컴파일러 오류 C3228

'function': 'param'에 대한 제네릭 형식 인수는 'type'일 수 없으며 값 형식이거나 핸들 형식이어야 합니다.

잘못된 형식이 제네릭 형식 인수로 전달되었습니다.

다음 샘플에서는 C3228을 생성합니다.

```
// C3228.cpp
// compile with: /clr
class A {};

value class B {};

generic <class T>
void Test() {}

ref class C {
public:
   generic <class T>
   static void f() {}
};

int main() {
   C::f<A>();   // C3228
   C::f<B>();   // OK

   Test<C>();   // C3228
   Test<C ^>();   // OK
}
```
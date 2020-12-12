---
description: '자세한 정보: 컴파일러 오류 C3214'
title: 컴파일러 오류 C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: 8f1b558b37e3a9f4daa08ecdd2f90b0f7a74a2a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173820"
---
# <a name="compiler-error-c3214"></a>컴파일러 오류 C3214

'type': 제네릭 'generic_type'의 제네릭 매개 변수 'param'에 대한 형식 인수가 잘못되었습니다. 제약 조건 'constraint'에 맞지 않습니다.

제네릭 클래스의 인스턴스화에 대해 제네릭 클래스의 제약 조건을 충족하지 않는 형식을 지정했습니다.

다음 샘플에서는 C3214를 생성합니다.

```cpp
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```

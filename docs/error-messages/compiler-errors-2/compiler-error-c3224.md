---
description: '자세한 정보: 컴파일러 오류 C3224'
title: 컴파일러 오류 C3224
ms.date: 11/04/2016
f1_keywords:
- C3224
helpviewer_keywords:
- C3224
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
ms.openlocfilehash: c6495a4bdd51115e679d0c9bd68bd370e3aebfd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239300"
---
# <a name="compiler-error-c3224"></a>컴파일러 오류 C3224

'type': 'number'개의 제네릭 형식 인수를 사용하는 오버로드된 제네릭 클래스가 없습니다.

컴파일러가 적절한 오버로드를 찾지 못했습니다.

다음 샘플에서는 C3224를 생성합니다.

```
// C3224.cs
// compile with: /target:library
public class C<T> {}
public class C<T,U> {}
```

그리고

```cpp
// C3224b.cpp
// compile with: /clr
#using "C3224.dll"
int main() {
   C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224
   C<int,int>^ c2 = gcnew C<int,int>();   // OK
}
```

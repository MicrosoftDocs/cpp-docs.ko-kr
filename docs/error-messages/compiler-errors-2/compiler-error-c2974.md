---
description: '자세한 정보: 컴파일러 오류 C2974'
title: 컴파일러 오류 C2974
ms.date: 11/04/2016
f1_keywords:
- C2974
helpviewer_keywords:
- C2974
ms.assetid: 1b444260-f2bf-48d7-ab1e-35573d8c4a0e
ms.openlocfilehash: 0f6d455a2ca79c4c830b24641a894356a5ef04b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210363"
---
# <a name="compiler-error-c2974"></a>컴파일러 오류 C2974

' number ' 형식 인수가 잘못 되었습니다. 형식이 필요 합니다.

제네릭 또는 템플릿 인수가 제네릭 또는 템플릿 선언과 일치 하지 않습니다. 형식은 꺾쇠 괄호 안에 표시 되어야 합니다. 제네릭 또는 템플릿 정의를 확인 하 여 올바른 형식을 찾습니다.

다음 샘플에서는 C2974를 생성 합니다.

```cpp
// C2974.cpp
// C2974 expected
template <class T>
struct TC {};

template <typename T>
void tf(T){}

int main() {
   // Delete the following 2 lines to resolve
   TC<1>* tc;
   tf<"abc">("abc");

   TC<int>* tc;
   tf<const char *>("abc");
}
```

제네릭을 사용 하는 경우에도 C2974이 발생할 수 있습니다.

```cpp
// C2974b.cpp
// compile with: /clr
// C2974 expected
using namespace System;
generic <class T>
ref struct GCtype {};

generic <typename T>
void gf(T){}

int main() {
   // Delete the following 2 lines to resolve
   GCtype<"a">^ gc;
   gf<"a">("abc");

   // OK
   GCtype<int>^ gc;
   gf<String ^>("abc");
}
```

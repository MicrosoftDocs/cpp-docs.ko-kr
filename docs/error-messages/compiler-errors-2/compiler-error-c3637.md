---
description: '자세한 정보: 컴파일러 오류 C3637'
title: 컴파일러 오류 C3637
ms.date: 11/04/2016
f1_keywords:
- C3637
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
ms.openlocfilehash: d62612778690984245d6b90fc1449177ec5f8d2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239209"
---
# <a name="compiler-error-c3637"></a>컴파일러 오류 C3637

' function ': friend 함수 정의는 함수 형식의 특수화 일 수 없습니다.

Friend 함수가 템플릿 또는 제네릭에 대해 잘못 정의 되었습니다.

다음 샘플에서는 C3637를 생성 합니다.

```cpp
// C3637.cpp
template <class T>
void f();

struct S {
   friend void f<int>() {}   // C3637
};
```

해결 방법:

```cpp
// C3637b.cpp
// compile with: /c
template <class T>
void f();

struct S {
   friend void f() {}
};
```

제네릭을 사용 하는 경우에도 C3637이 발생할 수 있습니다.

```cpp
// C3637c.cpp
// compile with: /clr

generic <class T>
void gf();

struct S {
   friend void gf<int>() {}   // C3637
};
```

해결 방법:

```cpp
// C3637d.cpp
// compile with: /clr /c
generic <class T>
void gf();

struct S {
   friend void gf() {}
};
```

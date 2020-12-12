---
description: '자세한 정보: 컴파일러 오류 C2914'
title: 컴파일러 오류 C2914
ms.date: 11/04/2016
f1_keywords:
- C2914
helpviewer_keywords:
- C2914
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
ms.openlocfilehash: 7ff40982a8c6d93130265795fa334dbbc9c21cc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270448"
---
# <a name="compiler-error-c2914"></a>컴파일러 오류 C2914

' identifier ': 함수 인수가 모호 하기 때문에 형식 인수를 추론할 수 없습니다.

컴파일러가 제네릭 또는 템플릿 인수에 사용할 오버 로드 된 함수를 확인할 수 없습니다.

다음 샘플에서는 C2914를 생성 합니다.

```cpp
// C2914.cpp
// compile with: /c
void f(int);
void f(double);
template<class T> void g(void (*) (T));
void h() { g(f); }   // C2914
// try the following line instead
// void h() { g<int>(f); }
```

제네릭을 사용 하는 경우에도 C2914이 발생할 수 있습니다.  다음 샘플에서는 C2914를 생성 합니다.

```cpp
// C2914b.cpp
// compile with: /clr /c
void f(int);
void f(double);

template<class T>
void gf(void (*) (T));

void h() { gf(f);}   // C2914
// try the following line instead
void h() { gf<int>(f); }
```

---
description: '자세한 정보: 컴파일러 오류 C2073'
title: 컴파일러 오류 C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 791f07040b0a0dd70d2cb0aa8373eb6c342c5b97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209167"
---
# <a name="compiler-error-c2073"></a>컴파일러 오류 C2073

' identifier ': 부분적으로 초기화 된 배열의 요소에는 기본 생성자가 있어야 합니다.

사용자 정의 형식 또는 상수의 배열에 대해 이니셜라이저가 너무 적게 지정 되었습니다. 명시적 이니셜라이저와 해당 생성자가 배열 멤버에 대해 지정 되지 않은 경우 기본 생성자를 제공 해야 합니다.

다음 샘플에서는 C2073를 생성 합니다.

```cpp
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```cpp
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```

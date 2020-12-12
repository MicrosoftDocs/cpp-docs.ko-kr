---
description: '자세한 정보: 컴파일러 오류 C2593'
title: 컴파일러 오류 C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 849cd79b1d469d957cf1bde499ce66bd54a64074
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120167"
---
# <a name="compiler-error-c2593"></a>컴파일러 오류 C2593

' operator identifier '가 모호 합니다.

오버 로드 된 연산자에 대해 둘 이상의 가능한 연산자가 정의 되었습니다.

하나 이상의 실제 매개 변수에 명시적 캐스트를 사용 하는 경우이 오류를 해결할 수 있습니다.

다음 샘플에서는 C2593를 생성 합니다.

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

이 오류는 개체를 사용 하 여 부동 소수점 변수를 serialize 하는 경우에 발생할 수 있습니다 `CArchive` . 컴파일러는 연산자를 `<<` 모호한 것으로 식별 합니다. Serialize 할 수 있는 유일한 기본 c + + 형식은 `CArchive` 고정 크기 형식인, `BYTE` , `WORD` `DWORD` 및 `LONG` 입니다. 모든 정수 형식은 serialization을 위해 이러한 형식 중 하나로 캐스팅 되어야 합니다. 부동 소수점 형식은 멤버 함수를 사용 하 여 보관 해야 합니다 `CArchive::Write()` .

다음 예제에서는 부동 소수점 변수 ()를 보관 하는 방법을 보여 줍니다 `f` `ar` .

```
ar.Write(&f, sizeof( float ));
```

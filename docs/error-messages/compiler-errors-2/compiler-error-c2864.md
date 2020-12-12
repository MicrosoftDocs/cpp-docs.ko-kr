---
description: '자세한 정보: 컴파일러 오류 C2864'
title: 컴파일러 오류 C2864
ms.date: 10/04/2019
f1_keywords:
- C2864
helpviewer_keywords:
- C2864
ms.assetid: d0ca2ad9-90a6-4aef-8511-98a3b414c102
ms.openlocfilehash: 763e70fd3ac988cca94f71feeab975e8b8630402
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305366"
---
# <a name="compiler-error-c2864"></a>컴파일러 오류 C2864

> '*멤버 이름*': in 클래스 이니셜라이저가 있는 정적 데이터 멤버는 volatile이 아닌 const 정수 계열 형식을 포함 해야 합니다.

## <a name="remarks"></a>설명

,가 **`static`** 아닌 또는 정수 계열 형식으로 정의 된 데이터 멤버를 초기화 하려면 **`volatile`** **`const`** 멤버 정의 문을 사용 합니다. 선언에서 초기화할 수 없습니다.

## <a name="example"></a>예제

이 샘플에서는 C2864를 생성 합니다.

```cpp
// C2864.cpp
// compile with: /c
class B  {
private:
   int a = 3;   // OK
   static int b = 3;   // C2864
   volatile static int c = 3;   // C2864
   volatile static const int d = 3;   // C2864
   static const long long e = 3;   // OK
   static const double f = 3.33;   // C2864
};
```

이 샘플에서는 C2864를 수정하는 방법을 보여 줍니다.

```cpp
// C2864b.cpp
// compile with: /c
class C  {
private:
   int a = 3;
   static int b; // = 3; C2864
   volatile static int c; // = 3; C2864
   volatile static const int d; // = 3; C2864
   static const long long e = 3;
   static const double f; // = 3.33; C2864
};

// Initialize static volatile, non-const, or non-integral
// data members when defined, not when declared:
int C::b = 3;
volatile int C::c = 3;
volatile const int C::d = 3;
const double C::f = 3.33;
```

---
description: '자세한 정보: 컴파일러 오류 C3849'
title: 컴파일러 오류 C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: 6dbe4656eea2691c1c77c1afa389be80ab76af18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255355"
---
# <a name="compiler-error-c3849"></a>컴파일러 오류 C3849

' type ' 형식의 식에 대 한 함수 스타일 호출은 모든 사용 가능한 연산자 오버 로드에 대해 const 및/또는 volatile 한정자가 손실 됩니다.

지정 된 const volatile 형식의 변수는 동일 하거나 더 큰 const volatile 자격으로 정의 된 멤버 함수만 호출할 수 있습니다.

이 오류를 해결 하려면 적절 한 멤버 함수를 제공 합니다. 변환으로 인해 한정자가 손실 되는 경우 const 또는 volatile 정규화 된 개체에 대 한 변환을 실행할 수 없습니다. 한정자를 얻을 수 있지만 변환 시 한정자를 손실할 수는 없습니다.

다음 샘플에서는 C3849를 생성 합니다.

```cpp
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```

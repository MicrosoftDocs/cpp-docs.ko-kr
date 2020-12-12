---
description: '자세한 정보: 컴파일러 오류 C2143'
title: 컴파일러 오류 C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 4218a14520016ef7b9180c2f5c8c7ddee55ffec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235517"
---
# <a name="compiler-error-c2143"></a>컴파일러 오류 C2143

구문 오류: ' token2 ' 앞에 ' token1 '가 없습니다.

컴파일러가 특정 토큰 (공백 이외의 언어 요소)을 예상 하 고 다른 토큰을 발견 했습니다.

[C + + 언어 참조](../../cpp/cpp-language-reference.md) 를 확인 하 여 코드의 구문이 잘못 된 위치를 확인 합니다. 컴파일러가 문제의 원인이 되는 줄을 발견 한 후에이 오류를 보고할 수 있으므로 오류 앞에 나오는 여러 줄의 코드를 확인 합니다.

C2143는 다양 한 상황에서 발생할 수 있습니다.

이는 다음 `::` `->` `.` 예제와 같이 이름 (, 및)을 한정할 수 있는 연산자 뒤에 키워드가와 야 하는 경우에 발생할 수 있습니다 **`template`** .

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

기본적으로 C++는 `Ty::PutFuncType`이 템플릿이 아니라고 가정하기 때문에 다음 `<`는 보다 작음 기호로 해석됩니다.  꺾쇠 괄호로 올바르게 구문 분석될 수 있도록 `PutFuncType`이 템플릿임을 컴파일러에 명시적으로 알려야 합니다. 이 오류를 해결 하려면 다음과 같이 **`template`** 종속 형식의 이름에 키워드를 사용 합니다.

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143는 **/clr** 을 사용 하 고 지시문에 **`using`** 구문 오류가 있는 경우에 발생할 수 있습니다.

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

또한 **/clr** 을 사용 하지 않고 CLR 구문을 사용 하 여 소스 코드 파일을 컴파일하려고 시도 하는 경우에도 발생할 수 있습니다.

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

문 뒤에 오는 공백이 아닌 첫 번째 문자는 **`if`** 왼쪽 괄호 여야 합니다. 컴파일러는 다른 항목을 변환할 수 없습니다.

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143은 오류가 검색된 줄 또는 윗줄 중 하나에서 닫는 중괄호, 괄호 또는 세미콜론이 누락된 경우 발생할 수 있습니다.

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

또는 클래스 선언에 잘못된 태그가 있는 경우:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

또는 레이블이 문에 첨부되지 않은 경우. 예를 들어, 복합 문의 끝에 레이블을 단독으로 저장 해야 하는 경우에는 null 문에 연결 합니다.

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

C + + 표준 라이브러리의 형식에 대해 정규화 되지 않은 호출이 수행 될 때 오류가 발생할 수 있습니다.

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

또는 누락 된 키워드가 있습니다 **`typename`** .

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

또는 명시적 인스턴스화를 정의하려고 한 경우:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

C 프로그램에서 변수는 함수 시작 부분에 선언 되어야 하며 함수에서 선언 되지 않은 명령을 실행 한 후에 선언할 수 없습니다.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```

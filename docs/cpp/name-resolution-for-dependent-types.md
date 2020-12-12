---
description: '자세히 알아보기: 종속 형식에 대 한 이름 확인'
title: 종속적인 형식에 대한 이름 확인
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: f50b067062f01d04ce26374ad969d572e1a7fe08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313790"
---
# <a name="name-resolution-for-dependent-types"></a>종속적인 형식에 대한 이름 확인

**`typename`** 템플릿 정의의 정규화 된 이름을 사용 하 여 지정 된 정규화 된 이름이 형식을 식별 함을 컴파일러에 알립니다. 자세한 내용은 [typename](../cpp/typename.md)을 참조 하세요.

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

종속 이름에 대 한 이름 조회는 템플릿 정의의 컨텍스트 모두에서 이름을 검사 합니다. 다음 예제에서이 컨텍스트는 `myFunction(char)` 및 템플릿 인스턴스화의 컨텍스트를 찾습니다. 다음 예제에서는 템플릿이 main에서 인스턴스화됩니다. 따라서가 `MyNamespace::myFunction` 인스턴스화 지점에서 표시 되 고 더 잘 일치 하는 것으로 선택 됩니다. `MyNamespace::myFunction`의 이름이 바뀐 경우 `myFunction(char)`이 대신 호출됩니다.

모든 이름은 종속 이름인 것처럼 확인됩니다. 그러나 충돌 발생 가능성이 있을 경우 철저하게 정규화된 이름을 사용하는 것이 좋습니다.

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>출력

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>템플릿 명확성

Visual Studio 2012는 "template" 키워드를 사용 하 여 명확성을 위해 c + + 98/03/11 표준 규칙을 적용 합니다. 다음 예제에서 Visual Studio 2010은 순응 하지 않는 줄과 순응 하는 줄을 모두 허용 합니다.  Visual Studio 2012은 맞는 줄만 허용 합니다.

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

기본적으로 C++에서는 `AY::Rebind`가 템플릿이 아니며 컴파일러에서 다음 " `<`"을 less-than으로 해석한다고 가정하기 때문에 명확성 규칙 준수가 필요합니다. C++에 `Rebind`가 템플릿이라는 것을 인지시켜 "`<`"을 꺾쇠로 올바르게 구문 분석할 수 있도록 해야 합니다.

## <a name="see-also"></a>참고 항목

[이름 확인](../cpp/templates-and-name-resolution.md)

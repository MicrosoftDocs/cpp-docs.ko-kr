---
title: 클래스, 구조체 및 공용 구조체에 대 한 중괄호 초기화
description: 모든 C++ 클래스, 구조체 또는 공용 구조체에 중괄호 초기화 사용
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: a2c9db4572b0dde94c42ec6768a0f3bed7766a96
ms.sourcegitcommit: 15677b0e4d2518847ce59b158990b25c4077e565
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75652626"
---
# <a name="brace-initialization"></a>중괄호 초기화

클래스, 특히 비교적 간단한 클래스에 대해 항상 생성자를 정의할 필요는 없습니다. 사용자는 다음 예제와 같이 균일 초기화를 사용하여 클래스 또는 구조체의 개체를 초기화할 수 있습니다.

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

클래스 또는 구조체에 생성자가 없는 경우 제공하는 멤버 클래스에서 선언되는 순서로 목록 요소를 참고합니다. 클래스에 생성자가 있는 경우 매개 변수를 순서대로 요소를 제공합니다. 형식에 암시적 또는 명시적으로 선언 된 기본 생성자가 있는 경우에는 기본 중괄호 초기화를 사용할 수 있습니다 (빈 중괄호 포함). 예를 들어 다음 클래스는 기본 및 기본이 아닌 중괄호 초기화를 모두 사용 하 여 초기화할 수 있습니다.

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

클래스에 기본 생성자가 아닌 생성자가 있는 경우에는 해당 매개 변수가 생성자에 표시 되는 순서가 며, 앞의 예제에서 `class_a`와 같이 멤버가 선언 되는 순서는 아닙니다. 그렇지 않고 형식에 선언 된 생성자가 없는 경우에는 멤버가 중괄호 이니셜라이저에 표시 되는 순서가 선언 된 순서와 동일 합니다. 이 경우 원하는 만큼 public 멤버를 초기화할 수 있지만 멤버를 건너뛸 수는 없습니다. 다음 예제에서는 선언 된 생성자가 없을 때 중괄호 초기화에 사용 되는 순서를 보여 줍니다.

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

기본 생성자를 명시적으로 선언 했지만 삭제 된 것으로 표시 한 경우에는 기본 중괄호 초기화를 사용할 수 없습니다.

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

일반적으로 초기화를 수행 하는 경우 (예: 함수 매개 변수 또는 반환 값) 또는 **new** 키워드를 사용 하 여 중괄호 초기화를 사용할 수 있습니다.

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

**/Std: c + + 17** 모드에서 빈 중괄호 초기화에 대 한 규칙은 약간 더 제한적입니다. [파생 된 생성자 및 확장 된 집계 초기화](constructors-cpp.md#extended_aggregate)를 참조 하세요.

## <a name="initializer_list-constructors"></a>initializer_list 생성자

[Initializer_list 클래스](../standard-library/initializer-list-class.md) 는 생성자와 다른 컨텍스트에서 사용할 수 있는 지정 된 형식의 개체 목록을 나타냅니다. 중괄호 초기화를 사용 하 여 initializer_list를 생성할 수 있습니다.

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  이 클래스를 사용 하려면 [\<initializer_list >](../standard-library/initializer-list.md) 헤더를 포함 해야 합니다.

`initializer_list` 복사할 수 있습니다. 이 경우 새 목록의 멤버는 원래 목록의 멤버에 대 한 참조입니다.

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

표준 라이브러리 컨테이너 클래스와 `string`, `wstring`및 `regex`에는 `initializer_list` 생성자가 있습니다. 다음 예제에서는 이러한 생성자를 사용 하 여 중괄호 초기화를 수행 하는 방법을 보여 줍니다.

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```


## <a name="see-also"></a>참조

[클래스 및 구조체](../cpp/classes-and-structs-cpp.md)<br/>
[생성자](../cpp/constructors-cpp.md)

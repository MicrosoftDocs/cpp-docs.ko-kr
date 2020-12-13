---
description: '자세한 정보: 헤더 파일 (c + +)'
title: 헤더 파일 (c + +)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 22ef05c723368f0456ee880729031610b34876d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332529"
---
# <a name="header-files-c"></a>헤더 파일 (c + +)

변수, 함수, 클래스 등의 프로그램 요소 이름은 먼저 선언 되어야 사용할 수 있습니다. 예를 들어 `x = 42` ' x '를 먼저 선언 하지 않고만 쓸 수 있습니다.

```cpp
int x; // declaration
x = 42; // use x
```

선언은 요소가 **`int`** ,, **`double`** , **함수** 인지 또는 다른 지를 컴파일러에 알립니다 **`class`** .  또한 각 이름은 사용 되는 모든 .cpp 파일에서 직접 또는 간접적으로 선언 되어야 합니다. 프로그램을 컴파일하면 각 .cpp 파일이 컴파일 단위에 독립적으로 컴파일됩니다. 컴파일러는 다른 컴파일 단위에 선언 된 이름을 알지 못합니다. 즉, 클래스 또는 함수 또는 전역 변수를 정의 하는 경우이를 사용 하는 각 추가 .cpp 파일에서 해당 항목의 선언을 제공 해야 합니다. 모든 파일에서 해당 항목의 선언이 정확히 동일 해야 합니다. 약간의 불일치는 링커에서 모든 컴파일 단위를 단일 프로그램으로 병합 하려고 할 때 발생 하는 오류 또는 의도 하지 않은 동작을 발생 시킵니다.

오류 가능성을 최소화 하기 위해 c + +에서는 *헤더 파일* 을 사용 하 여 선언을 포함 하는 규칙을 채택 했습니다. 헤더 파일에서 선언을 만든 다음 해당 선언이 필요한 모든 .cpp 파일 또는 다른 헤더 파일에 #include 지시어를 사용 합니다. #Include 지시어는 컴파일 전에 헤더 파일의 복사본을 .cpp 파일에 직접 삽입 합니다.

> [!NOTE]
> Visual Studio 2019에서 c + + 20 *모듈* 기능은 헤더 파일에 대 한 향상 된 기능 및 최종 대체 기능으로 도입 되었습니다. 자세한 내용은 [c + +의 모듈 개요](modules-cpp.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스를 선언한 다음 다른 소스 파일에서 사용 하는 일반적인 방법을 보여 줍니다. 헤더 파일로 시작 `my_class.h` 합니다. 클래스 정의를 포함 하지만 정의가 불완전 함을 확인 합니다. 멤버 함수가 `do_something` 정의 되지 않았습니다.

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

다음으로 구현 파일 (일반적으로 .cpp 또는 유사한 확장명 사용)을 만듭니다. My_class 파일을 호출 하 고 멤버 선언에 대 한 정의를 제공 합니다. `#include`"My_class .h" 파일에 대 한 지시문을 추가 하 여 .cpp 파일의이 지점에 my_class 선언을 삽입 하 고 `<iostream>` 에 대 한 선언에를 포함 `std::cout` 합니다. 따옴표는 소스 파일과 동일한 디렉터리에 있는 헤더 파일에 사용 되며, 표준 라이브러리 헤더에는 꺾쇠 괄호가 사용 됩니다. 또한 많은 표준 라이브러리 헤더에는 .h 또는 다른 파일 확장명이 없습니다.

구현 파일에서 선택적으로 문을 사용 하 여 " **`using`** N::" 또는 "std::"로 "my_class" 또는 "cout"의 모든 언급을 한정할 필요가 없도록 할 수 있습니다.  **`using`** 헤더 파일에 문을 넣지 마세요.

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

이제 `my_class` 다른 .cpp 파일에서을 사용할 수 있습니다. 컴파일러가 선언에서 가져오기 위해 헤더 파일을 #include 합니다. 모든 컴파일러는 my_class가 이라는 public 멤버 함수가 있는 클래스 라는 것을 알고 있어야 합니다 `do_something()` .

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

컴파일러가 각 .cpp 파일을 .obj 파일에 컴파일한 후에는 .obj 파일을 링커에 전달 합니다. 링커가 개체 파일을 병합 하는 경우 my_class에 대해 정확히 하나의 정의를 찾습니다. my_class에 대해 생성 된 .obj 파일에 있으며 빌드가 성공 합니다.

## <a name="include-guards"></a>가드 포함

일반적으로 헤더 파일에는  `#pragma once` 단일 .cpp 파일에 여러 번 삽입 되지 않도록 하는 include 가드 또는 지시문이 있습니다.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>헤더 파일에 삽입할 내용

헤더 파일은 잠재적으로 여러 파일에 포함 될 수 있으므로 동일한 이름의 여러 정의를 생성할 수 있는 정의를 포함할 수 없습니다. 다음은 허용 되지 않거나 매우 나쁜 방법으로 간주 됩니다.

- 네임 스페이스 또는 전역 범위의 기본 제공 형식 정의
- 비 인라인 함수 정의
- 비 const 변수 정의
- 집계 정의
- 명명되지 않은 네임스페이스
- using 지시문

지시문을 사용 하면 **`using`** 오류가 발생 하지 않을 수 있지만, 해당 헤더를 직접 또는 간접적으로 포함 하는 모든 .cpp 파일에서 네임 스페이스를 범위로 가져오기 때문에 문제가 발생할 수 있습니다.

## <a name="sample-header-file"></a>샘플 헤더 파일

다음 예제에서는 헤더 파일에 허용 되는 다양 한 종류의 선언 및 정의를 보여 줍니다.

```cpp
// sample.h
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```

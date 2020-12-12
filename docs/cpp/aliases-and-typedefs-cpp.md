---
description: '자세히 알아보기: 별칭 및 형식 정의 (c + +)'
title: 별칭 및 typedef(C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 7b5924fd30fe1d22e6a82fb82e2d252409d782ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239859"
---
# <a name="aliases-and-typedefs-c"></a>별칭 및 typedef(C++)

*별칭 선언을* 사용 하 여 이전에 선언 된 형식에 대 한 동의어로 사용할 이름을 선언할 수 있습니다. 이 메커니즘을 비공식적 *형식 별칭* 이 라고도 합니다. 이 메커니즘을 사용 하 여 사용자 지정 할당자에 특히 유용할 수 있는 *별칭 템플릿을* 만들 수도 있습니다.

## <a name="syntax"></a>구문

```
using identifier = type;
```

## <a name="remarks"></a>설명

*identifier*<br/>
별칭 이름입니다.

*type*<br/>
별칭을 만들 형식 식별자입니다.

별칭은 새 형식을 사용하지 않으며 기존 형식 이름의 의미를 변경할 수 없습니다.

별칭의 가장 간단한 형태는 **`typedef`** c + + 03의 메커니즘과 동일 합니다.

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

두 가지 모두 "카운터" 형식의 변수를 만들 수 있습니다. `std::ios_base::fmtflags`에 대해서는 이와 같은 형식 별칭이 더 유용합니다.

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

별칭은 함수 포인터에도 작동 하지만 해당 typedef 보다 훨씬 더 읽기 쉽습니다.

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

메커니즘의 제한 사항은 **`typedef`** 템플릿에서 작동 하지 않는다는 것입니다. 그러나 C++ 11의 형식 별칭 구문을 사용하면 별칭 템플릿을 만들 수 있습니다.

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>예제

다음 예제에서는 사용자 지정 할당자(이 경우 정수 벡터 형식)와 별칭 템플릿을 사용하는 방법을 데모로 보여 줍니다. 모든 형식을로 대체 하 여 **`int`** 기본 함수 코드에서 복잡 한 매개 변수 목록을 숨기는 편리한 별칭을 만들 수 있습니다. 코드 전반에 사용자 지정 할당자를 사용하여 가독성을 향상시키고 오타로 인한 버그의 위험을 줄일 수 있습니다.

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedefs

선언에는 **`typedef`** 해당 범위 내에서 선언의 *형식 선언* 부분에서 제공 하는 형식에 대 한 이름이 도입 됩니다.

typedef 선언을 사용하여 언어에서 이미 정의된 형식이나 사용자가 선언한 형식에 대한 보다 짧거나 의미 있는 이름을 생성할 수 있습니다. typedef 이름을 사용하면 변경될 수 있는 구현 정보를 캡슐화할 수 있습니다.

**`class`**,, **`struct`** **`union`** 및 선언과 달리 **`enum`** **`typedef`** 선언은 새 형식을 도입 하지 않으며 기존 형식에 대 한 새 이름을 도입 합니다.

를 사용 하 여 선언 **`typedef`** 된 이름은 다른 식별자 (문 레이블 제외)와 동일한 네임 스페이스를 차지 합니다. 따라서 클래스 형식으로 선언된 경우를 제외하고 이전에 선언된 이름과 동일한 식별자를 사용할 수 없습니다. 다음 예제를 참조하세요.

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

다른 식별자와 관련 된 이름 숨기기 규칙은를 사용 하 여 선언 된 이름의 표시 여부도 제어 합니다 **`typedef`** . 따라서 다음 예제는 C++에서 사용할 수 있습니다.

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

typedef와 동일한 이름의 로컬 범위 식별자를 선언하거나 같은 범위 또는 내부 범위에서 구조체 또는 공용 구조체의 멤버를 선언할 때 반드시 형식 지정자를 지정해야 합니다. 예를 들어:

```cpp
typedef char FlagType;
const FlagType x;
```

식별자, 구조체 멤버 또는 공용 구조체 멤버에 `FlagType` 이름을 다시 사용하려면 형식을 제공해야 합니다.

```cpp
const int FlagType;  // Type specifier required
```

다음과 같이 표현하면 충분하지 않습니다.

```cpp
const FlagType;      // Incomplete specification
```

`FlagType`이 다시 선언되는 식별자가 아니라 형식의 일부로 간주되기 때문입니다. 이 선언은 다음과 같이 잘못된 선언으로 간주됩니다.

```cpp
int;  // Illegal declaration
```

포인터, 함수 및 배열 형식을 비롯한 모든 형식을 typedef를 사용하여 선언할 수 있습니다. 정의의 표시 유형이 선언의 표시 유형과 동일한 경우 구조체 또는 공용 구조체 형식을 정의하기 전에 구조체 또는 공용 구조체 형식에 대한 포인터의 typedef 이름을 선언할 수 있습니다.

### <a name="examples"></a>예제

**`typedef`** 선언을 사용 하는 한 가지 방법은 선언을 더 균일 하 고 압축 하는 것입니다. 예를 들어:

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

를 사용 하 여 **`typedef`** 동일한 선언에서 기본 및 파생 형식을 지정 하려면 선언 자를 쉼표로 구분 하면 됩니다. 예를 들어:

```cpp
typedef char CHAR, *PSTR;
```

다음 예제에서는 값을 반환하지 않고 두 개의 int 인수를 사용하는 함수에 대한 `DRAWF` 형식을 제공합니다.

```cpp
typedef void DRAWF( int, int );
```

위의 문 뒤에 **`typedef`** 는 선언이 있습니다.

```cpp
DRAWF box;
```

다음 선언과 동일합니다.

```cpp
void box( int, int );
```

**`typedef`** 는와 결합 되어 **`struct`** 사용자 정의 형식을 선언 하 고 이름을 지정 하는 경우가 많습니다.

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>typedef 다시 선언

선언을 사용 하 여 동일한 **`typedef`** 형식을 참조 하는 동일한 이름을 다시 선언할 수 있습니다. 예를 들어:

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

프로그램 프로그램 *입니다. CPP* 에는 두 헤더 파일이 포함 되어 있으며 둘 다 **`typedef`** 이름에 대 한 선언을 포함 `CHAR` 합니다. 두 선언이 동일한 형식을 참조하는 한 이러한 재선언은 허용됩니다.

는 **`typedef`** 이전에 다른 형식으로 선언 된 이름을 다시 정의할 수 없습니다. 따라서 FILE2 인 경우 *입니다. H* 포함

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

컴파일러는 `CHAR`이라는 이름이 다른 형식을 참조하도록 다시 선언하려는 시도 때문에 오류를 발생시킵니다. 이는 다음과 같은 구문으로 확장됩니다.

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>c + + 및 C + +의 typedef

**`typedef`** 선언에서 명명 되지 않은 구조체를 선언 하는 ANSI C 연습 때문에 클래스 형식에 지정자를 사용 하는 것은 주로 지원 됩니다 **`typedef`** . 예를 들어 많은 C 프로그래머는 다음을 사용합니다.

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

이러한 선언의 장점은 다음과 같은 선언이 가능하다는 것입니다.

```cpp
POINT ptOrigin;
```

위의 선언을 아래의 선언 대신 사용할 수 있습니다.

```cpp
struct point_t ptOrigin;
```

C + +에서 **`typedef`** 이름 및 실수 형식 (,, 및 키워드를 사용 하 여 선언 됨)의 차이는 **`class`** **`struct`** **`union`** **`enum`** 더 고유 합니다. 문에서 이름이 없는 구조체를 선언 하는 C 사례는 **`typedef`** 여전히 작동 하지만 c에서는 표기법 밑수 이점을 제공 하지 않습니다.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

앞의 예제에서는 명명 `POINT` 되지 않은 클래스 구문을 사용 하 여 라는 클래스를 선언 합니다 **`typedef`** . `POINT`는 클래스 이름으로 간주되지만 다음과 같은 제한 사항이 이런 방식으로 생성된 이름에 적용됩니다.

- 이름 (동의어)은 **`class`** , 또는 접두사 뒤에 올 수 없습니다 **`struct`** **`union`** .

- 해당 이름은 클래스 선언 내에서 생성자 또는 소멸자 이름으로 사용할 수 없습니다.

요약하면 이 구문은 상속, 생성 또는 소멸을 위한 메커니즘을 제공하지 않습니다.

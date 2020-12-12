---
description: '자세한 정보: 컴파일러 오류 C2065'
title: 컴파일러 오류 C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: a686276aa093e1f2011212d5999d43c76062487f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328558"
---
# <a name="compiler-error-c2065"></a>컴파일러 오류 C2065

> '*identifier*': 선언 되지 않은 식별자입니다.

컴파일러가 식별자에 대 한 선언을 찾을 수 없습니다. 이 오류의 원인은 다양합니다. C2065의 가장 일반적인 원인은 식별자가 선언 되지 않았거나, 식별자의 철자가 틀렸거나, 식별자가 선언 된 헤더가 파일에 포함 되어 있지 않거나, 식별자에 범위 한정자 (예: 대신)가 없는 것입니다 `cout` `std::cout` . C + +의 선언에 대 한 자세한 내용은 [선언 및 정의 (c + +)](../../cpp/declarations-and-definitions-cpp.md)를 참조 하세요.

다음은 몇 가지 일반적인 문제 및 해결 방법입니다.

## <a name="the-identifier-is-undeclared"></a>식별자가 선언 되지 않았습니다.

식별자가 변수 또는 함수 이름인 경우이를 선언 해야 사용할 수 있습니다. 함수를 사용 하려면 함수 선언에도 해당 매개 변수의 형식이 포함 되어야 합니다. 를 사용 하 여 변수를 선언 하는 경우 **`auto`** 컴파일러는 해당 이니셜라이저에서 형식을 유추할 수 있어야 합니다.

식별자가 클래스 또는 구조체의 멤버 이거나 네임 스페이스에 선언 된 경우 클래스 또는 구조체 이름 또는 네임 스페이스 이름 (구조체, 클래스 또는 네임 스페이스 범위 외부에서 사용 되는 경우)으로 정규화 되어야 합니다. 또는와 같은 지시문을 통해 네임 스페이스를 범위로 가져와야 **`using`** `using namespace std;` 하거나,와 같은 선언으로 멤버 이름을 가져와야 합니다 **`using`** `using std::string;` . 그렇지 않으면 정규화 되지 않은 이름이 현재 범위에서 선언 되지 않은 식별자로 간주 됩니다.

식별자가 또는와 같은 사용자 정의 형식에 대 한 태그 이면 **`class`** **`struct`** 태그의 형식을 선언 해야만 사용할 수 있습니다. 예를 들어 `struct SomeStruct { /*...*/ };` 코드에서 변수를 선언 하려면 선언이 있어야 합니다 `SomeStruct myStruct;` .

식별자가 형식 별칭이 면 선언을 사용 하 여 형식을 선언 **`using`** 하거나 사용 하기 전에 형식을 선언 해야 합니다 **`typedef`** . 예를 들어를 `using my_flags = std::ios_base::fmtflags;` `my_flags` 에 대 한 형식 별칭으로 사용 하려면 먼저를 선언 해야 합니다 `std::ios_base::fmtflags` .

## <a name="example-misspelled-identifier"></a>예: 잘못 된 식별자

이 오류는 일반적으로 식별자 이름에 철자가 잘못 되었거나 식별자가 잘못 된 대/소문자를 사용 하는 경우에 발생 합니다. 선언에서 이름은 사용 하는 이름과 정확 하 게 일치 해야 합니다.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>예: 범위가 없는 식별자 사용

식별자의 범위가 올바르게 지정 되지 않은 경우이 오류가 발생할 수 있습니다. 를 사용할 때 C2065 `cout` 가 표시 되 면이는 원인입니다. C + + 표준 라이브러리 함수 및 연산자가 네임 스페이스로 정규화 되지 않았거나 `std` 지시문을 사용 하 여 네임 스페이스를 현재 범위로 전환 하지 않은 경우 **`using`** 컴파일러는 해당 함수를 찾을 수 없습니다. 이 문제를 해결 하려면 식별자 이름을 정규화 하거나 지시문을 사용 하 여 네임 스페이스를 지정 해야 합니다 **`using`** .

이 예에서는 `cout` 및 `endl` 가 네임 스페이스에 정의 되어 있기 때문에 컴파일되지 않습니다 `std` .

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

, 또는 형식 내에서 선언 된 식별자 **`class`** **`struct`** **`enum class`** 는 해당 범위 외부에서 사용할 때 바깥쪽 범위의 이름으로도 정규화 되어야 합니다.

## <a name="example-precompiled-header-isnt-first"></a>예: 미리 컴파일된 헤더는 먼저 수행 되지 않습니다.

#Include, #define, #pragma 등의 전처리기 지시문을 미리 컴파일된 헤더 파일 #include 앞에 배치 하는 경우이 오류가 발생할 수 있습니다. 소스 파일이 미리 컴파일된 헤더 파일을 사용 하는 경우 (즉, **/yu** 컴파일러 옵션을 사용 하 여 컴파일된 경우) 미리 컴파일된 헤더 파일 이전의 모든 전처리기 지시문이 무시 됩니다.

이 예제는 `cout` `endl` \<iostream> 미리 컴파일된 헤더 파일 앞에 포함 되기 때문에 무시 되는 헤더에가 정의 되어 있기 때문에 컴파일되지 않습니다. 이 예를 빌드하려면 세 개의 파일을 모두 만든 다음 stdafx.h를 컴파일한 다음 C2065_pch을 컴파일합니다.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

이 문제를 해결 하려면 #include를 \<iostream> 미리 컴파일된 헤더 파일에 추가 하거나, 미리 컴파일된 헤더 파일이 소스 파일에 포함 된 후에이 파일을 이동 합니다.

## <a name="example-missing-header-file"></a>예: 헤더 파일이 누락 됨

식별자를 선언 하는 헤더 파일을 포함 하지 않았습니다. 식별자에 대 한 선언이 포함 된 파일이이를 사용 하는 모든 소스 파일에 포함 되어 있는지 확인 합니다.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

또 다른 가능한 원인은 헤더를 포함 하지 않고 이니셜라이저 목록을 사용 하는 경우입니다 \<initializer_list> .

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

, 또는을 정의 하는 경우 Windows 데스크톱 앱 소스 파일에이 오류가 표시 될 수 있습니다 `VC_EXTRALEAN` `WIN32_LEAN_AND_MEAN` `WIN32_EXTRA_LEAN` . 이러한 전처리기 매크로는 windows .h 및 afxv w32.slammer에서 일부 헤더 파일 \_ 을 제외 하 여 컴파일을 가속화 합니다. Windows. h 및 afxv_w32에서 제외 된 항목에 대 한 최신 설명을 확인 하세요.

## <a name="example-missing-closing-quote"></a>예: 닫는 따옴표가 없습니다.

이 오류는 문자열 상수 뒤에 닫는 따옴표가 없는 경우에 발생할 수 있습니다. 이 방법은 컴파일러를 혼동 하는 쉬운 방법입니다. 누락 된 닫는 따옴표는 보고 된 오류 위치 앞에 여러 줄이 있을 수 있습니다.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>예: for 루프 범위 외부에서 반복기 사용

이 오류는 루프에서 반복기 변수를 선언한 **`for`** 다음 루프 범위 밖의 반복기 변수를 사용 하려고 할 때 발생할 수 있습니다 **`for`** . 컴파일러는 기본적으로 [/zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 컴파일러 옵션을 사용 하도록 설정 합니다. 자세한 내용은 [디버그 반복기 지원](../../standard-library/debug-iterator-support.md) 을 참조 하세요.

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>예: 전처리기 제거 선언

현재 구성에 대해 컴파일되지 않은 조건부로 컴파일된 코드에 있는 함수 또는 변수를 참조 하는 경우이 오류가 발생할 수 있습니다. 이는 빌드 환경에서 현재 지원 되지 않는 헤더 파일의 함수를 호출 하는 경우에도 발생할 수 있습니다. 특정 전처리기 매크로가 정의 된 경우에만 특정 변수나 함수를 사용할 수 있는 경우 해당 함수를 호출 하는 코드를 동일한 전처리기 매크로가 정의 된 경우에만 컴파일할 수 있는지 확인 합니다. 현재 빌드 구성에 대해 필수 전처리기 매크로가 정의 되지 않은 경우에는 함수에 대 한 선언이 회색으로 표시 되기 때문에 IDE에서이 문제를 쉽게 찾을 수 있습니다.

다음은 디버그로 빌드할 때 작동 하지만 일반 정품이 아닌 코드의 예제입니다.

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>예: c + +/CLI 형식 추론 오류

이 오류는 제네릭 함수를 호출할 때 사용 되는 매개 변수에서 의도 한 형식 인수를 추론할 수 없는 경우 발생할 수 있습니다. 자세한 내용은 [제네릭 함수 (c + +/cli)](../../extensions/generic-functions-cpp-cli.md)를 참조 하세요.

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>예: c + +/CLI 특성 매개 변수

이 오류는 Visual Studio 2005에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수도 있습니다. Visual C++ 특성에 대 한 매개 변수 검사입니다.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

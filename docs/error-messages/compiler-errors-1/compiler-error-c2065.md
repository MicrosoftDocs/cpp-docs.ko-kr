---
title: 컴파일러 오류 C2065 | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e67fcac9593dc4ad11dbff0cc479ac24d624110
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172792"
---
# <a name="compiler-error-c2065"></a>컴파일러 오류 C2065

> '*식별자*': 선언 되지 않은 식별자

컴파일러는 식별자에 대 한 선언을 찾을 수 없습니다. 이 오류에 대 한 다양 한 원인 있습니다. C2065의 가장 일반적인 원인은는 식별자를 선언 하지 않은, 식별자는 철자가 잘못 입력 된는 식별자가 선언 된 헤더 파일에 포함 되지 않습니다 또는 식별자 예를 들어 범위 한정자가 없습니다 `cout` 대신 `std::cout`. C + +의 선언에 대 한 자세한 내용은 참조 하십시오. [선언 및 정의 (c + +)](../../cpp/declarations-and-definitions-cpp.md)합니다.

다음 몇 가지 일반적인 문제와 해결 방법 자세히은입니다.

## <a name="the-identifier-is-undeclared"></a>식별자 선언 되지 않은

식별자는 변수 또는 함수 이름을 이면 사용 하려면 먼저 선언 해야 합니다. 함수 선언 함수를 사용 하려면 먼저 해당 매개 변수 형식을 포함 해야 합니다. 변수를 사용 하 여 선언 되 면 `auto`, 컴파일러는 해당 이니셜라이저에서 형식을 유추할 수 있어야 합니다.

식별자가 클래스 또는 구조체의 멤버인 네임 스페이스 선언, 구조체, 클래스 또는 네임 스페이스 범위 외부에서 사용 하는 경우 클래스 또는 구조체 이름 또는 네임 스페이스 이름으로 한정 되어야 합니다. 또는 네임 스페이스 시켜야 할 범위로 `using` 지시문과 같은 `using namespace std;`, 멤버 이름 범위로 가져와야 또는 `using` 선언 같은 `using std::string;`합니다. 그렇지 않으면 정규화 되지 않은 이름은 현재 범위에서 선언 되지 않은 식별자 간주 됩니다.

식별자가 사용자 정의 형식에 대 한 태그 예를 들어 한 `class` 또는 `struct`, 태그의 형식을 사용 하려면 먼저 선언 해야 합니다. 예를 들어 선언 `struct SomeStruct { /*...*/ };` 변수를 선언할 수 전에 있어야 `SomeStruct myStruct;` 코드에서.

식별자가 형식 별칭을 사용 하 여 형식을 선언 해야는 `using` 선언 또는 `typedef` 사용할 수 있습니다. 예를 들어 선언 해야 `using my_flags = std::ios_base::fmtflags;` 사용 하려면 먼저 `my_flags` 에 대 한 형식 별칭으로 `std::ios_base::fmtflags`합니다.

## <a name="example-misspelled-identifier"></a>예: 철자가 잘못 된 식별자

이 오류는 일반적으로 식별자 이름의 철자가, 식별자 잘못 된 사용 대 / 소문자 또는 경우에 발생 합니다. 선언에서 이름에 사용 하는 이름이 일치 해야 합니다.

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

## <a name="example-use-an-unscoped-identifier"></a>예: 범위가 지정 되지 않은 식별자를 사용 합니다.

식별자를 제대로 범위로 지정 되지 않은 경우이 오류가 발생할 수 있습니다. C2065 사용할 때 표시 되 면 `cout`, 이것이 원인입니다. C + + 표준 라이브러리 함수 및 연산자 정규화 되지 않은 네임 스페이스로 또는 하지 가져온 경우는 `std` 네임 스페이스를 사용 하 여 현재 범위에는 `using` 지시문, 컴파일러 찾을 수 없습니다 해당 합니다. 이 문제를 해결 하려면 완전히 식별자 이름을 한정 하거나 포함 된 네임 스페이스를 지정 된 `using` 지시문입니다.

이 예제는 있기 때문에 컴파일하지 실패 `cout` 및 `endl` 에 정의 된는 `std` 네임 스페이스:

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

내에 선언 된 식별자 `class`, `struct`, 또는 `enum class` 해당 범위 외부에서 사용 하는 경우 형식은 바깥쪽 범위의 이름으로 한정도 합니다.

## <a name="example-precompiled-header-isnt-first"></a>예: 미리 컴파일된 헤더가 아닙니다 첫 번째

이 오류와 같은 모든 전처리기 지시문을 설정 하는 경우 발생할 수 있습니다 #include #define, 또는 #pragma, 하기 전에 # 미리 컴파일된 헤더 파일 include 합니다. 소스 파일에 미리 컴파일된 헤더 파일을 사용 하는 경우 (즉, 사용 하 여 컴파일할 경우는 **/Yu** 컴파일러 옵션) 전에 미리 컴파일된 헤더 파일에 있는 모든 전처리기 지시문은 무시 됩니다.

이 예제는 있기 때문에 컴파일하지 실패 `cout` 및 `endl` 에 정의 된는 \<iostream > 헤더로, 미리 컴파일된 헤더 파일을 전에 포함 되어 있으므로 무시 됩니다. 이 예제를 빌드하려면 모두 세 개의 파일을 만들을 차례로 stdafx.cpp, 컴파일 C2065_pch.cpp 컴파일하십시오.

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
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

이 문제를 해결 하려면 추가 #include \<iostream >는 미리 컴파일된 헤더 파일에 소스 파일에 포함 되어 미리 컴파일된 헤더 파일 후 이동 합니다.

## <a name="example-missing-header-file"></a>예: 헤더 파일이 없습니다.

식별자를 선언 하는 헤더 파일을 포함 되지 않습니다. 식별자에 대 한 선언이 포함 된 파일이 사용 하는 모든 소스 파일에 포함 되어 있는지 확인 합니다.

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

이니셜라이저 목록을 사용 하 여 포함 하지 않고 경우 또 다른 원인으로는 \<initializer_list > 헤더입니다.

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

정의 하는 경우 Windows 데스크톱 응용 프로그램 소스 파일에서이 오류가 표시 될 수 있습니다 `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, 또는 `WIN32_EXTRA_LEAN`합니다. 이러한 전처리기 매크로 windows.h 및 afxv에서 일부 헤더 파일을 제외\_w32.h 속도를 컴파일합니다. Windows.h 및 afxv_w32.h에 대 한 최신 설명 제외 되는를 찾습니다.

## <a name="example-missing-closing-quote"></a>예: 닫는 따옴표가 없습니다.

이 오류는 문자열 상수 뒤 닫는 따옴표가 누락 된 경우에 발생할 수 있습니다. 이것이 쉽게 컴파일러 혼동을 줄 수입니다. Note 누락 닫는 따옴표 보고 된 오류 위치 앞에 여러 줄을 수 있습니다. 

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>예: for 루프 범위 외부의 반복기를 사용 합니다.

반복기 변수를 선언 하는 경우이 오류가 발생할 수 있습니다는 `for` 루프 및 다음의 범위를 벗어나는 반복기 변수를 사용 하려고는 `for` 루프입니다. 사용 하면 컴파일러는 [/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 기본적으로 컴파일러 옵션입니다. 참조 [디버그 반복기 지원](../../standard-library/debug-iterator-support.md) 자세한 정보에 대 한 합니다.

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

이 오류는 현재 구성에 대 한 컴파일되지 않은 조건부로 컴파일된 코드에 된 변수 또는 함수를 참조 하는 경우에 발생할 수 있습니다. 빌드 환경에서 현재 지원 되지 않는 헤더 파일에는 함수를 호출 하는 경우 발생할 수도 있습니다. 특정 변수 또는 함수 인만 사용할 수 있는 특정 전처리기 매크로 정의 된 경우 동일한 전처리기 매크로 정의 된 경우에 이러한 함수를 호출 하는 코드를 컴파일할 수 있는지 확인 합니다. 이 문제는 필요한 전처리기 매크로 현재 빌드 구성에 대해 정의 되어 있지 않은 경우 함수에 대 한 선언을 회색 때문에를 쉽게 IDE에 파악할 수 있습니다.

다음은 디버그를 빌드 하지만 하지 소매 작동 하는 코드의 예입니다.

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

## <a name="example-ccli-type-deduction-failure"></a>예: C + + /cli CLI 형식 추론이 실패

사용 된 매개 변수에서 원하는 형식 인수를 추론할 수 없는 경우 일반 함수를 호출할 때이 오류가 발생할 수 있습니다. 자세한 내용은 참조 [제네릭 함수 (C + + /cli CLI)](../../windows/generic-functions-cpp-cli.md)합니다.

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

## <a name="example-ccli-attribute-parameters"></a>예: C + + /cli CLI 특성 매개 변수

이 오류는 Visual C++ 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성될 수도 있습니다. 매개 변수에 Visual C++ 특성이 있는지 확인합니다.

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

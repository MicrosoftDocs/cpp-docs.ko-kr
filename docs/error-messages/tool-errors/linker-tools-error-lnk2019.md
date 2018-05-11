---
title: 링커 도구 오류 LNK2019 | Microsoft Docs
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4323e5f8357da046db7a9403d7c575dfdde566b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2019"></a>링커 도구 오류 LNK2019

확인 되지 않은 외부 기호 '*기호*'함수에서 참조 된'*함수*'

컴파일된 코드를 *함수* 참조 또는 호출을 사용 하면 *기호*이지만, 그에 라이브러리 또는 개체 파일을 링커에 지정 기호가 정의 되지 않습니다.

이 오류 메시지 다음에 심각한 오류 [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)합니다. LNK1120 오류를 해결 하려면 모든 LNK2001 및 LNK2019 오류를 수정 해야 합니다.

## <a name="possible-causes"></a>가능한 원인

이 오류가 발생 하는 방법은 여러 가지가 있지만 링커 없습니다 된 변수 또는 함수에 대 한 참조를 포함 하는 모든 *해결*, 또는 찾기에 대 한 정의입니다. 기호가 없을 때 확인할 수 있습니다 *선언*, 하지는 않지만 *정의*이므로 다른 소스 파일 또는 라이브러리에는 정의가 있을 수 있습니다. 기호 참조 되었지만 정의 되지 않았습니다. 된 경우 링커는 확인 되지 않은 외부 기호 오류가 생성 됩니다.

LNK2019를 일으키는 일반적인 문제는 다음과 같습니다.

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>개체 파일 또는 기호 정의 포함 된 라이브러리에 연결 되어 있지 않습니다.

Visual Studio에서 정의 포함 하는 소스 파일 프로젝트의 일부분으로 연결 된 빌드를 확인 합니다. 명령줄에서 정의 포함 하는 소스 파일을 컴파일한 있으며 결과 개체 파일에 연결 하는 파일의 목록에 포함 되어 있는지 확인 합니다.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>기호의 선언 하지 철자가 기호 정의와 동일

올바른 철자 및 대/소문자가 선언과 정의 모두 사용 되 고 아무 곳에 나 기호가 사용 되었거나 호출을 확인 합니다.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>함수를 사용 하지만 형식 또는 매개 변수 개수가 함수 정의와 일치 하지 않습니다.

함수 선언은 정의와 일치해야 합니다. 함수 호출이 선언과 일치하며 선언이 정의와 일치하는지 확인하세요. 또한 템플릿 함수를 호출하는 코드에는 정의와 같은 템플릿 매개 변수가 포함되는 일치하는 템플릿 함수 선언이 있어야 합니다. 템플릿 선언 불일치의 예를 들어 LNK2019e.cpp "예" 섹션에서 샘플을 참조 합니다.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>함수 또는 변수가 선언 되었지만 정의 되지 않았습니다.

이 문제는 일반적으로 선언이 헤더 파일에 존재 하지만 일치 하는 정의가 구현 되지 의미 합니다. 멤버 함수 또는 정적 데이터 멤버의 경우 구현에 클래스 범위 선택기가 포함되어야 합니다. 예제를 보려면 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)를 참조하십시오.

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>호출 규칙 함수 선언과 함수 정의 간에 차이가 있는

호출 규칙([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)또는 [__vectorcall](../../cpp/vectorcall.md))은 트데코레이된 이름의 일부로써 인코딩됩니다. 호출 규칙이 동일한지 확인하세요.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>기호가 C 파일에 정의 되어 있지만 c + + 파일에서 extern "C"를 사용 하지 않고 선언

C로 컴파일된 파일에 정의 된 기호는 사용 하지 않는 한 c + + 파일에 선언 된 기호와 다른 트 데코 레이 된 이름과 이름을 [extern "C"](../../cpp/using-extern-to-specify-linkage.md) 한정자입니다. 선언이 각 기호의 컴파일 링크와 일치하는지 확인하세요. 마찬가지로, C 프로그램에서 사용할 기호를 C++ 파일에서 정의하는 경우 정의에 `extern "C"` 을 사용하세요.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>기호가 static으로 정의 되 고 후 나중에 파일 외부 참조

C와 달리 C++에서는 [전역 상수](../../error-messages/tool-errors/global-constants-in-cpp.md) 에 `static` 링크가 있습니다. 이 제한을 해결하기 위해 헤더 파일에 `const` 초기화를 포함하고 .cpp 파일에 해당 헤더를 포함하거나, 변수를 비상수로 만들고 상수 참조를 사용하여 액세스할 수 있습니다.

### <a name="a-static-member-of-a-class-is-not-defined"></a>클래스의 정적 멤버가 정의 되지 않았습니다.

정적 클래스 멤버에는 고유한 정의가 있어야 합니다. 그렇지 않으면 단일 정의 규칙을 위반하게 됩니다. 인라인으로 정의될 수 없는 정적 클래스 멤버는 정규화된 이름을 사용하여 한 소스 파일에 정의되어야 합니다. 전혀 정의되지 않은 경우 링커는 LNK2019를 생성합니다.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>빌드 종속성은 솔루션의 프로젝트 종속성 으로만 정의

이전 버전의 Visual Studio에서는이 수준의 종속성으로 충분 했습니다. 그러나 Visual Studio 2010 이상에서는 Visual Studio을 사용 하려면 한 [프로젝트 간 참조](/visualstudio/ide/managing-references-in-a-project)합니다. 프로젝트에 프로젝트 간 참조가 없는 경우 이 링커 오류가 발생할 수 있습니다. 프로젝트 간 참조를 추가하여 오류를 해결하세요.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Windows 응용 프로그램에 대 한 설정을 사용 하 여 콘솔 응용 프로그램 빌드

오류 메시지는 비슷한 경우 **WinMain 함수에서 참조 하는 확인 되지 않은 외부 기호** *function_name*, 링크를 사용 하 여 **/SUBSYSTEM:CONSOLE** 대신 **/SUBSYSTEM:WINDOWS**합니다. 이 설정에 대한 자세한 내용과 Visual Studio에서 이 속성을 설정하는 방법에 대한 지침은 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)을 참조하세요.

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>64 비트 라이브러리가 32 비트 코드 또는 64 비트 코드를 32 비트 라이브러리에 연결 하려고 하면

라이브러리 및 코드에 연결 된 개체 파일에 대 한 코드와 동일한 아키텍처가 컴파일해야 합니다. 확인 하는 라이브러리 프로젝트와 동일한 아키텍처에 대 한 프로젝트 참조 컴파일됩니다. 있는지 확인은 [/LIBPATH](../../build/reference/libpath-additional-libpath.md) 또는 **추가 라이브러리 디렉터리** 링커 가리키는 올바른 아키텍처에 대해 작성 하는 라이브러리에서 사용 하는 경로 옵션.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>다른 컴파일러 옵션을 사용 하 여 여러 소스 파일에서 함수 인라이닝에 대 한

여러 소스 파일에서 .cpp 파일에 정의된 인라인된 함수를 사용하고 함수 인라이닝 컴파일러 옵션을 혼합하면 LNK2019가 발생할 수 있습니다. 자세한 내용은 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)을 참조하세요.

### <a name="you-use-automatic-variables-outside-their-scope"></a>자동 변수를 사용 하 여 해당 범위 외부

자동(함수 범위) 변수는 해당 함수의 범위 내에서만 사용할 수 있습니다. 이러한 변수는 `extern` 으로 선언할 수 없으며 다른 소스 파일에서 사용할 수 없습니다. 예제를 보려면 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)를 참조하십시오.

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>내장 함수를 호출 하거나 대상 아키텍처에서 지원 되지 않는 내장 함수에 인수 형식을 전달합니다

예들 들어 AVX2 내장 함수를 사용하지만 [/ARCH:AVX2](../../build/reference/arch-x86.md) 컴파일러 옵션을 지정하지 않은 경우, 컴파일러는 내장 함수가 외부 함수라고 가정합니다. 인라인 명령을 생성하는 대신 컴파일러는 내장 함수와 같은 이름의 외부 기호에 대해 호출을 생성합니다. 링커가 이 누락된 함수의 정의를 찾으려고 할 때 LNK2019가 생성됩니다. 대상 아키텍처에서 지원하는 내장 함수 및 형식만 사용하는지 확인하세요.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>네이티브 wchar를 사용 하는 코드를 혼합 하 여\_하지 않은 코드로 t

Visual C++ 2005에서 수행된 C++ 언어 규칙 작업은 `wchar_t` 를 기본적으로 네이티브 형식으로 만듭니다. 이전 버전의 Visual C++를 사용하여 컴파일된 라이브러리 및 개체 파일과 호환되는 코드를 생성하려면 [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 컴파일러 옵션을 사용해야 합니다. 일부 파일이 동일한를 사용 하 여 컴파일되지 않은 경우 **/Zc:wchar\_t** 설정, 형식 참조를 호환 가능한 형식 확인 되지 않을 수 있습니다. 사용된 형식을 업데이트하거나 컴파일할 때 일관된 `wchar_t` 설정을 사용하여 모든 라이브러리 및 개체 파일의 **/Zc:wchar_t** 형식이 호환되는지 확인하세요.

## <a name="third-party-library-issues-and-vcpkg"></a>타사 라이브러리 문제 및 Vcpkg

빌드의 일부로 타사 라이브러리를 구성 하려고 시도할 때이 오류를 표시 하는 경우를 사용해 [Vcpkg](../../vcpkg.md), Visual c + + 패키지 관리자를 설치 하 여 라이브러리를 빌드합니다. 크기가 크고 점점 Vcpkg에서는 [타사 라이브러리 목록이](https://github.com/Microsoft/vcpkg/tree/master/ports), 구성 속성 및 프로젝트의 일부분으로 빌드가 성공한 경우에 필요한 종속성을 가져오거나 설정 합니다. 자세한 내용은 참조는 관련 [Visual c + + 블로그](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) 게시 합니다.

## <a name="diagnosis-tools"></a>진단 도구

링커가 특정 기호 정의를 찾을 수 없는 이유는 확인하기 어려울 수 있습니다. 종종 빌드 정의 포함 하는 코드를 포함 하지 또는 빌드 옵션 다른 만든 데코레이팅된 이름 외부 기호에 대 한 문제가입니다. LNK2019 오류를 진단하는데 도움이 되는 여러 가지 도구 및 옵션이 있습니다.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 링커 옵션은 링커가 참조하는 파일을 확인하는데 도움이 될 수 있습니다. 기호 정의를 포함하는 파일이 빌드에 포함되어 있는지 여부를 확인할 수 있습니다.

- [/exports](../../build/reference/dash-exports.md) 및 [/기호](../../build/reference/symbols.md) 의 옵션은 **DUMPBIN** .dll 및 개체 또는 라이브러리 파일에 정의 된 기호는 검색할 유틸리티 수 있습니다. 내보낸 트데코레이된 이름이 링커가 검색하는 트데코레이된 이름과 일치하는지 확인하세요.

- **UNDNAME** 유틸리티는 트 데코 레이 된 이름에 대 한 해당 하는 데코레이팅되지 않은 외부 기호를 확인할 수 있습니다.

## <a name="examples"></a>예제

LNK2019 오류를 해결하는 방법에 대한 정보와 함께, LNK2019 오류를 유발하는 여러 가지 코드 예제는 다음과 같습니다.

### <a name="a-symbol-is-declared-but-not-defined"></a>기호가 선언되었지만 정의되지 않았습니다.

이 예제에서는 외부 변수가 선언 되었지만 정의 되지 않았습니다.

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

변수 및 함수로 선언 된 다른 예로 `extern` 아니지만 정의가 제공 됩니다.

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

하지 않는 한 `i` 및 `g` 정의 된 링커 빌드에 포함 된 파일 중 하나에 l n k 2019를 생성 합니다. 컴파일의 일부로써 정의를 포함하는 소스 코드 파일을 포함하여 오류를 해결할 수 있습니다. 또는.obj 파일이 나 링커에 정의 포함 하는.lib 파일을 전달할 수 있습니다.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>정적 데이터 멤버가 선언되었지만 정의되지 않았습니다.

정적 데이터 멤버가 선언되었지만 정의되지 않은 경우에도 LNK2019가 발생할 수 있습니다. 다음 샘플에서는 LNK2019가 생성되며 해결 방법을 보여 줍니다.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-do-not-match-definition"></a>선언 매개 변수가 정의와 일치하지 않습니다.

템플릿 함수를 호출하는 코드에는 일치하는 템플릿 함수 선언이 있어야 합니다. 선언에는 정의와 동일한 템플릿 매개 변수가 포함되어야 합니다. 다음 샘플에서는 사용자 정의 연산자에 LNK2019가 생성되고 해결 방법을 보여 줍니다.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class 
Test {
   // The operator<< declaration does not match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-wchart-type-definitions"></a>일관성 없는 wchar_t 형식 정의

이 샘플을 사용 하는 내보내기가 있는 DLL을 만듭니다. `WCHAR`, 확인 되 `wchar_t`합니다.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

다음 샘플 이전 샘플에서 DLL을 사용 하 고 형식을 unsigned short * 및 WCHAR 때문에 l n k 2019를 생성\* 같지 않습니다.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

 이 오류를 해결 하려면 변경 `unsigned short` 를 `wchar_t` 또는 `WCHAR`를 사용 하 여 LNK2019g.cpp를 컴파일 **/Zc:wchar_t-** 합니다.

## <a name="additional-resources"></a>추가 자료

LNK2001에 대 한 가능한 원인 및 해결 하는 방법에 대 한 자세한 내용은 스택 오버플로 질문을 참조 하십시오. [정의 되지 않은 참조/확인 되지 않은 외부 기호 오류가 란 무엇이 고 어떻게 해결 하나요?](http://stackoverflow.com/q/12573816/2002113)합니다.


---
title: main 함수 및 명령줄 인수 (c + +)
description: main함수는 c + + 프로그램의 진입점입니다.
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: b27668c3c7ce77e4369af144bb8be4efb695e522
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499808"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>main 함수 및 명령줄 인수

모든 c + + 프로그램에는 함수가 있어야 합니다 `main` . 함수 없이 c + + *.exe* 프로젝트를 컴파일하려는 경우 main 컴파일러에서 오류가 발생 합니다. 동적 연결 라이브러리 및 static 라이브러리에는 `main` 함수가 없습니다. `main` 함수는 소스 코드의 실행을 시작 하지만 프로그램이 함수를 시작 하기 전에 `main` static 명시적 이니셜라이저가 없는 모든 클래스 멤버가 0으로 설정 됩니다. Microsoft c + +에서는 static 에 대 한 진입 전에 전역 개체도 초기화 됩니다 `main` . `main`다른 c + + 함수에는 적용 되지 않는 함수에는 몇 가지 제한 사항이 적용 됩니다. `main`함수는 다음과 같습니다.

- 오버 로드할 수 없습니다 ( [함수 오버 로드](function-overloading.md)참조).
- 는로 선언할 수 없습니다 **`inline`** .
- 는로 선언할 수 없습니다 **`static`** .
- 주소를 사용할 수 없습니다.
- 호출할 수 없습니다.

main함수는 언어에 기본 제공 되므로 선언이 없습니다. 이 경우의 선언 구문은 `main` 다음과 같습니다.

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 전용**

원본 파일이 유니코드 와이드 acters를 사용 하는 경우 char `wmain` 의 wide acter 버전을 사용할 수 있습니다 char `main` . `wmain`의 선언 구문은 다음과 같습니다.

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

또한 `_tmain` t. h에 정의 된를 사용할 수 있습니다 char . `_tmain``main`_UNICODE 정의 되지 않은 경우으로 확인 됩니다. _UNICODE가 정의된 경우에는 `_tmain`이 `wmain`으로 확인됩니다.

반환 값이 지정 되지 않은 경우 컴파일러는 반환 값 0을 제공 합니다. 또는 `main` 및 함수를 `wmain` **`void`** 반환 (반환 값 없음)으로 선언할 수 있습니다. 또는를 반환 하는 것으로 선언 하는 경우에는 `main` `wmain` **`void`** exit [return](./program-termination.md) 문을 사용 하 여 부모 프로세스 또는 운영 체제에 대 한 코드를 반환할 수 없습니다. exit또는이로 선언 될 때 코드를 반환 하려면 `main` `wmain` 함수를 **`void`** 사용 해야 합니다 [exit](./program-termination.md) .

**Microsoft 전용 종료**

## <a name="command-line-arguments"></a>명령줄 인수

또는에 대 한 인수를 `main` 사용 하면 인수를 편리 하 게 명령줄 `wmain` 구문 분석 하 고, 선택적으로 환경 변수에 액세스할 수 있습니다. `argc` 및 `argv`의 형식은 언어에서 정의됩니다. `argc`, 및 이름은 `argv` 일반적인 이름 `envp` 이지만 원하는 이름을 지정할 수 있습니다.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

인수 정의는 다음과 같습니다.

*argc*<br/>
에서 따르는 인수의 개수를 포함 하는 정수입니다 *argv* . *argc* 매개 변수는 항상 1 보다 크거나 같습니다.

*argv*<br/>
프로그램의 사용자가 입력한 명령줄 인수를 나타내는 null로 끝나는 문자열의 배열입니다. 규칙에 따라 `argv[0]` 은 프로그램을 호출 하는 데 사용 되는 명령이 고, `argv[1]` 첫 번째 명령줄 인수 이며 `argv[argc]` , 항상 NULL이 될 때까지입니다. 명령줄 처리를 억제 하는 방법에 대 한 자세한 내용은 [명령줄 처리 사용자 지정]() 을 참조 하세요.

첫 번째 명령줄 인수는 항상 `argv[1]`이고 마지막 인수는 `argv[argc - 1]`입니다.

> [!NOTE]
> 규칙에 따라 `argv[0]` 는 프로그램 호출에 사용 되는 명령입니다. 그러나를 사용 하 여 프로세스를 생성할 수 [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 있으며 첫 번째 인수와 두 번째 인수 (*lpapplicationname* 및 *lpapplicationname*)를 모두 사용 하는 경우 `argv[0]` 실행 파일 이름이 아닐 수 있습니다. [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 실행 파일 이름 및 정규화 된 경로를 검색 하는 데 사용 합니다.

**Microsoft 전용**

*envp*<br/>
*envp* 대부분의 UNIX 시스템에서 일반적인 확장인 배열은 Microsoft c + +에서 사용 됩니다. 이는 사용자 환경에서 설정된 변수를 나타내는 문자열의 배열입니다. 이 배열은 NULL 항목으로 종료됩니다. ()에 대 한 포인터의 배열 **`char`** `char *envp[]` 또는 **`char`** ()에 대 한 포인터에 대 한 포인터로 선언할 수 있습니다 `char **envp` . 프로그램에서 대신를 사용 하는 경우 대신 `wmain` `main` **`wchar_t`** 데이터 형식을 사용 **`char`** 합니다. 및에 전달 된 환경 블록은 `main` `wmain` 현재 환경의 "고정" 복사본입니다. 이후에 또는에 대 한 호출을 통해 환경을 변경 하는 경우 `putenv` `_wputenv` 현재 환경 ( `getenv` 또는 `_wgetenv` 및 또는 변수에서 반환 `_environ`  `_wenviron` )이 변경 되지만가 가리키는 블록은 envp 변경 되지 않습니다. 환경 처리를 억제 하는 방법에 대 한 자세한 내용은 [명령줄 처리 사용자 지정]() 을 참조 하세요. 이 인수는 C에서는 ANSI와 호환되지만 C++에서는 호환되지 않습니다.

**Microsoft 전용 종료**

### <a name="example"></a>예제

다음 예제에서는 *argc* , 및 인수를 사용 하 여 다음을 수행 하는 방법을 보여 줍니다 *argv* *envp* `main` .

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>C + + 명령줄 인수 구문 분석

**Microsoft 전용**

Microsoft C/c + + 시작 코드에서는 운영 체제 명령줄에 지정 된 인수를 해석할 때 다음 규칙을 사용 합니다.

- 인수를 공백이나 탭으로 구분합니다.

- 캐럿 char acter (^)은 이스케이프 char acter 또는 구분 기호로 인식 되지 않습니다. charActer는 `argv` 프로그램의 배열에 전달 되기 전에 운영 체제의 명령줄 파서에서 완전히 처리 됩니다.

- 큰따옴표 ("*string*")로 둘러싸인 문자열은에 포함 된 공백에 관계 없이 단일 인수로 해석 됩니다. 따옴표로 묶은 문자열은 인수에 포함될 수 있습니다.

- 백슬래시 (") 뒤에 오는 큰따옴표는 \\ 리터럴 큰따옴표 char (")로 해석 됩니다.

- 백슬래시는 큰따옴표 바로 앞에 있지 않으면 리터럴로 해석됩니다.

- 짝수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍 마다 하나의 백슬래시가 배열에 배치 되 고 큰따옴표 `argv` 는 문자열 구분 기호로 해석 됩니다.

- 홀수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍 마다 하나의 백슬래시가 배열에 배치 되 고 큰따옴표는 `argv` 백슬래시를 다시 "이스케이프" main 하므로 리터럴 큰따옴표 (")가에 배치 됩니다 `argv` .

### <a name="example"></a>예제

다음 프로그램은 명령줄 인수를 전달 하는 방법을 보여 줍니다.

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

다음 표에서는 위의 목록에 있는 규칙을 보여 주는 예제 입력 및 예상 출력을 보여 줍니다.

### <a name="results-of-parsing-command-lines"></a>명령줄 구문 분석 결과

|명령줄 입력|argv[1]|argv[2]|argv3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**Microsoft 전용 종료**

## <a name="wildcard-expansion"></a>와일드카드 식

**Microsoft 전용**

명령줄에서 파일 이름과 경로 인수를 지정하기 위해 와일드카드, 즉 물음표(?)와 별표(*)를 사용할 수 있습니다.

명령줄 인수는 `_setargv` `_wsetargv` char 기본적으로 와일드 카드를 문자열 배열의 개별 문자열로 확장 하지 않는 (또는 와이드 acter 환경에서) 호출 된 루틴에 의해 처리 됩니다 `argv` . 와일드 카드 확장을 사용 하는 방법에 대 한 자세한 내용은 [와일드 카드 인수 확장](../c-language/expanding-wildcard-arguments.md)을 참조 하세요.

**Microsoft 전용 종료**

## <a name="customizing-c-command-line-processing"></a>C++ 명령줄 처리 사용자 지정

**Microsoft 전용**

프로그램에서 명령줄 인수를 사용하지 않는 경우 명령줄 처리를 수행하는 라이브러리 루틴의 사용을 억제하여 약간의 공간을 절약할 수 있습니다. 이 루틴은 호출 되며 `_setargv` [와일드 카드 확장]()에 설명 되어 있습니다. 사용 하지 않으려면 함수를 포함 하는 파일에서 아무 작업도 수행 하지 않는 루틴을 정의 하 `main` 고 이름을로 지정 `_setargv` 합니다. 에 대 `_setargv` 한 호출은의 정의에 의해 충족 `_setargv` 되며 라이브러리 버전이 로드 되지 않습니다.

마찬가지로 인수를 통해 환경 테이블에 액세스 하지 않는 경우 `envp` 환경 처리 루틴 대신 사용할 사용자 고유의 빈 루틴을 제공할 수 있습니다 `_setenvp` . `_setargv`함수와 마찬가지로를 `_setenvp` ** extern "C"** 로 선언 해야 합니다.

프로그램에서 `spawn` `exec` C 런타임 라이브러리에 있는 또는 루틴의 집합을 호출할 수 있습니다. 이 루틴이 부모 프로세스에서 자식 프로세스로 환경을 전달 하는 데 사용 되므로 환경 처리 루틴을 억제 해서는 안 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[기본 개념](../cpp/basic-concepts-cpp.md)

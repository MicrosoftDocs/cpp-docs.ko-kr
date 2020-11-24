---
title: '`main` 함수 및 명령줄 인수 (c + +)'
description: '`main`함수는 c + + 프로그램의 진입점입니다.'
ms.date: 11/19/2020
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
ms.openlocfilehash: 8a5ed43bdacf5d9d6dd2cbc5d1c56783c82b8e9a
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483219"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>`main` 함수 및 명령줄 인수

모든 c + + 프로그램에는 함수가 있어야 합니다 `main` . 함수 없이 c + + 프로그램을 컴파일하는 경우 `main` 컴파일러에서 오류가 발생 합니다. 동적 연결 라이브러리 및 static 라이브러리에는 `main` 함수가 없습니다. `main` 함수는 소스 코드의 실행을 시작 하지만 프로그램이 함수를 시작 하기 전에 `main` static 명시적 이니셜라이저가 없는 모든 클래스 멤버가 0으로 설정 됩니다. Microsoft c + +에서는 static 에 대 한 진입 전에 전역 개체도 초기화 됩니다 `main` . `main`다른 c + + 함수에는 적용 되지 않는 함수에는 몇 가지 제한 사항이 적용 됩니다. `main`함수는 다음과 같습니다.

- 오버 로드할 수 없습니다 ( [함수 오버 로드](./function-overloading.md)참조).
- 는로 선언할 수 없습니다 **`inline`** .
- 는로 선언할 수 없습니다 **`static`** .
- 주소를 가져올 수 없습니다.
- 프로그램에서를 호출할 수 없습니다.

## <a name="the-no-locmain-function-signature"></a>`main`함수 시그니처

`main`함수는 언어에 기본 제공 되므로 선언이 없습니다. 이 경우의 선언 구문은 `main` 다음과 같습니다.

```cpp
int main();
int main(int argc, char *argv[]);
```

에 반환 값이 지정 되지 않은 경우 `main` 컴파일러는 반환 값 0을 제공 합니다.

## <a name="standard-command-line-arguments"></a>표준 명령줄 인수

인수를 사용 하면 인수를 편리 하 게 명령줄 `main` 구문 분석할 수 있습니다. `argc` 및 `argv`의 형식은 언어에서 정의됩니다. 및 이름은 `argc` `argv` 일반 이지만 원하는 이름을 지정할 수 있습니다.

인수 정의는 다음과 같습니다.

*`argc`*\
에서 따르는 인수의 개수를 포함 하는 정수입니다 *argv* . *argc* 매개 변수는 항상 1 보다 크거나 같습니다.

*`argv`*\
프로그램의 사용자가 입력한 명령줄 인수를 나타내는 null로 끝나는 문자열의 배열입니다. 규칙에 따라 `argv[0]` 는 프로그램 호출에 사용 되는 명령입니다. `argv[1]` 는 첫 번째 명령줄 인수입니다. 명령줄의 마지막 인수는 이며 `argv[argc - 1]` `argv[argc]` 항상 NULL입니다.

명령줄 처리를 표시 하지 않는 방법에 대 한 자세한 내용은 [c + + 명령줄 처리 사용자 지정](#customize)을 참조 하세요.

> [!NOTE]
> 규칙에 따라 `argv[0]` 는 프로그램의 파일 이름입니다. 그러나 Windows에서는를 사용 하 여 프로세스를 생성할 수 [`CreateProcess`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 있습니다. 첫 번째와 두 번째 인수 (및)를 모두 사용 하는 경우은 *`lpApplicationName`* *`lpCommandLine`* `argv[0]` 실행 파일 이름이 아닐 수 있습니다. [`GetModuleFileName`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)를 사용 하 여 실행 파일 이름 및 정규화 된 경로를 검색할 수 있습니다.

## <a name="microsoft-specific-extensions"></a>Microsoft 전용 확장

다음 섹션에서는 Microsoft 전용 동작에 대해 설명 합니다.

## <a name="the-no-locwmain-function-and-no-loc_tmain-macro"></a>`wmain`함수 및 `_tmain` 매크로

유니코드 와이드 acters를 사용 하도록 소스 코드를 디자인 하는 경우 char `wmain` 의 wide Acter 버전인 Microsoft 전용 진입점을 사용할 수 있습니다 char `main` . 다음은에 대 한 유효한 선언 구문입니다 `wmain` .

```cpp
int wmain();
int wmain(int argc, wchar_t *argv[]);
```

`_tmain`에 정의 된 전처리기 매크로 인 Microsoft 관련를 사용할 수도 있습니다 *`tchar.h`* . `_tmain``main`가 정의 되지 않은 경우은로 확인 됩니다 `_UNICODE` . _UNICODE가 정의된 경우에는 `_tmain`이 `wmain`으로 확인됩니다. `_tmain`매크로와로 시작 하는 기타 매크로는 `_t` 좁게 및 wide acter 집합 모두에 대해 별도의 버전을 작성 해야 하는 코드에 유용 합니다 char . 자세한 내용은 [일반 텍스트 매핑 사용](../c-runtime-library/using-generic-text-mappings.md)을 참조 하세요.

## <a name="returning-no-locvoid-from-no-locmain"></a>반환 `void` 원본 main

Microsoft 확장으로 `main` 및 `wmain` 함수는 반환 값 없음을 반환 하는 것으로 선언할 수 있습니다 **`void`** . 이 확장은 다른 컴파일러 에서도 사용할 수 있지만 사용 하지 않는 것이 좋습니다. `main`에서 값을 반환 하지 않는 경우 대칭에 사용할 수 있습니다.

또는를 반환 하는 것으로 선언 하는 경우 `main` `wmain` **`void`** exit 문을 사용 하 여 부모 프로세스 또는 운영 체제에 대 한 코드를 반환할 수 없습니다 [`return`](./program-termination.md) . exit또는이로 선언 될 때 코드를 반환 하려면 `main` `wmain` 함수를 **`void`** 사용 해야 합니다 [`exit`](./program-termination.md) .

## <a name="the-no-locenvp-command-line-argument"></a>`envp`명령줄 인수

`main`또는 `wmain` 서명을 사용 하면 선택적 Microsoft 전용 확장을 사용 하 여 환경 변수에 액세스할 수 있습니다. 이 확장은 Windows 및 UNIX 시스템의 다른 컴파일러 에서도 일반적으로 사용할 수 있습니다. 이름은 *`envp`* 일반적인 이름 이지만 환경 매개 변수의 이름을 원하는 대로 지정할 수 있습니다. 환경 매개 변수를 포함 하는 인수 목록에 대 한 유효한 선언은 다음과 같습니다.

```cpp
int main(int argc, char* argv[], char* envp[]);
int wmain(int argc, wchar_t* argv[], wchar_t* envp[]);
```

*`envp`*\
선택적 *`envp`* 매개 변수는 사용자 환경에 설정 된 변수를 나타내는 문자열 배열입니다. 이 배열은 NULL 항목으로 종료됩니다. ()에 대 한 포인터의 배열 **`char`** `char *envp[]` 또는 **`char`** ()에 대 한 포인터에 대 한 포인터로 선언할 수 있습니다 `char **envp` . 프로그램에서 대신를 사용 하는 경우 대신 `wmain` `main` **`wchar_t`** 데이터 형식을 사용 **`char`** 합니다.

및에 전달 된 환경 블록은 `main` `wmain` 현재 환경의 "고정" 복사본입니다. 나중에 또는을 호출 하 여 환경을 변경 하는 `putenv` 경우 `_wputenv` 현재 환경 ( `getenv` 또는 `_wgetenv` 및 `_environ` 또는 변수에서 반환  `_wenviron` )이 변경 되지만가 가리키는 블록은 *`envp`* 변경 되지 않습니다. 환경 처리를 억제 하는 방법에 대 한 자세한 내용은 [c + + 명령줄 처리 사용자 지정](#customize)을 참조 하세요. *`envp`* 인수는 c + + 표준이 아닌 C89 표준과 호환 됩니다.

### <a name="example-arguments-to-no-locmain"></a>에 대 한 예제 인수 `main`

다음 예제에서는 *`argc`* , 및 인수를 사용 하 여 다음을 수행 하는 방법을 보여 줍니다 *`argv`* *`envp`* `main` .

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

## <a name="parsing-c-command-line-arguments"></a>C++ 명령줄 인수 구문 분석

Microsoft C/c + + 코드에 사용 되는 명령줄 구문 분석 규칙은 Microsoft 전용입니다. 런타임 시작 코드는 운영 체제 명령줄에 지정 된 인수를 해석할 때 다음 규칙을 사용 합니다.

- 인수를 공백이나 탭으로 구분합니다.

- 첫 번째 인수(`argv[0]`)는 특별하게 처리됩니다. 이 인수는 프로그램 이름을 나타냅니다. 유효한 경로 이름이어야 하므로 큰따옴표( **`"`** )로 묶은 파트가 허용됩니다. 큰따옴표는 `argv[0]` 출력에 포함되지 않습니다. 큰따옴표를 표시 하는 부분은 인수의 끝으로 공백 또는 탭 acter의 해석을 방지 char 합니다. 이 목록의 이후 규칙은 적용되지 않습니다.

- 큰따옴표로 묶은 문자열은 공백 acters을 포함할 수 있는 단일 인수로 해석 됩니다 char . 따옴표로 묶은 문자열은 인수에 포함될 수 있습니다. 캐럿 ( **`^`** )은 이스케이프 char acter 또는 구분 기호로 인식 되지 않습니다. 따옴표 붙은 문자열 내에서 큰따옴표 쌍은 이스케이프된 단일 큰따옴표로 해석됩니다. 닫는 큰따옴표 표시를 찾기 전에 명령줄이 종료 되 면 char 지금까지 읽은 모든 acters 마지막 인수로 출력 됩니다.

- 백슬래시 다음의 큰따옴표( **`\"`** )는 리터럴 큰따옴표( **`"`** )로 해석됩니다.

- 백슬래시는 큰따옴표 바로 앞에 있지 않으면 리터럴로 해석됩니다.

- 짝수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍( **`\\`** )마다 하나의 백슬래시( **`\`** )가 `argv` 배열에 배치되고, 큰따옴표( **`"`** )는 문자열 구분 기호로 해석됩니다.

- 홀수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍( **`\\`** )마다 `argv` 배열에 하나의 백슬래시( **`\`** )가 배치됩니다. 큰따옴표는 백슬래시를 다시 표시 하는 이스케이프 시퀀스로 해석 되어 main 리터럴 큰따옴표 ( **`"`** )가에 배치 됩니다 `argv` .

### <a name="example-of-command-line-argument-parsing"></a>명령줄 인수 구문 분석 예제

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

### <a name="results-of-parsing-command-lines"></a>명령줄 구문 분석 결과

다음 표에서는 위의 목록에 있는 규칙을 보여 주는 예제 입력 및 예상 출력을 보여 줍니다.

| 명령줄 입력 | argv[1] | argv[2] | argv3 |
|--|--|--|--|
| `"abc" d e` | `abc` | `d` | `e` |
| `a\\b d"e f"g h` | `a\\b` | `de fg` | `h` |
| `a\\\"b c d` | `a\"b` | `c` | `d` |
| `a\\\\"b c" d e` | `a\\b c` | `d` | `e` |
| `a"b"" c d` | `ab" c d` |  |  |

## <a name="wildcard-expansion"></a>와일드카드 식

선택적으로 Microsoft 컴파일러에서는 *와일드 카드* char acters 물음표 ( **`?`** )와 별표 ()를 사용 하 여 **`*`** 명령줄에서 파일 이름 및 경로 인수를 지정할 수 있습니다.

명령줄 인수는 런타임 시작 코드의 내부 루틴에 의해 처리 되며, 기본적으로 문자열 배열의 개별 문자열로 와일드 카드를 확장 하지 않습니다 `argv` . *`setargv.obj`* *`wsetargv.obj`* `wmain` **`/link`** 컴파일러 옵션 또는 명령줄에 파일 (파일)을 포함 하 여 와일드 카드 확장을 사용 하도록 설정할 수 있습니다 **`LINK`** .

런타임 시작 링커 옵션에 대 한 자세한 내용은 [Link options](../c-runtime-library/link-options.md)을 참조 하세요.

## <a name="customize-c-command-line-processing"></a><a name="customize"/> C + + 명령줄 처리 사용자 지정

프로그램에서 명령줄 인수를 사용 하지 않는 경우 명령줄 처리 루틴을 억제 하 여 적은 공간을 절약할 수 있습니다. 사용 하지 않으려면 *`noarg.obj`* `main` `wmain` **`/link`** 컴파일러 옵션 또는 명령줄에 파일 (및의 경우)을 포함 합니다 **`LINK`** .

마찬가지로 인수를 통해 환경 테이블에 액세스 하지 않는 경우 *`envp`* 내부 환경 처리 루틴을 표시 하지 않을 수 있습니다. 사용 하지 않으려면 *`noenv.obj`* `main` `wmain` **`/link`** 컴파일러 옵션 또는 명령줄에 파일 (및의 경우)을 포함 합니다 **`LINK`** .

프로그램은 `spawn` `exec` C 런타임 라이브러리에서 또는 루틴의 패밀리를 호출할 수 있습니다. 부모 프로세스에서 자식 프로세스로 환경을 전달 하는 데 사용 되므로 환경 처리 루틴을 억제 하면 안 됩니다.

## <a name="see-also"></a>참조

[기본 개념](../cpp/basic-concepts-cpp.md)

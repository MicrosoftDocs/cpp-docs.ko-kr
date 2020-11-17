---
title: C 명령줄 인수 구문 분석
description: Microsoft C 런타임 시작 코드가 명령줄 인수를 해석하여 argv 및 argc 매개 변수를 만드는 방법을 알아봅니다.
ms.date: 11/09/2020
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- double quote marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
ms.openlocfilehash: 92921e91ee6bb37b2bf7b702a1b31ed045187b59
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441257"
---
# <a name="parsing-c-command-line-arguments"></a>C 명령줄 인수 구문 분석

**Microsoft 전용**

Microsoft C 시작 코드에서는 운영 체제 명령줄에 지정된 인수를 해석할 때 다음 규칙을 사용합니다.

- 인수를 공백이나 탭으로 구분합니다.

- 첫 번째 인수(`argv[0]`)는 특별하게 처리됩니다. 이 인수는 프로그램 이름을 나타냅니다. 유효한 경로 이름이어야 하므로 큰따옴표( **`"`** )로 묶은 파트가 허용됩니다. 큰따옴표는 `argv[0]` 출력에 포함되지 않습니다. 큰따옴표로 묶은 파트는 공백 또는 탭 문자를 인수의 끝으로 해석하는 것을 방지합니다. 이 목록의 이후 규칙은 적용되지 않습니다.

- 큰따옴표로 묶은 문자열은 공백 포함 여부에 상관없이 하나의 인수로 해석됩니다. 따옴표로 묶은 문자열은 인수에 포함될 수 있습니다. 캐럿( **`^`** )은 이스케이프 문자나 구분 기호로 인식되지 않습니다. 따옴표 붙은 문자열 내에서 큰따옴표 쌍은 이스케이프된 단일 큰따옴표로 해석됩니다. 닫는 큰따옴표 전에 명령줄이 끝나면 지금까지 읽은 모든 문자가 마지막 인수로 출력됩니다.

- 백슬래시 다음의 큰따옴표( **`\"`** )는 리터럴 큰따옴표( **`"`** )로 해석됩니다.

- 백슬래시는 큰따옴표 바로 앞에 있지 않으면 리터럴로 해석됩니다.

- 짝수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍( **`\\`** )마다 하나의 백슬래시( **`\`** )가 `argv` 배열에 배치되고, 큰따옴표( **`"`** )는 문자열 구분 기호로 해석됩니다.

- 홀수 개의 백슬래시 다음에 큰따옴표가 오는 경우, 백슬래시 쌍( **`\\`** )마다 `argv` 배열에 하나의 백슬래시( **`\`** )가 배치됩니다. 큰따옴표는 나머지 백슬래시에 의해 이스케이프 시퀀스로 해석되어 리터럴 큰따옴표( **`"`** )가 `argv`에 배치됩니다.

다음 목록은 몇 가지 명령줄 인수 예제의 경우 `argv`에 전달된 해석된 결과를 표시하여 위의 규칙을 보여 줍니다. 두 번째, 세 번째 및 네 번째 열에 나와 있는 출력은 다음 목록 뒤에 나오는 ARGS.C 프로그램에서 제공된 것입니다.

|명령줄 입력|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|
|`a"b"" c d`|`ab" c d`|||

## <a name="example"></a>예제

### <a name="code"></a>코드

```c
// ARGS.C illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
//

#include <stdio.h>

int main( int argc, // Number of strings in array argv
char *argv[],      // Array of command-line argument strings
char **envp )      // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf_s( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf_s( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf_s( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf_s( "  %s\n", *(envp++) );

    return;
}
```

## <a name="comments"></a>주석

이 프로그램의 출력 예는 다음과 같습니다.

```
Command-line arguments:
  argv[0]   C:\MSC\TEST.EXE

Environment variables:
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE

  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;
  PROMPT=[$p]
  TEMP=c:\tmp
  TMP=c:\tmp
  EDITORS=c:\binr
  WINDIR=c:\nt
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[main 함수 및 프로그램 실행](../c-language/main-function-and-program-execution.md)

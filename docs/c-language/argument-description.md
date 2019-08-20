---
title: 인수 설명
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: 88d477c874d62800c47bb03220246cb3f0999724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492515"
---
# <a name="argument-description"></a>인수 설명

**main** 및 **wmain** 함수 안의 `argc` 매개 변수는 명령줄에서 프로그램에 전달되는 인수의 개수를 지정하는 정수입니다. 프로그램 이름이 인수로 간주되므로 `argc`의 값이 1 이상입니다.

## <a name="remarks"></a>설명

`argv` 매개 변수는 프로그램 인수를 나타내며 null로 끝나는 문자열에 대한 포인터의 배열입니다. 배열의 각 요소는 **main** 또는 **wmain**에 전달되는 인수의 문자열 표현을 가리킵니다. 배열에 대한 내용은 [배열 선언](../c-language/array-declarations.md)을 참조하세요. `argv` 형식에 대한 포인터의 배열(`char`) 또는 `char *argv[]` 형식에 대한 포인터의 포인터(`char`)로 `char **argv` 매개 변수를 선언할 수 있습니다. **wmain**의 경우 `wchar_t` 형식에 대한 포인터의 배열(`wchar_t *argv[]`) 또는 `wchar_t` 형식에 대한 포인터의 포인터(`wchar_t **argv`)로 `argv` 매개 변수를 선언할 수 있습니다.

규칙에 따라 `argv` **[0]** 은 프로그램을 호출하는 데 사용하는 명령입니다.  그러나 [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)를 사용하여 프로세스를 생성할 수 있으며 첫 번째 인수와 두 번째 인수(`lpApplicationName` 및 `lpCommandLine`)를 모두 사용할 경우 `argv` **[0]** 이 실행 파일 이름이 아닐 수 있습니다. 실행 파일 이름을 검색하려면 [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)을 사용하세요.

마지막 포인터(`argv[argc]`)는 **NULL**입니다. 환경 변수 정보를 가져오기 위한 다른 방법은 *런타임 라이브러리 참조*의 [getenv](../c-runtime-library/reference/getenv-wgetenv.md)를 참조하세요.

**Microsoft 전용**

`envp` 매개 변수는 사용자의 환경 변수에 설정된 값을 나타내며 null로 끝나는 문자열의 배열에 대한 포인터입니다. `envp`에 대한 포인터의 배열(`char`) 또는 `char *envp[]`에 대한 포인터의 포인터(`char`)로 `char **envp` 매개 변수를 선언할 수 있습니다. **wmain** 함수에서 `wchar_t`에 대한 포인터의 배열(`wchar_t *envp[]`) 또는 `wchar_t`에 대한 포인터의 포인터(`wchar_t **envp`)로 `envp` 매개 변수를 선언할 수 있습니다. **NULL** \*포인터로 배열의 끝을 나타냅니다. **main**이나 **wmain**에 전달된 환경 변수는 현재 환경의 "고정" 복사본입니다. 이후에 _**putenv** 또는 `_wputenv`를 통해 환경을 변경할 경우 현재 환경(`getenv`/`_wgetenv` 및 `_environ` 또는 `_wenviron` 변수에서 반환)이 변경되지만 `envp`가 가리키는 블록은 변경되지 않습니다. `envp` 매개 변수는 C에서 ANSI 호환되지만 C++에서는 그렇지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[main 함수 및 프로그램 실행](../c-language/main-function-and-program-execution.md)

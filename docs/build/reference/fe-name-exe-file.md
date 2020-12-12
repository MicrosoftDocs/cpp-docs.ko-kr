---
description: 자세히 알아보기:/Fe (EXE 파일 이름)
title: /Fe(EXE 파일 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: 551c6f54ba75c71d9229b5a60ff0fdb192dbf100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192280"
---
# <a name="fe-name-exe-file"></a>/Fe(EXE 파일 이름 지정)

컴파일러에서 만든 .exe 파일 또는 DLL의 이름과 디렉터리를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/Fe**[_경로 이름_] \
> **/Fe:** _pathname_

### <a name="arguments"></a>인수

*아니라*<br/>
상대 또는 절대 경로 및 기본 파일 이름 또는 생성 된 실행 파일에 사용할 기본 파일 이름 또는 디렉터리에 대 한 상대 또는 절대 경로입니다.

## <a name="remarks"></a>설명

**/Fe** 옵션을 사용 하면 생성 된 실행 파일에 대 한 출력 디렉터리, 출력 실행 파일 이름 또는 둘 다를 지정할 수 있습니다. *Pathname* 이 경로 구분 기호 (**&#92;**)로 끝나면 출력 디렉터리만 지정 하는 것으로 간주 됩니다. 그렇지 않으면 *pathname* 의 마지막 구성 요소가 출력 파일 기본 이름으로 사용 되 고, 나머지 *경로* 이름은 출력 디렉터리를 지정 합니다. *Pathname* 에 경로 구분 기호가 없으면 현재 디렉터리에 출력 파일 이름을 지정 하는 것으로 간주 됩니다. 공백, 확장 문자 또는 경로 구성 요소와 같은 짧은 경로에 포함할 수 없는 문자를 포함 하는 경우 경로 *이름을* 큰따옴표 (**"**)로 묶어야 합니다 (예: 8 자 이상).

**/Fe** 옵션을 지정 하지 않거나 *pathname* 에 파일 기본 이름을 지정 하지 않은 경우 컴파일러는 명령줄에 지정 된 첫 번째 소스 또는 개체 파일의 기본 이름과 확장명 .exe 또는 .dll을 사용 하 여 출력 파일에 기본 이름을 제공 합니다.

[/C (링크 없이 컴파일)](c-compile-without-linking.md) 옵션을 지정 하는 경우 **/Fe** 는 아무런 영향을 주지 않습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **일반** 속성 페이지를 엽니다.

1. **출력 파일** 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>을 참조하세요.

## <a name="examples"></a>예제

다음 명령줄은 현재 디렉터리에 있는 모든 C 소스 파일을 컴파일하고 연결 합니다. 결과로 생성 되는 실행 파일의 이름은 PROCESS.exe "C:\Users\User Name\repos\My Project\bin" 디렉터리에 생성 됩니다.

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

다음 명령줄은 `C:\BIN` 현재 디렉터리의 첫 번째 원본 파일과 동일한 기본 이름을 사용 하 여에 실행 파일을 만듭니다.

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[경로 이름 지정](specifying-the-pathname.md)<br/>

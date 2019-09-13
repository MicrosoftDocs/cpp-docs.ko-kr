---
title: /Tc, /Tp, /TC, /TP(소스 파일 형식 지정)
ms.date: 01/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927626"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP(소스 파일 형식 지정)

**/Tc** 옵션은 .c 확장명이 없는 경우에도 해당 파일 이름 인수가 c 소스 파일 임을 지정 합니다. **/Tp** 옵션은 .cpp 또는. .cxx 확장명이 없는 경우 C++ 에도 파일 이름 인수가 소스 파일 임을 지정 합니다. 옵션과 파일 이름 사이의 공백은 선택 사항입니다. 각 옵션은 파일 하나를 지정 합니다. 추가 파일을 지정 하려면 옵션을 반복 합니다.

**/Tc** 및 **/tp** 는 **/tc** 및 **/tp**의 전역 변형입니다. 옵션을 기준으로 명령줄의 위치에 관계 없이 명령줄에서 이름이 지정 된 모든 파일을 C소스 파일 ( C++ /tc) 또는 소스 파일 ( **/tp**)로 처리 하도록 컴파일러에 지정 합니다. 이러한 전역 옵션은 **/tc** 또는 **/tp**를 통해 단일 파일로 재정의할 수 있습니다.

## <a name="syntax"></a>구문

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>인수

*filename*<br/>
C 또는 C++ 소스 파일입니다.

## <a name="remarks"></a>설명

기본적으로 **CL** 은 확장명이 .c 인 파일이 c 소스 파일 이며 .cpp 또는 확장명이 .cxx 인 파일이 C++ 소스 파일 이라고 가정 합니다.

**Tc** 또는 **tc** 옵션 중 하나를 지정 하면 [/Zc: Wchar_t (wchar_t is Native Type)](zc-wchar-t-wchar-t-is-native-type.md) 옵션의 지정은 무시 됩니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++**  > **고급** 속성 페이지를 선택하세요.

1. **Compile 이름** 속성을 수정 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 적용 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- [https://docs.microsoft.com/azure/active-directory/develop/scenario-protected-web-api-overview](<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>) 을 참조하세요.

## <a name="examples"></a>예

이 CL 명령줄은 기본 .c, test.txt 및 COLLATE가 모든 C 소스 파일 임을 지정 합니다. CL은 인쇄. prg를 인식 하지 못합니다.

> CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG

이 CL 명령줄은 TEST1. c, .cxx, TEST3 및 TEST4가 C++ 파일로 컴파일되며 TEST5가 c 파일로 컴파일되는 것을 지정 합니다.

> CL TEST1. C TEST2. .CXX TEST3. TEST4. O/Tc TEST5. Z/TP

## <a name="see-also"></a>참고자료

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)

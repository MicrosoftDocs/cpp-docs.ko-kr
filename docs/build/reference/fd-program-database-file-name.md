---
description: 자세히 알아보기:/Fd (프로그램 데이터베이스 파일 이름)
title: /Fd(프로그램 데이터베이스 파일 이름)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: 3990cdd6c560dfdeaef7078a29e965831c2a9504
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200665"
---
# <a name="fd-program-database-file-name"></a>/Fd(프로그램 데이터베이스 파일 이름)

[/Z7,/zi,/zi (디버그 정보 형식)](z7-zi-zi-debug-information-format.md)에 의해 만들어진 PDB (프로그램 데이터베이스) 파일의 파일 이름을 지정 합니다.

## <a name="syntax"></a>구문

```
/Fdpathname
```

## <a name="remarks"></a>설명

**/Fd** 를 사용 하지 않으면 pdb 파일 이름은 기본적으로 VC *x* 0 .pdb로 설정 됩니다. 여기서 *x* 는 사용 중인 Visual C++의 주 버전입니다.

파일 이름을 포함 하지 않는 경로 이름을 지정 하는 경우 (경로가 백슬래시로 끝남) 컴파일러는 지정 된 디렉터리에 VC *x* 0 .pdb 라는 .pdb 파일을 만듭니다.

확장명을 포함 하지 않는 파일 이름을 지정 하는 경우 컴파일러는 확장명으로 .pdb를 사용 합니다.

이 옵션은 최소 다시 빌드 및 증분 컴파일에 사용 되는 상태 (.idb) 파일의 이름을로도 사용 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **출력 파일** 속성 페이지를 클릭합니다.

1. **프로그램 데이터베이스 파일 이름** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>을 참조하세요.

## <a name="example"></a>예제

이 명령줄은 PROG .pdb 라는 .pdb 파일을 만들며 PROG 파일은 PROG입니다.

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[경로 이름 지정](specifying-the-pathname.md)

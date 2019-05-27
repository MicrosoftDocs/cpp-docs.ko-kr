---
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
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292733"
---
# <a name="fd-program-database-file-name"></a>/Fd(프로그램 데이터베이스 파일 이름)

[/Z7, /Zi, /ZI (디버그 정보 형식)](z7-zi-zi-debug-information-format.md)로 생성된 프로그램 데이터베이스(PDB) 파일의 이름을 지정합니다.

## <a name="syntax"></a>구문

```
/Fdpathname
```

## <a name="remarks"></a>설명

**/Fd**가 없으면 PDB 파일 이름의 기본값은 VC*x*0.pdb입니다. 여기서 *x*는 사용 중인 Visual C++의 주 버전입니다.

파일 이름이 포함되지 않은 경로명(백슬래시로 끝나는 경로)으로 지정할 경우 컴파일러는 지정된 디렉터리에 VC*x*0.pdb이라는 .pdb 파일을 만듭니다.

확장자를 포함하지 않는 파일 이름을 지정하면 컴파일러는 .pdb를 확장자로 사용합니다.

또한 이 옵션은 최소 다시 빌드 및 증분 컴파일을 위해 사용되는 상태 (.idb) 파일의 이름을 지정합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **출력 파일** 속성 페이지를 클릭합니다.

1. **프로그램 데이터베이스 파일 이름** 속성을 수정합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>을 참조하세요.

## <a name="example"></a>예제

이 명령줄 PROG.pdb 및 PROG.idb 라는.idb 파일 라는.pdb 파일을 만듭니다.

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>참고자료

[출력 파일(/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)<br/>
[경로 이름 지정](specifying-the-pathname.md)

---
title: /FS(동기 PDB 쓰기 적용)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 97ffb9529087329cf327ba704523b93d5d9b99b1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817597"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS(동기 PDB 쓰기 적용)

프로그램 데이터베이스 (PDB) 파일에 강제로 쓰기-만든 [/Zi](z7-zi-zi-debug-information-format.md) 하거나 [/ZI](z7-zi-zi-debug-information-format.md)-MSPDBSRV 통해 직렬화 해야 합니다. EXE 수 있습니다.

## <a name="syntax"></a>구문

```
/FS
```

## <a name="remarks"></a>설명

기본적으로 때 **/Zi** 하거나 **/ZI** 를 지정 하면 컴파일러는 형식 정보와 기호 디버깅 정보를 쓰도록 PDB 파일을 잠급니다. 이렇게 하면 형식 수가 많을 경우 컴파일러가 형식 정보를 생성하는 데 걸리는 시간을 크게 줄일 수 있습니다. 다른 프로세서(예: 바이러스 백신 프로그램)가 PDB 파일을 일시적으로 잠그는 경우, 컴파일러에 의한 쓰기가 실패하고 치명적인 오류가 발생할 수 있습니다. 이 문제는 또한 여러 cl.exe 복사본이 동일한 PDB 파일에 액세스하는 경우에도 발생할 수 있습니다. 이에 대한 예로는 솔루션에 동일한 중간 디렉터리 또는 출력 디렉터리를 사용하는 독립 프로젝트가 포함되었고 병렬 빌드가 사용하도록 설정된 경우를 예로 들 수 있습니다. 합니다 **/FS** 컴파일러 옵션 컴파일러는 PDB 파일을 잠근 하지 못하도록 하 고 쓰기 MSPDBSRV 통과를 강제로 적용 합니다. EXE가 액세스를 serialize 합니다. 이렇게 하면 빌드가 더 길어질 수 있으며, 여러 cl.exe 인스턴스가 동시에 PDB 파일에 액세스할 때 발생할 수 있는 모든 오류를 방지합니다. 독립 프로젝트가 개별 중간 및 출력 위치에 쓰기를 수행하거나 serialize된 프로젝트 빌드를 강제로 적용하기 위해 프로젝트 중 하나가 서로 종속되도록 솔루션을 변경하는 것이 좋습니다.

합니다 [/MP](mp-build-with-multiple-processes.md) 옵션을 사용 하면 **/FS** 기본적으로 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual Studio에서 설정 C++ 컴파일러 및 빌드 속성](../working-with-project-properties.md)합니다.

1. 선택 된 **C/C++** 폴더입니다.

1. 선택 된 **명령줄** 속성 페이지.

1. 수정 된 **추가 옵션** 포함할 속성을 `/FS` 를 선택한 후 **확인**합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)

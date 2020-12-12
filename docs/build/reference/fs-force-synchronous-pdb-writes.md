---
description: 자세히 알아보기:/FS (동기 PDB 쓰기 적용)
title: /F(동기 PDB 쓰기 적용)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 2dcddd046cc7232f40be5a54d73e659ed099e85d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192033"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/F(동기 PDB 쓰기 적용)

[/Zi](z7-zi-zi-debug-information-format.md) 또는 [/zi](z7-zi-zi-debug-information-format.md)에 의해 생성 되는 프로그램 데이터베이스 (PDB) 파일에 대 한 쓰기를 강제로 MSPDBSRV.EXE를 통해 serialize 합니다.

## <a name="syntax"></a>구문

```
/FS
```

## <a name="remarks"></a>설명

기본적으로 **/zi** 또는 **/zi** 를 지정 하면 컴파일러가 PDB 파일을 잠가 형식 정보 및 기호화 된 디버깅 정보를 씁니다. 이렇게 하면 형식 수가 많을 경우 컴파일러가 형식 정보를 생성하는 데 걸리는 시간을 크게 줄일 수 있습니다. 다른 프로세서(예: 바이러스 백신 프로그램)가 PDB 파일을 일시적으로 잠그는 경우, 컴파일러에 의한 쓰기가 실패하고 치명적인 오류가 발생할 수 있습니다. 이 문제는 또한 여러 cl.exe 복사본이 동일한 PDB 파일에 액세스하는 경우에도 발생할 수 있습니다. 이에 대한 예로는 솔루션에 동일한 중간 디렉터리 또는 출력 디렉터리를 사용하는 독립 프로젝트가 포함되었고 병렬 빌드가 사용하도록 설정된 경우를 예로 들 수 있습니다. **/Fs** 컴파일러 옵션을 사용 하면 컴파일러가 PDB 파일을 잠그지 않고 쓰기를 강제로 수행 하 여 액세스를 serialize 하는 MSPDBSRV.EXE를 통해 수행 됩니다. 이렇게 하면 빌드가 더 길어질 수 있으며, 여러 cl.exe 인스턴스가 동시에 PDB 파일에 액세스할 때 발생할 수 있는 모든 오류를 방지합니다. 독립 프로젝트가 개별 중간 및 출력 위치에 쓰기를 수행하거나 serialize된 프로젝트 빌드를 강제로 적용하기 위해 프로젝트 중 하나가 서로 종속되도록 솔루션을 변경하는 것이 좋습니다.

[/Mp](mp-build-with-multiple-processes.md) 옵션은 기본적으로 **/fs** 를 사용 하도록 설정 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/c + +** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. 포함 하도록 **추가 옵션** 속성을 수정한 `/FS` 다음 **확인** 을 선택 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)

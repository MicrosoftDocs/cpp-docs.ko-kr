---
description: 자세한 정보:/Zf (더 빠른 PDB 생성)
title: /Zf(더 빠른 PDB 생성)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: 6acf84de3c286131f470808505cdf0e895feeaeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178890"
---
# <a name="zf-faster-pdb-generation"></a>/Zf(더 빠른 PDB 생성)

mspdbsrv.exe에 대 한 RPC 호출을 최소화 하 여 병렬 빌드에서 더 빠른 PDB 생성을 사용 하도록 설정 합니다.

## <a name="syntax"></a>Syntax

> **/Zf**

## <a name="remarks"></a>설명

**/Zf** 옵션을 사용 하면 [/Mp (여러 프로세스로 빌드)](mp-build-with-multiple-processes.md) 옵션을 사용 하거나 빌드 시스템 (예: [MSBuild](/visualstudio/msbuild/msbuild-reference) 또는 [cmake](../cmake-projects-in-visual-studio.md))에서 동시에 여러 cl.exe 컴파일러 프로세스를 실행할 때 PDB 파일을 더 빠르게 생성할 수 있습니다. 이 옵션을 선택 하면 컴파일러가 컴파일을 마칠 때까지 PDB 파일의 각 형식 레코드에 대 한 형식 인덱스 생성을 지연 시키고 각 레코드에 대해 RPC 요청을 수행 하는 대신 mspdbsrv.exe에 대 한 단일 RPC 호출로 모두 요청 합니다. 이렇게 하면 여러 cl.exe 컴파일러 프로세스가 동시에 실행 되는 환경에서 mspdbsrv.exe 프로세스에 대 한 RPC 부하를 줄임으로써 빌드 처리량을 크게 향상 시킬 수 있습니다.

**/Zf** 옵션은 PDB 생성에만 적용 되므로 [/zi](z7-zi-zi-debug-information-format.md) 또는 [/zi](z7-zi-zi-debug-information-format.md) 옵션이 필요 합니다.

**/Zf** 옵션은 Visual Studio 2017 버전 15.1부터 사용할 수 있으며 기본적으로 해제 되어 있습니다. Visual Studio 2017 버전 15.7 Preview 3부터 **/zi** 또는 **/zi** 옵션이 설정 된 경우이 옵션은 기본적으로 설정 되어 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zf** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션 사전순 목록](compiler-options-listed-alphabetically.md)<br/>
[/MP (여러 프로세스로 빌드)](mp-build-with-multiple-processes.md)<br/>

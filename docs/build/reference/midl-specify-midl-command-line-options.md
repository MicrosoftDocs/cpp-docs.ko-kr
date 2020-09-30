---
title: /MIDL(MIDL 명령줄 옵션 지정)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: 3f1b6526f51e5aaa48008792361d3e63249d9f16
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502849"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL(MIDL 명령줄 옵션 지정)

MIDL 명령줄 옵션에 대 한 지시 파일을 지정 합니다.

## <a name="syntax"></a>구문

> **/MIDL: \@ ** <em>파일</em>

## <a name="arguments"></a>인수

*file*<br/>
[MIDL 명령줄 옵션](/windows/win32/Midl/general-midl-command-line-syntax)을 포함 하는 파일의 이름입니다.

## <a name="remarks"></a>설명

IDL 파일을 TLB 파일로 변환 하는 모든 옵션을 *파일*에 지정 해야 합니다. MIDL 명령줄 옵션은 링커에 대 한 명령줄에서 지정할 수 없습니다. /MIDL를 지정 하지 않으면 MIDL 컴파일러는 IDL 파일 이름 으로만 호출 되며 다른 옵션은 호출 되지 않습니다.

파일은 한 줄에 하나의 MIDL 명령줄 옵션을 포함 해야 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **포함 IDL** 속성 페이지를 선택 합니다.

1. **MIDL Commands** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[/IDLOUT (MIDL 출력 파일 이름)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (특성을 MIDL로 처리 하지 않음)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (이름. TLB 파일)](tlbout-name-dot-tlb-file.md)<br/>
[특성을 사용하는 프로그램 빌드](../../windows/attributes/cpp-attributes-com-net.md)

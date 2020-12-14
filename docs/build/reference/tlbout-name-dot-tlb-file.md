---
description: 자세히 알아보기:/TLBOUT (이름. TLB 파일)
title: /TLBOUT(.TLB 파일 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 4e99f3b5a036ddbc424732e771f7bab27aeb228d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230005"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT(.TLB 파일 이름 지정)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>인수

*path*<br/>
.Tlb 파일이 생성 되어야 하는 위치에 대 한 절대 또는 상대 경로 지정입니다.

*filename*<br/>
MIDL 컴파일러에 의해 생성 된 .tlb 파일의 이름을 지정 합니다. 파일 확장명을 가정 하지 않습니다. .tlb 확장명을 원하는 경우 *파일 이름*.tlb를 지정 합니다.

## <a name="remarks"></a>설명

/TLBOUT 옵션은 .tlb 파일의 이름과 확장명을 지정 합니다.

MIDL 컴파일러는 [module](../../windows/attributes/module-cpp.md) 특성을 포함 하는 프로젝트를 연결할 때 MSVC 링커에서 호출 합니다.

/TLBOUT를 지정 하지 않으면 .tlb 파일은 [/IDLOUT](idlout-name-midl-output-files.md) *filename* 에서 이름을 가져옵니다. /IDLOUT를 지정 하지 않으면 .tlb 파일이 vc70로 호출 됩니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **포함 된 IDL** 속성 페이지를 클릭 합니다.

1. **형식 라이브러리** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[/IGNOREIDL (특성을 MIDL로 처리 하지 않음)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (MIDL 명령줄 옵션 지정)](midl-specify-midl-command-line-options.md)<br/>
[특성을 사용하는 프로그램 빌드](../../windows/attributes/cpp-attributes-com-net.md)

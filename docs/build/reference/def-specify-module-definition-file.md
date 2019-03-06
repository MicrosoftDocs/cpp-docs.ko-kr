---
title: /DEF(모듈 정의 파일 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: 4b6490186e2faf289844f7fb6b84f5a1c27b10a5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423506"
---
# <a name="def-specify-module-definition-file"></a>/DEF(모듈 정의 파일 지정)

```
/DEF:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
모듈 정의 파일 (.def)을 링커에 전달할의 이름입니다.

## <a name="remarks"></a>설명

/DEF 옵션으로 모듈 정의 파일 (.def)을 링커에 전달 합니다. .Def 파일 하나만 링크를 지정할 수 있습니다. .Def 파일에 대 한 자세한 내용은 참조 하세요 [모듈 정의 파일](../../build/reference/module-definition-dot-def-files.md)합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual c + + 프로젝트 속성 설정](../../ide/working-with-project-properties.md)합니다.

1. 클릭 합니다 **링커** 폴더입니다.

1. 클릭 합니다 **입력** 속성 페이지.

1. 수정 된 **모듈 정의 파일** 속성입니다.

개발 환경 내에서.def 파일을 지정 하려면 다른 파일과 함께 프로젝트에 추가 하 고 /DEF 옵션으로 파일을 지정 해야 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[링커 옵션 설정](../../build/reference/setting-linker-options.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)

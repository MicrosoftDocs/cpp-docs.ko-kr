---
description: 자세히 알아보기:/DEF (Module-Definition 파일 지정)
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
ms.openlocfilehash: 3b9178004621a55f999f7c2636eaa5b697d2de98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201705"
---
# <a name="def-specify-module-definition-file"></a>/DEF(모듈 정의 파일 지정)

```
/DEF:filename
```

## <a name="arguments"></a>인수

*filename*<br/>
링커에 전달 되는 모듈 정의 파일 (.def)의 이름입니다.

## <a name="remarks"></a>설명

/DEF 옵션은 모듈 정의 파일 (.def)을 링커에 전달 합니다. 하나의 .def 파일만 연결 하도록 지정할 수 있습니다. .Def 파일에 대 한 자세한 내용은 [모듈 정의 파일](module-definition-dot-def-files.md)을 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **입력** 속성 페이지를 클릭 합니다.

1. **모듈 정의 파일** 속성을 수정 합니다.

개발 환경 내에서 .def 파일을 지정 하려면 다른 파일과 함께 프로젝트에 .def 파일을 추가한 다음/DEF 옵션으로 파일을 지정 해야 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

---
description: 자세히 알아보기:/MACHINE (대상 플랫폼 지정)
title: /MACHINE(대상 플랫폼 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
ms.openlocfilehash: a1bf87142fb99577672391356a43a2771ea0b09f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190811"
---
# <a name="machine-specify-target-platform"></a>/MACHINE(대상 플랫폼 지정)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>설명

/MACHINE 옵션은 프로그램의 대상 플랫폼을 지정 합니다.

일반적으로 /MACHINE 옵션은 지정할 필요가 없습니다. LINK는 .obj 파일에서 컴퓨터 유형을 유추 합니다. 그러나 경우에 따라 LINK에서 컴퓨터 유형을 확인할 수 없고 [링커 도구 오류 LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)를 발급할 수 있습니다. 이러한 오류가 발생 하는 경우/CD를 지정 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **대상 컴퓨터** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

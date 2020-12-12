---
description: 자세히 알아보기:/DELAYLOAD (가져오기 로드 지연)
title: /DELAYLOAD(가져오기 로드 지연)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: 9f6a91a102b66a16896d51b960d44273a7935d79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201497"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD(가져오기 로드 지연)

> **/DELAYLOAD:**_dllname_

## <a name="parameters"></a>매개 변수

*dllname*<br/>
로드를 지연할 DLL의 이름입니다.

## <a name="remarks"></a>설명

/DELAYLOAD 옵션을 사용하면 `dllname`으로 지정된 DLL에서 프로그램이 함수를 처음 호출할 때만 해당 DLL이 로드됩니다. 자세한 내용은 [Delay-Loaded dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)을 참조 하세요. 이 옵션을 필요한 횟수만큼 사용하여 선택한 수만큼의 DLL을 지정할 수 있습니다. 프로그램을 링크할 때 Delayimp.lib를 사용해야 하거나, 고유한 지연 로드 도우미 함수를 구현할 수 있습니다.

[/Delay](delay-delay-load-import-settings.md) 옵션은 지연 로드 된 각 DLL에 대 한 바인딩 및 로드 옵션을 지정 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더에서 **입력** 속성 페이지를 선택 합니다.

1. **지연 로드 된 dll** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

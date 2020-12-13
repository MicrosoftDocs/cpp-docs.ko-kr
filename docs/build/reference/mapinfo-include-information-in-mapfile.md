---
description: 자세히 알아보기:/MAPINFO (맵 파일에 정보 포함)
title: /MAPINFO(맵파일에 정보 포함)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.MapLines
- VC.Project.VCLinkerTool.MapInfoFixups
- VC.Project.VCLinkerTool.MapExports
- /mapinfo
helpviewer_keywords:
- /MAPINFO linker option
- MAPINFO linker option
- -MAPINFO linker option
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
ms.openlocfilehash: 5cf785182bd91923c3398d542d7e60d9afdb4a4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137906"
---
# <a name="mapinfo-include-information-in-mapfile"></a>/MAPINFO(맵파일에 정보 포함)

```
/MAPINFO:EXPORTS
```

## <a name="remarks"></a>설명

/MAPINFO 옵션을 지정 하면 지정 된 정보를 맵 파일에 포함 하도록 링커에 지시 합니다 .이 옵션은 [/map](map-generate-mapfile.md) 옵션을 지정 하면 생성 됩니다.  내보내기는 내보낸 함수를 포함 하도록 링커에 지시 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버그** 속성 페이지를 클릭 합니다.

1. **맵 내보내기** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

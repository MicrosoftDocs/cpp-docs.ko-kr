---
description: 자세히 알아보기:/MANIFESTFILE (매니페스트 파일 이름)
title: /MANIFESTFILE(매니페스트 파일 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ManifestFile
helpviewer_keywords:
- MANIFESTFILE linker option
- -MANIFESTFILE linker option
- /MANIFESTFILE linker option
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
ms.openlocfilehash: a0d3a4ba1d17c4aa8c97cb09cc768e614e46c864
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138023"
---
# <a name="manifestfile-name-manifest-file"></a>/MANIFESTFILE(매니페스트 파일 이름 지정)

```
/MANIFESTFILE:filename
```

## <a name="remarks"></a>설명

/MANIFESTFILE를 사용 하면 매니페스트 파일의 기본 이름을 변경할 수 있습니다.  매니페스트 파일의 기본 이름은 .manifest가 추가 된 파일 이름입니다.

/MANIFESTFILE는 [/ss](manifest-create-side-by-side-assembly-manifest.md)와도 연결 되지 않은 경우에는 영향을 주지 않습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **매니페스트 파일** 속성 페이지를 선택 합니다.

1. **매니페스트 파일** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

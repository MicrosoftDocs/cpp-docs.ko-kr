---
description: 자세히 알아보기:/RELEASE (체크섬 설정)
title: /RELEASE(체크섬 설정)
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: ed1e55dffb02ace26e91e262bd3e9514f056196e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225325"
---
# <a name="release-set-the-checksum"></a>/RELEASE(체크섬 설정)

```
/RELEASE
```

## <a name="remarks"></a>설명

/RELEASE 옵션은 .exe 파일의 헤더에 체크섬을 설정 합니다.

운영 체제에는 장치 드라이버에 대 한 체크섬이 필요 합니다. 이후 운영 체제와의 호환성을 보장 하기 위해 장치 드라이버의 릴리스 버전에 대 한 체크섬을 설정 합니다.

/RELEASE 옵션은 [/SUBSYSTEM: NATIVE](subsystem-specify-subsystem.md) 옵션이 지정 된 경우 기본적으로 설정 되어 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **Set Checksum** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

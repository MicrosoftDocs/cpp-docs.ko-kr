---
description: 자세히 알아보기:/DRIVER (Windows NT 커널 모드 드라이버)
title: /DRIVER(Windows NT 커널 모드 드라이버)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: a9c066aa58b6cae64bd60ab451c6edd04f71f256
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201094"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER(Windows NT 커널 모드 드라이버)

>/DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>설명

**/DRIVER** 링커 옵션을 사용 하 여 Windows NT 커널 모드 드라이버를 빌드할 수 있습니다.

**/DRIVER: UPONLY** 를 지정 하면 링커가 출력 헤더의 특성에 **IMAGE_FILE_UP_SYSTEM_ONLY** 비트를 추가 하 여이 드라이버가 단일 프로세서 (UP) 드라이버 임을 지정 합니다. 운영 체제는 다중 프로세서 (MP) 시스템에서 UP 드라이버 로드를 거부 합니다.

**/DRIVER: WDM** 에서 링커가 선택적 헤더의 DLLCHARACTERISTICS 필드에 **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** 비트를 설정 하도록 합니다.

**/DRIVER** 를 지정 하지 않으면 링커가 이러한 비트를 설정 하지 않습니다.

**/DRIVER** 가 지정 된 경우:

- **/Fixed: NO** 가 적용 됩니다. 자세한 내용은 [/fixed (고정 기준 주소)](fixed-fixed-base-address.md)를 참조 하세요.

- 출력 파일의 확장명은 .sys로 설정 됩니다. **/Out** 을 사용 하 여 기본 파일 이름 및 확장명을 변경 합니다. 자세한 내용은 [/out (출력 파일 이름)](out-output-file-name.md)을 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **시스템** 속성 페이지를 클릭 합니다.

1. **드라이버** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- [VCLinkerTool 속성](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

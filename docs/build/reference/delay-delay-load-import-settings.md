---
description: 자세히 알아보기:/DELAY (가져오기 설정 지연 로드)
title: /DELAY(가져오기 설정 로드 지연)
ms.date: 01/28/2021
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.openlocfilehash: 0dd6aaaffd378afe4ca7d75180da869b2748d639
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522198"
---
# <a name="delay-delay-load-import-settings"></a>`/DELAY` (가져오기 설정 지연 로드)

런타임에 Dll의 지연 로드를 제어 하는 링커 옵션입니다.

## <a name="syntax"></a>구문

> **`/DELAY:UNLOAD`**\
> **`/DELAY:NOBIND`**

## <a name="remarks"></a>설명

**`/DELAY`** 옵션은 dll의 [지연 로드](linker-support-for-delay-loaded-dlls.md) 를 제어 합니다.

- **`/DELAY:UNLOAD`** 한정자는 지연 로드 도우미 함수에 DLL의 명시적 언로드를 지원 하도록 지시 합니다. IAT(가져오기 주소 테이블)는 원래 폼으로 다시 설정되어 IAT 포인터를 무효화하고 해당 포인터를 덮어쓰게 합니다.

   을 선택 하지 않으면 **`/DELAY:UNLOAD`** 에 대 한 호출이 [`__FUnloadDelayLoadedDLL`](linker-support-for-delay-loaded-dlls.md#explicitly-unload-a-delay-loaded-dll) 실패 합니다.

- 한정자는 런타임에 **`/DELAY:NOBIND`** 바인딩 가능한 IAT를 최종 이미지에 포함 하지 않도록 링커에 지시 합니다. 기본값은 지연 로드된 DLL에 대해 바인딩할 수 있는 IAT를 만드는 것입니다. 결과 이미지는 정적으로 바인딩할 수 없습니다. 바인딩 가능한 Iat 있는 이미지는 실행 전에 정적으로 바인딩될 수 있습니다. 자세한 내용은을 참조 하십시오 [`/BIND`](bind.md) .

   DLL이 바인딩된 경우 도우미 함수는 [`GetProcAddress`](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 참조 되는 각 가져오기에 대해를 호출 하는 대신 바인딩된 정보를 사용 하려고 합니다. 타임 스탬프 또는 기본 설정 주소가 로드 된 DLL의 타임 스탬프 또는 기본 설정 주소와 일치 하지 않는 경우 도우미 함수는 바인딩된 IAT가 만료 된 것으로 가정 합니다. 바인딩된 IAT가 없는 것 처럼 계속 됩니다.

   **`/DELAY:NOBIND`** 프로그램 이미지를 더 크게 만들지만 DLL의 로드 시간을 단축할 수 있습니다. DLL을 바인딩하지 않으려는 경우에는에서 **`/DELAY:NOBIND`** 바인딩된 IAT가 생성 되지 않습니다.

로드를 지연할 Dll을 지정 하려면 옵션을 사용 [`/DELAYLOAD`](delayload-delay-load-import.md) 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요.

1. **구성 속성**  >  **링커**  >  **고급** 속성 페이지를 선택 합니다.

1. **지연 로드 된 DLL** 속성을 수정 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)\
[MSVC 링커 옵션](linker-options.md)

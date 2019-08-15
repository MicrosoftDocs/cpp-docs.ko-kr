---
title: /DELAY(가져오기 설정 로드 지연)
ms.date: 11/04/2016
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
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493003"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY(가져오기 설정 로드 지연)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>설명

/DELAY 옵션은 다음과 같이 Dll의 [지연 로드](linker-support-for-delay-loaded-dlls.md) 를 제어 합니다.

- UNLOAD 한정자는 지연 로드 도우미 함수에 DLL의 명시적 언로드를 지원하도록 지시합니다. IAT(가져오기 주소 테이블)는 원래 폼으로 다시 설정되어 IAT 포인터를 무효화하고 해당 포인터를 덮어쓰게 합니다.

   UNLOAD를 선택 하지 않으면 [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md) 에 대 한 호출이 실패 합니다.

- NOBIND 한정자는 링커에 바인딩할 수 있는 IAT를 최종 이미지에서 제외하도록 지시합니다. 기본값은 지연 로드된 DLL에 대해 바인딩할 수 있는 IAT를 만드는 것입니다. 결과 이미지는 정적으로 바인딩할 수 없습니다. 바인딩할 수 있는 IAT가 포함된 이미지는 실행 전에 정적으로 바인딩할 수 없습니다. [/Cbind](bind.md)를 참조 하십시오.

   DLL이 바인딩된 경우 도우미 함수는 참조 되는 각 가져오기에서 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 를 호출 하는 대신 바인딩된 정보를 사용 하려고 합니다. 타임스탬프 또는 기본 설정 주소가 로드된 DLL의 타임스탬프 또는 기본 설정 주소와 일치하지 않으면 도우미 함수는 바인딩된 IAT가 오래되었다고 가정하고 마치 바인딩된 IAT가 없는 것처럼 진행합니다.

   NOBIND는 프로그램 이미지를 더 크게 만들지만 DLL 로드 시간은 단축할 수 있습니다. DLL 바인딩을 의도하지 않은 경우 NOBIND는 바인딩된 IAT가 생성되지 않도록 합니다.

로드를 지연할 Dll을 지정 하려면 [/DELAYLOAD](delayload-delay-load-import.md) 옵션을 사용 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요.

1. **구성 속성**, **링커**를 확장 한 다음 **고급**을 선택 합니다.

1. **지연 로드 된 DLL** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

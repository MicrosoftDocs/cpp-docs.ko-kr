---
description: 자세히 알아보기:/TSAWARE (터미널 서버 인식 응용 프로그램 만들기)
title: /TSAWARE(터미널 서버 인식 애플리케이션 만들기)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: 6086bdcdf4aa41f116491a602286a0c8410bd61d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171974"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE(터미널 서버 인식 애플리케이션 만들기)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>설명

/TSAWARE 옵션은 프로그램 이미지의 선택적 헤더에 있는 IMAGE_OPTIONAL_HEADER DllCharacteristics 필드에 플래그를 설정 합니다. 이 플래그를 설정하면 터미널 서버가 애플리케이션에서 특정 변경 작업을 수행할 수 없습니다.

응용 프로그램이 터미널 서버를 인식 하지 못하는 경우 (레거시 응용 프로그램이 라고도 함) 터미널 서버는 레거시 응용 프로그램을 수정 하 여 다중 사용자 환경에서 제대로 작동 하도록 합니다. 예를 들어 터미널 서버는 가상 Windows 폴더를 만들어 각 사용자가 시스템의 Windows 디렉터리를 가져오는 대신 Windows 폴더를 가져옵니다. 이를 통해 사용자는 자신의 INI 파일에 액세스할 수 있습니다. 또한 터미널 서버는 레거시 응용 프로그램에 대 한 레지스트리를 일부 조정 합니다. 이러한 수정을 통해 터미널 서버에서 레거시 응용 프로그램을 로드 하는 속도가 느려집니다.

터미널 서버를 인식 하는 응용 프로그램은 설치 하는 동안 INI 파일을 사용 하거나 **HKEY_CURRENT_USER** 레지스트리에 쓰지 않아야 합니다.

/TSAWARE를 사용 하 고 응용 프로그램에서 계속 INI 파일을 사용 하는 경우 시스템의 모든 사용자가 파일을 공유 합니다. 허용 되는 경우에도 응용 프로그램을/TSAWARE에 연결할 수 있습니다. 그렇지 않으면/TSAWARE: NO를 사용 해야 합니다.

/TSAWARE 옵션은 Windows 및 콘솔 응용 프로그램에 대해 기본적으로 사용 하도록 설정 되어 있습니다. 자세한 내용은 [/SUBSYSTEM](subsystem-specify-subsystem.md) 및 [/VERSION](version-version-information.md) 를 참조 하세요.

/TSAWARE는 드라이버 또는 Dll에 사용할 수 없습니다.

응용 프로그램이/TSAWARE에 연결 된 경우 DUMPBIN [/헤더](headers.md) 는 해당 효과에 대 한 정보를 표시 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **시스템** 속성 페이지를 클릭 합니다.

1. **터미널 서버** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[User-Specific 정보 저장](/windows/win32/TermServ/storing-user-specific-information)<br/>
[터미널 서비스 환경의 레거시 응용 프로그램](/previous-versions/aa382957(v=vs.85))

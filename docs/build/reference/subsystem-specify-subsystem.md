---
description: 자세히 알아보기:/SUBSYSTEM (하위 시스템 지정)
title: /SUBSYSTEM(하위 시스템 지정)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: 18a8ad549cc4aa1e143e43619d549c9eb7ae7324
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236245"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM(하위 시스템 지정)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>인수

**BOOT_APPLICATION**<br/>
Windows 부팅 환경에서 실행되는 애플리케이션입니다. 부팅 응용 프로그램에 대 한 자세한 내용은 [BCD 정보](/previous-versions/windows/desktop/bcd/about-bcd)를 참조 하세요.

**CONSOLE**<br/>
Win32 문자 모드 응용 프로그램입니다. 운영 체제는 콘솔 애플리케이션에 콘솔을 제공합니다. `main`또는 `wmain` 이 네이티브 코드에 대해 정의 되어 있거나가 `int main(array<String ^> ^)` 관리 코드에 대해 정의 되어 있거나를 사용 하 여 응용 프로그램을 완전히 빌드하는 경우 `/clr:safe` CONSOLE이 기본값입니다.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
확장 가능한 펌웨어 인터페이스 하위 시스템입니다. 자세한 내용은 EFI 사양을 참조 하십시오. 예제는 Intel 웹 사이트를 참조 하십시오. 최소 버전 및 기본 버전은 1.0입니다.

**전용**<br/>
Windows NT 용 커널 모드 드라이버 이 옵션은 일반적으로 Windows 시스템 구성 요소에 대해 예약 되어 있습니다. [/DRIVER: WDM](driver-windows-nt-kernel-mode-driver.md) 을 지정 하면 NATIVE가 기본값입니다.

**POSIX**<br/>
Windows NT의 POSIX 하위 시스템에서 실행 되는 응용 프로그램입니다.

**WINDOWS**<br/>
응용 프로그램은 사용자와의 상호 작용을 위해 자체 창을 만들기 때문에 콘솔이 필요 하지 않습니다. `WinMain`또는 `wWinMain` 이 네이티브 코드에 대해 정의 되어 있거나 `WinMain(HISTANCE *, HINSTANCE *, char *, int)` `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` 관리 코드에 대해 정의 된 경우 WINDOWS가 기본값입니다.

*주* 및 *부*<br/>
필드 하위 시스템의 최소 필수 버전을 지정 합니다. 인수는 0에서 65535 사이의 10 진수입니다. 자세한 내용은 설명 부분을 참조 하십시오. 버전 번호에 대 한 상한이 없습니다.

## <a name="remarks"></a>설명

**/SUBSYSTEM** 옵션은 실행 파일에 대 한 환경을 지정 합니다.

선택한 하위 시스템은 링커가 선택 하는 진입점 기호 (또는 진입점 함수)에 영향을 줍니다.

하위 시스템의 최소 및 기본 *주* 버전 번호 및 *부* 버전 번호는 다음과 같습니다.

|하위 시스템|최소|기본값|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|CONSOLE|5.01 (x86) 5.02 (x64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|WINDOWS|5.01 (x86) 5.02 (x64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|네이티브 (드라이버: WDM)|1.00 (x86) 1.10 (x64, ARM)|1.00 (x86) 1.10 (x64, ARM)|
|네이티브 (/DRIVER: WDM 불포함)|4.00 (x86) 5.02 (x64) 6.02 (ARM)|4.00 (x86) 5.02 (x64) 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 링커 폴더를 선택합니다.

1. **시스템** 속성 페이지를 선택 합니다.

1. 속성을 수정 `SubSystem` 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

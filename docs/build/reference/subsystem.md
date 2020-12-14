---
description: 자세히 알아보기:/SUBSYSTEM
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem_editbin
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 24c334099eca93fc0f6e5790e78ed99049c572a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230239"
---
# <a name="subsystem"></a>/SUBSYSTEM

실행 가능 이미지에 필요한 실행 환경을 지정합니다.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>설명

이 옵션은 이미지를 편집하여 운영 체제가 실행을 위해 호출해야 하는 하위 시스템을 나타냅니다.

다음과 같은 하위 시스템을 지정할 수 있습니다.

**BOOT_APPLICATION**<br/>
Windows 부팅 환경에서 실행되는 애플리케이션입니다. 부팅 응용 프로그램에 대 한 자세한 내용은 [BCD WMI 공급자 정보](/previous-versions/windows/desktop/bcd/about-bcd)를 참조 하세요.

**CONSOLE**<br/>
Windows 문자 모드 애플리케이션입니다. 운영 체제는 콘솔 애플리케이션에 콘솔을 제공합니다.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
EFI(Extensible Firmware Interface) 이미지

EFI 하위 시스템 옵션은 Extensible Firmware Interface 환경에서 실행되는 실행 가능 이미지에 대해 설명합니다. 이 환경은 일반적으로 하드웨어와 함께 제공되고 운영 체제가 로드되기 전에 실행됩니다. EFI 이미지 형식 간의 주요 차이점은 이미지가 로드되는 메모리 위치와 이미지 호출에서 반환할 때 수행되는 동작입니다. EFI_APPLICATION 이미지는 컨트롤이 반환될 때 언로드됩니다. EFI_BOOT_SERVICE_DRIVER 또는 EFI_RUNTIME_DRIVER는 컨트롤이 반환되고 오류 코드가 표시되는 경우에만 언로드됩니다. EFI_ROM 이미지는 ROM에서 실행됩니다. 자세한 내용은 [통합 EFI 포럼](https://www.uefi.org/) 웹 사이트의 사양을 참조 하십시오.

**전용**<br/>
커널 모드 디바이스 드라이버 및 네이티브 시스템 프로세스와 같이 하위 시스템 환경 없이 실행되는 코드입니다. 이 옵션은 일반적으로 Windows 시스템 기능에 예약되어 있습니다.

**POSIX**<br/>
Windows의 POSIX 하위 시스템에서 실행되는 앱입니다.

**WINDOWS**<br/>
Windows 그래픽 환경에서 실행되는 앱입니다. 여기에는 데스크톱 앱과 UWP (유니버설 Windows 플랫폼) 앱이 모두 포함 됩니다.

**WINDOWSCE**<br/>
WINDOWSCE 하위 시스템은 앱이 Windows CE 커널 버전이 있는 디바이스에서 실행되도록 되어 있음을 나타냅니다. 커널 버전으로는 PocketPC, Windows Mobile, Windows Phone 7, Windows CE V1.0-6.0R3 및 Windows Embedded Compact 7이 있습니다.

선택적 `major` 및 `minor` 값은 지정된 하위 시스템에 필요한 최소 버전을 지정합니다.

- 버전 번호의 정수 부분(소수점 왼쪽에 있는 부분)은 `major`로 나타냅니다.

- 버전 번호의 소수 부분(소수점 오른쪽에 있는 부분)은 `minor`로 나타냅니다.

- `major` 및 `minor` 값은 0에서 65,535 사이여야 합니다.

하위 시스템 선택은 프로그램의 기본 시작 주소에 영향을 줍니다. 자세한 내용은 [/entry (진입점 기호)](entry-entry-point-symbol.md), 링커/entry:*함수* 옵션을 참조 하세요.

각 하위 시스템의 주 버전 및 부 버전 번호에 대 한 최소값 및 기본값을 포함 하 여 자세한 내용은 [/SUBSYSTEM](subsystem-specify-subsystem.md) 링커 옵션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)

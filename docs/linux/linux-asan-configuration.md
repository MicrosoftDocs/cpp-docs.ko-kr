---
title: Address Sanitizer를 사용하도록 Linux 프로젝트 구성
description: Visual Studio에서 Address Sanitizer를 사용하도록 C++ Linux 프로젝트를 구성하는 방법을 설명합니다.
ms.date: 10/7/2020
ms.openlocfilehash: 3c2f78346e4a2049e3482ba4093d8a6212f54e9a
ms.sourcegitcommit: 611e903f222ec794ef14195796b332851ab98904
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847153"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Address Sanitizer를 사용하도록 Linux 프로젝트 구성

Visual Studio 2019 버전 16.1에서 AddressSanitizer(ASan) 지원은 Linux 프로젝트에 통합됩니다. MSBuild 기반 Linux 프로젝트 및 CMake 프로젝트에 ASan을 사용할 수 있습니다. 원격 Linux 시스템 및 WSL(Linux용 Windows 하위 시스템)에서 작동합니다.

## <a name="about-asan"></a>ASan에 대한 정보

ASan은 다음 오류를 감지하는 C/C++에 대한 런타임 메모리 오류 감지기입니다.

- 해제 후 사용(현수 포인터 참조)
- 힙 버퍼 오버플로
- 스택 버퍼 오버플로
- 반환 후 사용
- 범위 지정 후 사용
- 초기화 순서 버그

ASan에서 오류를 감지하면 실행이 즉시 중지됩니다. 디버거에서 ASan 지원 프로그램을 실행하는 경우 오류 유형, 메모리 주소 및 오류가 발생한 원본 파일의 위치를 설명하는 메시지가 표시됩니다.

   ![ASan 오류 메시지](media/asan-error.png)

출력 창의 디버그 창에서 전체 ASan 출력(손상된 메모리가 할당/할당 취소된 위치 포함)을 볼 수도 있습니다.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>MSBuild 기반 Linux 프로젝트에 ASan 사용

> [!NOTE]
> Visual Studio 2019 버전 16.4부터 Linux 프로젝트용 AddressSanitizer는 **프로젝트 속성** > **구성 속성** > **C/C++**  > **Address Sanitizer 사용** 을 통해 사용하도록 설정됩니다.

MSBuild 기반 Linux 프로젝트에 ASan을 사용하려면 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다. 다음으로 **구성 속성** > **C/C++**  > **Sanitizers** 로 이동합니다. ASan은 컴파일러 및 링커 플래그를 통해 활성화되며, 작동하려면 프로젝트를 다시 컴파일해야 합니다.

![MSBuild 프로젝트에 ASan 사용](media/msbuild-asan-prop-page.png)

**구성 속성** > **디버깅** > **AddressSanitizer 런타임 플래그** 로 이동하여 옵션 ASan 런타임 플래그를 전달할 수 있습니다. 아래쪽 화살표를 클릭하여 플래그를 추가하거나 제거합니다.

![ASan 런타임 플래그 구성](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Visual Studio CMake 프로젝트에 ASan 사용

CMake에 ASan을 사용하려면 **솔루션 탐색기** 에서 CMakeLists.txt 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에 대한 CMake 설정** 을 선택합니다.

대화 상자의 왼쪽 창에서 Linux 구성(예: **Linux-Debug** )이 선택되어 있는지 확인합니다.

![Linux 디버그가 구성 옵션 중 하나로 나열된 왼쪽 창의 스크린샷](media/linux-debug-configuration.png)

ASan 옵션은 **일반** 아래에 있습니다. 공백으로 구분된 "flag=value" 양식으로 ASan 런타임 플래그를 입력합니다. UI에서 세미콜론 사용을 잘못 제안합니다. 공백 또는 콜론을 사용하여 플래그를 구분합니다.

![일부 주소 삭제기 런타임 플래그가 표시된 주소 삭제기 사용 옵션의 스크린샷](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>ASan 디버그 기호 설치

ASan 진단을 활성화하려면 원격 Linux 머신 또는 WSL 설치에 해당 디버그 기호(libasan-dbg)를 설치해야 합니다. 로드하는 libasan-dbg의 버전은 Linux 머신에 설치된 GCC의 버전에 따라 달라집니다.

|**ASan 버전**|**GCC 버전**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

이 명령을 사용하여 GCC 버전을 확인할 수 있습니다.

```bash
gcc --version
```

필요한 libasan-dbg의 버전을 보려면 프로그램을 실행한 다음, **출력** 창의 **디버그** 창을 확인합니다. 로드된 ASan의 버전은 Linux 머신에 필요한 libasan-dbg의 버전에 해당합니다. **Ctrl + F** 키를 사용하여 창에서 "libasan"을 검색할 수 있습니다. 예를 들어 libasan4가 있는 경우 다음과 같은 줄이 표시됩니다.

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

다음 명령을 사용하여 apt를 사용하는 Linux 배포판에 ASan 디버그 비트를 설치할 수 있습니다. 이 명령은 버전 4를 설치합니다.

```bash
sudo apt-get install libasan4-dbg
```

Ubuntu에 디버그 기호 패키지를 설치하는 방법에 대한 전체 지침은 [디버그 기호 패키지](https://wiki.ubuntu.com/Debug%20Symbol%20Packages)에 있습니다.

ASan을 사용하는 경우 Visual Studio는 **출력** 창의 **디버그** 창의 맨 위에 ASan 디버그 기호 설치를 묻는 메시지를 표시합니다.

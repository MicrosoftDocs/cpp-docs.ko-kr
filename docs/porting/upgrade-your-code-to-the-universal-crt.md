---
description: '자세한 정보: 코드를 유니버설 CRT로 업그레이드'
title: 코드를 유니버설 CRT로 업그레이드
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: a69643fb2741cef929b7dfc4a3908c8001b367ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331207"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>코드를 유니버설 CRT로 업그레이드

Visual Studio 2015에서 Microsoft CRT(C 런타임 라이브러리)가 리팩터링되었습니다. 표준 C 라이브러리, POSIX 확장 및 Microsoft 전용 함수, 매크로, 전역 변수가 새로운 라이브러리인 유니버설 CRT 또는 UCRT(유니버설 C 런타임 라이브러리)로 이동되었습니다. CRT의 컴파일러별 구성 요소가 새 vcruntime 라이브러리로 이동되었습니다.

UCRT는 이제 Windows 구성 요소이며 Windows 10의 일부로 제공됩니다. UCRT는 C 호출 규칙에 기반을 둔 안정적인 ABI를 지원하고 몇 가지 예외를 제외하고 ISO C99 표준을 철저히 준수합니다. 더 이상 컴파일러의 특정 버전에 연결되지 않습니다. Visual Studio 2015 또는 Visual Studio 2017에서 지원하는 Windows 버전에서 UCRT를 사용할 수 있습니다. 이 방법은 Visual Studio를 업그레이드할 때마다 새 CRT 버전을 대상으로 지정하도록 더 이상 빌드를 업데이트할 필요가 없다는 장점이 있습니다.

이 리팩터링을 통해 대부분 CRT 헤더 파일, 라이브러리 파일 및 재배포 가능 파일의 이름 또는 위치와 코드에 필요한 배포 방법이 변경되었습니다. 또한 UCRT의 많은 함수 및 매크로가 추가되거나 변경되어 표준 준수가 향상되었습니다. 이러한 변경 내용을 이용하려면 기존 코드와 프로젝트 빌드 시스템을 업데이트해야 합니다.

## <a name="where-to-find-the-universal-crt-files"></a>유니버설 CRT 파일의 위치

Windows 구성 요소인 UCRT 라이브러리 파일 및 헤더는 이제 Windows SDK(소프트웨어 개발 키트)에 포함됩니다. Visual Studio를 설치하면 UCRT를 사용하는 데 필요한 Windows SDK 부분도 설치됩니다. Visual Studio 설치 관리자는 UCRT 헤더, 라이브러리 및 DLL 파일의 위치를 Visual Studio 프로젝트 빌드 시스템에 사용되는 기본 경로에 추가합니다. Visual Studio C++ 프로젝트를 업데이트할 때 기본 프로젝트 설정을 사용하면 IDE에서는 자동으로 헤더 파일의 새 위치를 찾고 링커는 자동으로 새로운 기본 UCRT 및 vcruntime 라이브러리를 사용합니다. 마찬가지로 개발자 명령 프롬프트를 사용하여 명령줄 빌드를 실행하면 헤더 및 라이브러리의 경로가 포함된 환경 변수가 업데이트되고 자동으로 작동합니다.

표준 C 라이브러리 헤더 파일은 이제 SDK 버전별 디렉터리에 있는 include 폴더의 Windows SDK에서 찾을 수 있습니다. 헤더 파일에 대 한 일반적인 위치는 windows 키트 10의 Program files 또는 Program Files (x86) 디렉터리에 \\ 있습니다 \\ . 여기서 sdk 버전은 windows \\  \\ 버전 또는  업데이트에 해당 합니다. 예를 들어 windows 10의 기념일 업데이트에 대 한 10.0.14393.0입니다.

C # 또는 Program Files (x86) 디렉터리의 Program files 또는 Program Files (x86) 디렉터리에서 Windows 키트 \\ 10 \\ Lib \\ _sdk-버전_ 을 참조 하세요 \\ \\ . 여기서 _아키텍처_ 는 ARM, x86 또는 X64입니다. 정품 및 디버그 정적 라이브러리는 libucrt.lib 및 libucrtd.lib이고 UCRT DLL용 라이브러리는 ucrt.lib 및 ucrtd.lib입니다.

정품 및 디버그 UCRT DLL은 별도의 위치에 있습니다. 일반 정품 Dll은 재배포 가능 하며, Windows 키트 \\ 10 \\ 재배포 가능 패키지의 \\ \\ \\  program files 또는 program files (x86) 디렉터리에서 찾을 수 있습니다.\. 디버그 프로그램은 재배포 가능 하지 않으며, Windows 키트 \\ 10 \\ bin 아키텍처를 참조 \\  \\ 하세요. 폴더의 program files 또는 program files (x86) 디렉터리에서 찾을 수 있습니다.

C 및 C++ 컴파일러별 런타임 지원 라이브러리인 **vcruntime** 에는 예외 처리 및 내장 함수와 같이 프로그램 시작 및 기능을 지원하는 데 필요한 코드가 포함됩니다. 라이브러리 및 해당 헤더 파일은 Program Files 또는 Program files (x86) 디렉터리의 버전별 Microsoft Visual Studio 폴더에 있습니다. Visual Studio 2017에서 헤더는 Microsoft Visual Studio \\ 2017 \\ _edition_ \\ vc \\ tools \\ MSVC \\ _lib-버전_ \\ 포함에 있으며, 링크 라이브러리는 Microsoft Visual Studio \\ 2017 \\ _edition_ \\ vc tools MSVC에 있습니다. \\ \\ 여기에서 \\  \\ \\  _버전_ 은 Visual Studio가 설치 되어 있고 _lib_ 버전은 라이브러리 버전이 며 _아키텍처_ 는 프로세서 아키텍처입니다. OneCore 및 Store에 대한 링크 라이브러리는 libraries 폴더에도 있습니다. 정적 라이브러리의 정품 및 디버그 버전은 libvcruntime.lib 및 libvcruntimed.lib입니다. 동적 링크 정품 및 디버그 스텁 라이브러리는 각각 vcruntime.lib 및 vcruntimed.lib입니다.

Visual Studio C++ 프로젝트를 업데이트할 때 프로젝트의 **Linker** 속성 **모든 기본 라이브러리 무시** 를 **예** 로 설정했거나 명령줄에서 `/NODEFAULTLIB` 링커 옵션을 사용할 경우에는 새로운 리팩터링된 라이브러리를 포함하도록 라이브러리 목록을 업데이트해야 합니다. 이전 CRT 라이브러리(예: libcmt.lib, libcmtd.lib, msvcrt.lib 또는 msvcrtd.lib)를 해당하는 리팩터링된 라이브러리로 바꿉니다. 사용할 특정 라이브러리에 대한 자세한 내용은 [CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)을 참조하세요.

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>유니버설 CRT의 배포 및 재배포

이제 UCRT는 Microsoft Windows 운영 체제 구성 요소이므로 Windows 10 운영 체제의 일부로 포함되고 Windows Vista부터 Windows 8.1까지 이전 운영 체제에서는 Windows 업데이트를 통해 사용할 수 있습니다. Windows XP의 경우 재배포 가능 버전을 사용할 수 있습니다. 운영 체제 구성 요소로서 UCRT의 업데이트 및 서비스는 Visual Studio 및 Microsoft C++ 컴파일러 버전과는 별개로 Windows 업데이트를 통해 관리됩니다. UCRT는 Windows 구성 요소이므로 안전하고 쉽게 업데이트하고 이미지 크기를 줄일 수 있도록 앱용 UCRT의 중앙 배포를 사용해야 합니다.

Visual Studio 2015 또는 Visual Studio 2017에서 지원하는 Windows 버전에서 UCRT를 사용할 수 있습니다. Windows 10이 아닌 지원되는 다른 버전의 Windows에 대해 vcredist 패키지를 사용하여 재배포할 수 있습니다. vcredist 패키지는 UCRT 구성 요소를 포함하고 이들 구성 요소가 기본적으로 설치되지 않은 Windows 운영 체제에 자동으로 설치합니다. 자세한 내용은 [Visual C++ 파일 재배포](../windows/redistributing-visual-cpp-files.md)를 참조하세요.

UCRT의 app-local 배포가 지원되지만 성능 및 보안상의 이유로 권장되지 않습니다. app-local 배포용 DLL은 **redist** 하위 디렉터리 아래에 Windows SDK의 일부로 포함됩니다. 필요한 DLL에는 ucrtbase.dll 및 api-ms-win-_subset_.dll이라는 **APISet 전달자** DLL 집합이 포함됩니다. 각 운영 체제에서 필요한 DLL 집합은 다르므로 app-local 배포를 사용할 경우 모든 DLL을 포함하는 것이 좋습니다. app-local 배포에 대한 자세한 내용 및 주의할 점은 [Visual C++의 배포](../windows/deployment-in-visual-cpp.md)을 참조하세요.

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>유니버설 CRT 함수 및 매크로에 대한 변경 내용

ISO C99 준수를 향상하고 코드 품질 및 보안 문제를 해결하기 위해 UCRT에서 많은 함수가 추가되거나 업데이트되었습니다. 경우에 따라 이를 위해 라이브러리에 대한 상당한 변경이 필요했습니다. 이전 버전의 CRT를 사용하면 코드가 깔끔하게 컴파일되지만 UCRT를 사용하여 컴파일하면 코드가 중단되는 경우 이러한 업데이트와 기능을 이용하려면 코드를 변경해야 합니다. 유니버설 CRT에 있는 CRT에 대한 주요 변경 내용 및 업데이트의 전체 목록은 Visual C++ 변경 기록의 [CRT(C 런타임 라이브러리)](visual-cpp-change-history-2003-2015.md#BK_CRT) 섹션을 참조하세요. 여기에는 코드에서 필요한 변경 내용을 식별하는 데 사용할 수 있는 영향 받는 헤더 및 함수 목록이 포함됩니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 포팅 및 업그레이드 가이드](visual-cpp-porting-and-upgrading-guide.md)<br/>
[잠재적인 업그레이드 문제 개요(Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[이전 버전의 Visual C++에서 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual C++ 변경 기록 2003 - 2015](visual-cpp-change-history-2003-2015.md)<br/>
[Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md)

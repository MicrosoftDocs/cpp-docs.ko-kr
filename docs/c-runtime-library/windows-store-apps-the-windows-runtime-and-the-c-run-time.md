---
title: UWP 앱, Windows 런타임 및 C 런타임
ms.date: 11/04/2016
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
ms.openlocfilehash: ea6e3e5017fcbef997a1e844e9f84e9c385bd31d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441134"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>UWP 앱, Windows 런타임 및 C 런타임

UWP(유니버설 Windows 플랫폼) 앱은 Windows 8에서 실행되는 Windows 런타임에서 실행하는 프로그램입니다. Windows 런타임은 UWP 앱에서 사용할 수 있는 함수, 변수 및 리소스를 제어하는 신뢰할 수 있는 환경입니다. 그러나 기본적으로 Windows 런타임 제한 때문에 UWP 앱에서 대부분의 CRT(C 런타임 라이브러리) 기능을 사용할 수 없습니다.

Windows 런타임에서는 다음 CRT 기능을 지원하지 않습니다.

- 지원되지 않는 기능과 관련된 대부분의 CRT 함수

   예를 들어 UWP 앱은 루틴의 **exec** 및 **spawn** 패밀리를 사용하여 프로세스를 만들 수 없습니다.

   UWP 앱에서 CRT 함수가 지원되지 않은 경우 이러한 팩트가 해당 참조 아티클에 기록됩니다.

- 대부분의 멀티바이트 문자 및 문자열 함수

   그러나 유니코드 텍스트와 ANSI 텍스트 모두 지원됩니다.

- 콘솔 응용 프로그램 및 명령줄 인수

   그러나 일반적인 데스크톱 응용 프로그램에서도 콘솔 및 명령줄 인수를 지원합니다.

- 환경 변수.

- 현재 작업 디렉터리의 개념

- 정적으로 CRT에 연결되고 [/MT](../build/reference/md-mt-ld-use-run-time-library.md) 또는 `/MTd` 컴파일러 옵션을 사용하여 빌드된 UWP 앱 및 DLL

   즉, CRT의 다중 스레드 정적 버전을 사용하는 응용 프로그램입니다.

- [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 컴파일러 옵션을 사용하여 빌드한 앱

   즉, CRT의 디버그, 다중 스레드 및 DLL 전용 버전입니다. 이러한 앱은 Windows 런타임에서 지원되지 않습니다.

UWP 앱에서 사용할 수 없는 CRT 함수의 전체 목록 및 대체 기능에 대한 제안을 보려면 [유니버설 Windows 플랫폼 앱에는 CRT 함수가 지원 안 됨](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[호환성](../c-runtime-library/compatibility.md)<br/>
[Windows 런타임 지원되지 않는 CRT 함수](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>

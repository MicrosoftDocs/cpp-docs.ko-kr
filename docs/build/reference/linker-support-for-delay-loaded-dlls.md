---
title: 링커의 지연 로드된 DLL 지원
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 248a559735750f912030a37aea85a2cb34156887
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664544"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>링커의 지연 로드된 DLL 지원

Visual c + + 링커는 이제 Dll의 지연된 로드를 지원합니다. 이 줄여 줍니다 Windows SDK 함수를 사용 해야 **LoadLibrary** 하 고 **GetProcAddress** DLL 지연 로드를 구현 합니다.

Visual c + + 6.0 하기 전에 사용 하 여 런타임 시 DLL을 로드 하는 유일한 방법은 했습니다 **LoadLibrary** 및 **GetProcAddress**; 운영 체제 DLL을 로드 하면 실행 파일 또는 로드 된 DLL를 사용 하 여 합니다.

DLL을 사용 하 여 정적으로 연결 하는 경우 Visual c + + 6.0 부터는 링커 지연 하는 옵션이 프로그램 DLL의 함수를 호출할 때까지 DLL 로드를 제공 합니다.

응용 프로그램을 지연 시킬 수를 사용 하 여 DLL을 로드 합니다 [/DELAYLOAD (가져오기 로드 지연)](../../build/reference/delayload-delay-load-import.md) 도우미 함수 (Visual c + +에서 제공 되는 기본 구현)를 사용 하 여 링커 옵션입니다. 도우미 함수를 호출 하 여 런타임 시 DLL을 로드할 됩니다 **LoadLibrary** 하 고 **GetProcAddress** 있습니다.

DLL 지연 로드 하는 경우를 고려해 야 합니다.

- 프로그램은 DLL의 함수를 호출할 수 있습니다.

- 프로그램 실행 년 말에 DLL에서 함수 호출 되지 않을 수 있습니다.

DLL의 지연 된 로드 중 빌드 중 지정할 수는 있습니다. EXE 또는 합니다. DLL 프로젝트입니다. 입니다. 하나 이상의 Dll의 로드를 지연 시키는 DLL 프로젝트 호출 하지 않습니다 자체 지연 로드 된 진입점 Dllmain에서.

다음 항목에서는 Dll 지연 로드를 설명 합니다.

- [지연 로드할 DLL 지정](../../build/reference/specifying-dlls-to-delay-load.md)

- [지연 로드된 DLL의 명시적 언로드](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

- [지연 로드된 DLL에 대한 모든 가져오기 로드](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)

- [가져오기 바인딩](../../build/reference/binding-imports.md)

- [오류 처리 및 알림](../../build/reference/error-handling-and-notification.md)

- [지연 로드된 가져오기 덤프](../../build/reference/dumping-delay-loaded-imports.md)

- [DLL 지연 로드의 제약 조건](../../build/reference/constraints-of-delay-loading-dlls.md)

- [도우미 함수 이해](understanding-the-helper-function.md)

- [사용자 도우미 함수 개발](../../build/reference/developing-your-own-helper-function.md)

## <a name="see-also"></a>참고 항목

[Visual C++의 DLL](../../build/dlls-in-visual-cpp.md)<br/>
[링크](../../build/reference/linking.md)
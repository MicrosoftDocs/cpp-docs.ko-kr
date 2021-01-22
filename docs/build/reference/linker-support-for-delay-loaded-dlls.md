---
description: '자세히 알아보기: 지연 로드 된 Dll에 대 한 링커 지원'
title: 링커의 지연 로드된 DLL 지원
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.openlocfilehash: 9ae1e2c68ed59e742493a9098d98fc35d5f2a7c7
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667273"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>링커의 지연 로드된 DLL 지원

MSVC 링커는 Dll의 지연 로드를 지원 합니다. 이 기능을 사용 하면 Windows SDK 함수를 사용 하 `LoadLibrary` 고 `GetProcAddress` DLL 지연 로드를 구현할 필요가 없습니다.

지연 로드 없이 런타임에 DLL을 로드 하는 유일한 방법은 및를 사용 하는 것 `LoadLibrary` 입니다 `GetProcAddress` . 운영 체제는 dll을 사용 하는 실행 파일이 나 dll이 로드 될 때 dll을 로드 합니다.

지연 로드를 사용 하는 경우 DLL을 암시적으로 연결할 때 링커에서는 프로그램에서 해당 DLL의 함수를 호출할 때까지 DLL 로드를 지연 하는 옵션을 제공 합니다.

응용 프로그램은 도우미 함수를 사용 하 여 [ `/DELAYLOAD` 로드 지연 가져오기)](delayload-delay-load-import.md) 링커 옵션을 사용 하 여 DLL 로드를 지연 시킬 수 있습니다. (기본 도우미 함수 구현은 Microsoft에서 제공 합니다.) 도우미 함수는 런타임에 및를 호출 하 여 런타임에 필요할 때 DLL을 로드 합니다 `LoadLibrary` `GetProcAddress` .

다음과 같은 경우 DLL 로드를 지연 하는 것이 좋습니다.

- 프로그램이 DLL에서 함수를 호출 하지 않을 수 있습니다.

- DLL의 함수는 프로그램의 실행이 지연 될 때까지 호출 되지 않을 수 있습니다.

DLL의 지연 된 로드는 EXE 또는 DLL 프로젝트를 빌드하는 동안 지정할 수 있습니다. 하나 이상의 Dll 자체 로드를 지연 하는 DLL 프로젝트는에서 지연 로드 된 진입점을 호출 해서는 안 `DllMain` 됩니다.

다음 문서에서는 Dll 지연 로드에 대해 설명 합니다.

- [로드를 지연할 Dll 지정](specifying-dlls-to-delay-load.md)

- [지연 로드 된 DLL을 명시적으로 언로드](explicitly-unloading-a-delay-loaded-dll.md)

- [지연 로드 된 DLL에 대 한 모든 가져오기 로드](loading-all-imports-for-a-delay-loaded-dll.md)

- [바인딩 지연 로드 된 가져오기](binding-imports.md)

- [오류 처리 및 알림](error-handling-and-notification.md)

- [덤프 지연 로드 된 가져오기](dumping-delay-loaded-imports.md)

- [DLL 지연 로드의 제약 조건](constraints-of-delay-loading-dlls.md)

- [도우미 함수 이해](understanding-the-helper-function.md)

- [사용자 고유의 도우미 함수 개발](developing-your-own-helper-function.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](../dlls-in-visual-cpp.md)<br/>
[MSVC 링커 참조](linking.md)

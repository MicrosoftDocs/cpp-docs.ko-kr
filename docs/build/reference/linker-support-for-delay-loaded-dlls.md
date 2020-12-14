---
description: 자세한 내용은 Delay-Loaded Dll에 대 한 링커 지원을 확인 하세요.
title: 링커의 지연 로드된 DLL 지원
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 6bf4527d14c7313874f162f0597114132b1a81cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190967"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>링커의 지연 로드된 DLL 지원

이제 MSVC 링커는 Dll의 지연 로드를 지원 합니다. 이렇게 하면 Windows SDK 함수 **LoadLibrary** 및 **GetProcAddress** 를 사용 하 여 DLL 지연 로드를 구현할 필요가 없습니다.

Visual C++ 6.0 이전에는 **LoadLibrary** 및 **GetProcAddress** 를 사용 하 여 DLL을 로드 하는 유일한 방법입니다. 운영 체제는 DLL을 사용 하는 실행 파일이 나 DLL이 로드 될 때 DLL을 로드 합니다.

Visual C++ 6.0부터 DLL을 사용 하 여 암시적으로 링크 하는 경우 링커에서는 프로그램에서 해당 DLL의 함수를 호출할 때까지 DLL을 지연 로드 하는 옵션을 제공 합니다.

응용 프로그램은 도우미 함수 (Visual C++에서 제공 하는 기본 구현)를 사용 하 여 [/DELAYLOAD (가져오기 로드 지연)](delayload-delay-load-import.md) 링커 옵션을 사용 하 여 DLL 로드를 지연 시킬 수 있습니다. 도우미 함수는 런타임에 **LoadLibrary** 및 **GetProcAddress** 를 호출 하 여 DLL을 로드 합니다.

다음과 같은 경우 DLL 로드 지연을 고려해 야 합니다.

- 프로그램은 DLL에서 함수를 호출 하지 않을 수 있습니다.

- DLL의 함수는 프로그램의 실행이 지연 될 때까지 호출 되지 않을 수 있습니다.

중 하나를 빌드하는 동안 DLL의 지연 된 로드를 지정할 수 있습니다. EXE 또는. DLL 프로젝트. 은. 하나 이상의 Dll 로드를 지연 하는 DLL 프로젝트는 Dllmain에서 지연 로드 된 진입점을 호출 하면 안 됩니다.

다음 항목에서는 Dll 지연 로드에 대해 설명 합니다.

- [로드를 지연할 Dll 지정](specifying-dlls-to-delay-load.md)

- [명시적으로 Delay-Loaded DLL 언로드](explicitly-unloading-a-delay-loaded-dll.md)

- [Delay-Loaded DLL에 대 한 모든 가져오기 로드](loading-all-imports-for-a-delay-loaded-dll.md)

- [바인딩 가져오기](binding-imports.md)

- [오류 처리 및 알림](error-handling-and-notification.md)

- [Delay-Loaded 가져오기 덤프](dumping-delay-loaded-imports.md)

- [Dll 지연 로드의 제약 조건](constraints-of-delay-loading-dlls.md)

- [도우미 함수 이해](understanding-the-helper-function.md)

- [사용자 고유의 도우미 함수 개발](developing-your-own-helper-function.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](../dlls-in-visual-cpp.md)<br/>
[MSVC 링커 참조](linking.md)

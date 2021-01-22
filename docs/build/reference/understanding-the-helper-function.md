---
description: 지연 로드 도우미 함수에 대 한 자세한 정보
title: 지연 로드 도우미 함수 이해
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.openlocfilehash: a4b25a51af25458f5add5ed7eb3fd58f759dae7b
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667250"
---
# <a name="understand-the-delay-load-helper-function"></a>지연 로드 도우미 함수 이해

링커 지원 지연 로드에 대 한 도우미 함수는 런타임에 실제로 DLL을 로드 하는 것입니다. 도우미 함수를 수정 하 여 동작을 사용자 지정할 수 있습니다 .에서 제공 된 도우미 함수를 사용 하는 대신 *`delayimp.lib`* 고유한 함수를 작성 하 고 프로그램에 연결 합니다. 하나의 도우미 함수는 모든 지연 로드 된 Dll을 사용 합니다.

DLL 또는 가져오기의 이름을 기반으로 특정 처리를 수행 하려는 경우 자체 버전의 도우미 함수를 제공할 수 있습니다.

도우미 함수는 다음 작업을 수행 합니다.

- 라이브러리에 대 한 저장 된 핸들이 이미 로드 되었는지 확인 합니다.

- `LoadLibrary`를 호출 하 여 DLL 로드를 시도 합니다.

- `GetProcAddress`프로시저의 주소를 가져오기 위해를 호출 합니다.

- 지연 가져오기 로드 썽크로 반환 되어 현재 로드 된 진입점을 호출 합니다.

도우미 함수는 다음 작업을 수행할 때마다 프로그램의 알림 후크를 다시 호출할 수 있습니다.

- 도우미 함수가 시작 될 때

- `LoadLibrary`도우미 함수에서가 호출 되기 직전

- `GetProcAddress`도우미 함수에서가 호출 되기 직전

- 도우미 함수에서에 대 한 호출이 `LoadLibrary` 실패 하면

- 도우미 함수에서에 대 한 호출이 `GetProcAddress` 실패 하면

- 도우미 함수 처리가 완료 된 후

이러한 각 후크 지점은 지연 가져오기 로드 썽크로의 반환을 제외 하 고 특정 방식으로 도우미 루틴의 정상적인 처리를 변경 하는 값을 반환할 수 있습니다.

기본 도우미 코드는 *`Delayhlp.cpp`* 및 *`Delayimp.h`* (vc 디렉터리)에서 찾을 수 있으며 *`include`* 에서 *`Delayimp.lib`* (vc *`lib`* 디렉터리에서) 컴파일됩니다. 사용자 고유의 도우미 함수를 작성 하지 않는 한이 라이브러리를 컴파일에 포함 해야 합니다.

다음 문서에서는 도우미 함수에 대해 설명 합니다.

- [Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [호출 규칙, 매개 변수, 반환 형식](calling-conventions-parameters-and-return-type.md)

- [구조체 및 상수 정의](structure-and-constant-definitions.md)

- [필요한 값 계산](calculating-necessary-values.md)

- [지연 로드 된 DLL을 명시적으로 언로드](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)

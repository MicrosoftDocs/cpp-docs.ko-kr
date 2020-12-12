---
description: '자세히 알아보기: 도우미 함수 이해'
title: 도우미 함수 이해
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: d47e392d78d6cf872af28b992885c57d34bddf0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247100"
---
# <a name="understanding-the-helper-function"></a>도우미 함수 이해

링커 지원 지연 로드에 대 한 도우미 함수는 런타임에 실제로 DLL을 로드 하는 것입니다. 도우미 함수를 수정 하 여 사용자 고유의 함수를 작성 하 고 Delayimp.lib에서 제공 된 도우미 함수를 사용 하는 대신 프로그램에 연결 하 여 동작을 사용자 지정할 수 있습니다. 하나의 도우미 함수는 모든 지연 로드 된 Dll을 사용 합니다.

DLL 또는 가져오기의 이름을 기반으로 특정 처리를 수행 하려는 경우 자체 버전의 도우미 함수를 제공할 수 있습니다.

도우미 함수는 다음 작업을 수행 합니다.

- 라이브러리에 대 한 저장 된 핸들이 이미 로드 되었는지 확인 합니다.

- **LoadLibrary** 를 호출 하 여 DLL의 로드를 시도 합니다.

- 는 **GetProcAddress** 를 호출 하 여 프로시저의 주소를 가져옵니다.

- 지연 가져오기 로드 썽크로 반환 되어 현재 로드 된 진입점을 호출 합니다.

도우미 함수는 다음 작업을 수행할 때마다 프로그램의 알림 후크를 다시 호출할 수 있습니다.

- 도우미 함수가 시작 될 때

- 도우미 함수에서 **LoadLibrary** 가 호출 되기 직전

- Helper 함수에서 **GetProcAddress** 를 호출 하기 직전

- 도우미 함수에서 **LoadLibrary** 를 호출 하지 못한 경우

- 도우미 함수의 **GetProcAddress** 호출이 실패 한 경우

- 도우미 함수 처리가 완료 된 후

이러한 각 후크 지점은 지연 가져오기 로드 썽크로의 반환을 제외 하 고 일부 방법으로 도우미 루틴의 정상 처리를 변경 하는 값을 반환할 수 있습니다.

기본 도우미 코드는 Delayhlp 및 Delayimp.lib (vc\include)에서 찾을 수 있으며 Delayimp.lib (vc\lib)에서 컴파일됩니다. 사용자가 직접 도우미 함수를 작성 하지 않는 한이 라이브러리를 컴파일에 포함 해야 합니다.

다음 항목에서는 도우미 함수에 대해 설명 합니다.

- [Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [호출 규칙, 매개 변수 및 반환 형식](calling-conventions-parameters-and-return-type.md)

- [구조체 및 상수 정의](structure-and-constant-definitions.md)

- [필요한 값 계산](calculating-necessary-values.md)

- [Delay-Loaded DLL 언로드](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)

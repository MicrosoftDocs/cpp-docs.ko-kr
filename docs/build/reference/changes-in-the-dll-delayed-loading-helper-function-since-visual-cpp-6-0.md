---
description: '자세한 정보: Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용'
title: Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.openlocfilehash: a83d5e2895863efde396c48d68316e32aa42a2a1
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666968"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용

컴퓨터에 여러 버전의 Visual C++가 있거나 자체 도우미 함수를 정의한 경우 DLL 지연 로드 도우미 함수를 변경한 내용이 영향을 받을 수 있습니다. 다음은 그 예입니다. 

- **`__delayLoadHelper`** 현재 `__delayLoadHelper2`

- `__pfnDliNotifyHook`는 이제 `__pfnDliNotifyHook2`입니다.

- `__pfnDliFailureHook`는 이제 `__pfnDliFailureHook2`입니다.

- `__FUnloadDelayLoadedDLL`는 이제 `__FUnloadDelayLoadedDLL2`입니다.

> [!NOTE]
> 기본 도우미 함수를 사용 하는 경우 이러한 변경 내용이 영향을 받지 않습니다. 링커를 호출 하는 방법에 대 한 변경 내용은 없습니다.

## <a name="multiple-versions-of-visual-c"></a>여러 버전의 Visual C++

컴퓨터에 여러 버전의 Visual C++ 있는 경우 링커가 일치 하는지 확인 *`delayimp.lib`* 합니다. 일치 하지 않는 경우 또는 확인 되지 `___delayLoadHelper2@8` 않은 외부 기호로 링커 오류 보고를 받게 됩니다 `___delayLoadHelper@8` . 이전에는 이전을 사용 하 여 새 링커를 암시 *`delayimp.lib`* 하며, 후자는 새로운를 사용 하는 이전 링커를 의미 합니다 *`delayimp.lib`* .

확인 되지 않은 링커 오류가 발생 하는 경우 [`dumpbin /linkermember:1`](linkermember.md) 도우미 함수를 포함 하는 것으로 간주 되는에서를 실행 하 여 *`delayimp.lib`* 정의 된 도우미 함수를 확인 합니다. 도우미 함수는 개체 파일에도 정의 될 수 있습니다. [`dumpbin /symbols`](symbols.md) 을 실행 하 고 `delayLoadHelper` 또는을 찾습니다 `delayLoadHelper2` .

Visual C++ 6.0 링커가 있는 경우 다음을 수행 합니다.

- **`dumpbin`** 지연 로드 도우미의 또는 파일에서를 실행 *`.lib`* 하 여 *`.obj`* 이 정의 되었는지 여부를 확인 `__delayLoadHelper2` 합니다. 그렇지 않으면 링크가 실패 합니다.

- `__delayLoadHelper`지연 로드 도우미의 또는 파일에서를 정의 *`.lib`* *`.obj`* 합니다.

## <a name="user-defined-helper-function"></a>사용자 정의 도우미 함수

사용자 고유의 도우미 함수를 정의 하 고 현재 버전의 Visual C++을 사용 하는 경우 다음 단계를 수행 합니다.

- 도우미 함수의 이름을으로 바꿉니다 `__delayLoadHelper2` .

- 지연 설명자 (의)에 있는 포인터가 `ImgDelayDescr` *`delayimp.h`* 32 비트 및 64 비트 프로그램에서 모두 예상 대로 작동 하도록 절대 주소 (VAs)에서 상대 주소 (rva)로 변경 되었으므로 이러한 rva를 다시 포인터로 변환 해야 합니다. 에서 발견 된 새 함수가 도입 `PFromRva` *`delayhlp.cpp`* 되었습니다. 설명자의 각 필드에 대해이 함수를 사용 하 여 32 비트 또는 64 비트 포인터로 다시 변환할 수 있습니다. 기본 지연 로드 도우미 함수는 예제로 사용 하기에 좋은 템플릿으로 계속 사용 됩니다.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>지연 로드 된 DLL에 대 한 모든 가져오기 로드

링커에서는 지정 된 DLL에서 모든 가져오기를 로드 하 여 지연 로드 되도록 할 수 있습니다. 자세한 내용은 [지연 로드 된 DLL에 대 한 모든 가져오기 로드](loading-all-imports-for-a-delay-loaded-dll.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)

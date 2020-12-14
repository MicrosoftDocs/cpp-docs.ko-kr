---
description: '자세한 정보: Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용'
title: Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 0141467aab0b804cf82d21c15510d8f9941853a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182491"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Visual C++ 6.0 이후 DLL 지연 로드 도우미 함수의 변경 내용

컴퓨터에 여러 버전의 Visual C++가 있거나 사용자 고유의 도우미 함수를 정의한 경우 DLL 지연 로드 도우미 함수에 대 한 변경 내용의 영향을 받을 수 있습니다. 예를 들어:

- 이제 **__delayLoadHelper** **__delayLoadHelper2**

- 이제 **__pfnDliNotifyHook** **__pfnDliNotifyHook2**

- 이제 **__pfnDliFailureHook** **__pfnDliFailureHook2**

- 이제 **__FUnloadDelayLoadedDLL** **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> 기본 도우미 함수를 사용 하는 경우 이러한 변경 내용은 영향을 주지 않습니다. 링커를 호출 하는 방법에 대 한 변경 내용은 없습니다.

## <a name="multiple-versions-of-visual-c"></a>여러 버전의 Visual C++

컴퓨터에 Visual C++ 버전이 여러 개 있는 경우 링커가 delayimp.lib과 일치 하는지 확인 합니다. 일치 하지 않는 경우 또는 확인 되지 `___delayLoadHelper2@8` 않은 외부 기호로 링커 오류 보고를 가져옵니다 `___delayLoadHelper@8` . 이전에는 이전 delayimp.lib를 사용 하 여 새 링커를 암시 하며, 후자는 새 delayimp.lib를 사용 하는 이전 링커를 의미 합니다.

확인 되지 않은 링커 오류가 발생 하는 경우 도우미 함수를 포함 하 여 정의 된 도우미 함수를 확인 하는 delayimp.lib에서 [dumpbin/linkermember](linkermember.md): 1을 실행 합니다. 도우미 함수는 개체 파일에도 정의 될 수 있습니다. [dumpbin/symbols](symbols.md) 을 실행 하 고를 찾습니다 `delayLoadHelper(2)` .

Visual C++ 6.0 링커가 있는 경우 다음을 수행 합니다.

- 지연 로드 도우미의 .lib 또는 .obj 파일에서 dumpbin을 실행 하 여 **__delayLoadHelper2** 정의 하는지 여부를 확인 합니다. 그렇지 않으면 링크가 실패 합니다.

- 지연 로드 도우미의 .lib 또는 .obj 파일에 **__delayLoadHelper** 를 정의 합니다.

## <a name="user-defined-helper-function"></a>User-Defined 도우미 함수

사용자 고유의 도우미 함수를 정의 하 고 현재 버전의 Visual C++을 사용 하는 경우 다음을 수행 합니다.

- 도우미 함수의 이름을 **__delayLoadHelper2** 로 바꿉니다.

- 지연 설명자의 포인터 (delayimp.lib의 ImgDelayDescr)가 32 및 64 비트 프로그램에서 모두 예상 대로 작동 하도록 상대 주소 (Rva)로 변경 되었으므로 이러한 포인터를 다시 포인터로 변환 해야 합니다. 새 함수가 추가 되었습니다. PFromRva는 delayhlp에 있습니다. 설명자의 각 필드에 대해이 함수를 사용 하 여 32 또는 64 비트 포인터로 다시 변환할 수 있습니다. 기본 지연 로드 도우미 함수는 예제로 사용 하기에 좋은 템플릿으로 계속 사용 됩니다.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Delay-Loaded DLL에 대 한 모든 가져오기 로드

링커에서는 지정 된 DLL에서 모든 가져오기를 로드 하 여 지연 로드 되도록 할 수 있습니다. 자세한 내용은 [Delay-Loaded DLL에 대 한 모든 가져오기 로드](loading-all-imports-for-a-delay-loaded-dll.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)

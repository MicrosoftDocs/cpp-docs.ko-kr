---
description: 지연 로드 된 DLL에 대 한 모든 가져오기 로드에 대해 자세히 알아보기
title: 지연 로드 된 DLL에 대 한 모든 가져오기 로드
ms.date: 01/19/2021
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.openlocfilehash: b197c50d3b6b68d77dbfccda99e3c2986c515204
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667217"
---
# <a name="load-all-imports-for-a-delay-loaded-dll"></a>지연 로드 된 DLL에 대 한 모든 가져오기 로드

`__HrLoadAllImportsForDll`에 정의 된 함수는 링커 *`delayhlp.cpp`* 옵션으로 지정 된 DLL에서 모든 가져오기를 로드 하도록 링커에 지시 합니다 [`/delayload`](delayload-delay-load-import.md) .

모든 가져오기를 로드 하면 오류 처리를 코드의 한 위치에 배치할 수 있으며 가져오기에 대 한 실제 호출에 대 한 예외 처리를 사용할 필요가 없습니다. 또한 도우미 코드가 가져오기를 로드 하지 못하는 결과로 응용 프로그램이 프로세스를 통해 부분적으로 실패 하는 상황을 방지 합니다.

호출은 `__HrLoadAllImportsForDll` 후크 및 오류 처리 동작을 변경 하지 않습니다. 자세한 내용은 [오류 처리 및 알림](error-handling-and-notification.md)을 참조 하세요.

에 전달 된 DLL 이름은 `__HrLoadAllImportsForDll` dll 자체 내에 저장 된 이름과 비교 되며 대/소문자를 구분 합니다.

다음 예제에서는를 호출 하는 방법을 보여 줍니다 `__HrLoadAllImportsForDll` .

```C
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)

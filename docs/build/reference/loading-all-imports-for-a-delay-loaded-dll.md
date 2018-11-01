---
title: 지연 로드된 DLL에 대한 모든 가져오기 로드
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: a9e9df6b0bae49eaf599e56e5d96040afae315e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536567"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>지연 로드된 DLL에 대한 모든 가져오기 로드

합니다 **__HrLoadAllImportsForDll** delayhlp.cpp에 정의 된 함수에는 지정 된 DLL에서 모든 가져오기 로드 하도록 링커에 지시 합니다 [/delayload](../../build/reference/delayload-delay-load-import.md) 링커 옵션.

모든 가져오기 로드 기능을 사용 하면 코드에서 한 곳에서 오류 처리 및 예외 처리를 실제로 가져오기 호출할 때 사용할 필요가 없습니다. 또한 가져오기 로드에 실패 하는 도우미 코드의 결과로 프로세스를 통해 응용 프로그램을 부분적으로 실패 하는 상황을 방지 합니다.

호출 **__HrLoadAllImportsForDll** 후크 및 오류 동작을 변경 하지 않는 참조 처리; [오류 처리 및 알림](../../build/reference/error-handling-and-notification.md) 자세한 내용은 합니다.

DLL 이름에 전달 **__HrLoadAllImportsForDll** DLL 자체 내에 저장 하는 이름을 비교 되 고 대 소문자를 구분 합니다.

다음 예제에서는 호출 하는 방법을 보여 줍니다 **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](../../build/reference/linker-support-for-delay-loaded-dlls.md)
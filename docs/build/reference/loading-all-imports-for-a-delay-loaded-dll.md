---
description: '자세한 정보: Delay-Loaded DLL에 대 한 모든 가져오기 로드'
title: 지연 로드된 DLL에 대한 모든 가져오기 로드
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: 0f1334f30568e4722bd97579145ddcae9851b901
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190925"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>지연 로드된 DLL에 대한 모든 가져오기 로드

Delayhlp에 정의 된 **__HrLoadAllImportsForDll** 함수는 [/delayload](delayload-delay-load-import.md) 링커 옵션을 사용 하 여 지정 된 DLL의 모든 가져오기를 로드 하도록 링커에 지시 합니다.

모든 가져오기를 로드 하면 오류 처리를 코드의 한 위치에 배치할 수 있으며 가져오기에 대 한 실제 호출에 대 한 예외 처리를 사용할 필요가 없습니다. 또한 도우미 코드의 결과로 가져오기를 로드 하지 못하는 결과로 응용 프로그램이 부분적으로 프로세스를 통해 실패 하는 상황을 방지 합니다.

**__HrLoadAllImportsForDll** 를 호출 해도 후크 및 오류 처리 동작은 변경 되지 않습니다. 자세한 내용은 [오류 처리 및 알림](error-handling-and-notification.md) 을 참조 하세요.

**__HrLoadAllImportsForDll** 전달 되는 DLL 이름은 dll 자체 내에 저장 된 이름과 비교 되며 대/소문자를 구분 합니다.

다음 예에서는 **__HrLoadAllImportsForDll** 를 호출 하는 방법을 보여 줍니다.

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)

---
description: 로드 지연에 대 한 Dll 지정에 대해 자세히 알아보기
title: 로드를 지연할 Dll 지정
ms.date: 01/19/2021
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.openlocfilehash: de8c2e3cb9605cbc6dbc215a0449348c12295c17
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667505"
---
# <a name="specify-dlls-to-delay-load"></a>로드를 지연할 Dll 지정

링커 옵션을 사용 하 여 로드를 지연할 Dll을 지정할 수 있습니다 [`/delayload:dllname`](delayload-delay-load-import.md) . 자체 버전의 도우미 함수를 사용 하지 않으려는 경우 프로그램을 *`delayimp.lib`* (데스크톱 응용 프로그램의 경우) 또는 *`dloadhelper.lib`* (UWP 앱의 경우)와 연결 해야 합니다.

다음은 DLL을 지연 로드 하는 간단한 예입니다.

```cpp
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

프로젝트의 디버그 버전을 빌드합니다. 디버거를 사용 하 여 코드를 단계별로 실행 하면 *`user32.dll`* 가 호출 될 때만 로드 됩니다 `MessageBox` .

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)

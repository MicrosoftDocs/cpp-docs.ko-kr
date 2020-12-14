---
description: '자세한 정보: 로드 지연에 대 한 Dll 지정'
title: 지연 로드할 DLL 지정
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: ece96ea6f818c7e0bc6b6e032ce523e96a9f4ecb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224545"
---
# <a name="specifying-dlls-to-delay-load"></a>지연 로드할 DLL 지정

[/Delayload](delayload-delay-load-import.md): 링커 옵션을 사용 하 여 로드를 지연할 dll을 지정할 수 있습니다 `dllname` . 자체 버전의 도우미 함수를 사용하려는 경우가 아니면 delayimp.lib(데스크톱 애플리케이션) 또는 dloadhelper.lib(스토어 앱)를 사용하여 프로그램을 연결해야 합니다.

다음은 DLL 지연 로드의 간단한 예입니다.

```
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

프로젝트의 디버그 버전을 빌드합니다. 디버거를 사용하여 코드를 단계별로 이동하면 user32.dll이 `MessageBox`를 호출할 때만 로드된다는 것을 알 수 있습니다.

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)

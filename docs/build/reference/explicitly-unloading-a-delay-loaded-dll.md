---
description: '자세한 정보: 명시적으로 Delay-Loaded DLL 언로드'
title: 지연 로드된 DLL의 명시적 언로드
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: 03df08487acc1be05226021d6b7c1593eb0f031b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192384"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>지연 로드된 DLL의 명시적 언로드

[/Delay](delay-delay-load-import-settings.md): unload 링커 옵션을 사용 하면 지연 로드 된 DLL을 언로드할 수 있습니다. 기본적으로 코드에서 DLL을 언로드할 때 (/delay: unload 및 **__FUnloadDelayLoadedDLL2** 사용) 지연 로드 된 가져오기는 IAT (가져오기 주소 테이블)에 남아 있습니다. 그러나 링커 명령줄에서/delay: unload를 사용 하는 경우 도우미 함수는 DLL의 명시적 언로드를 지원 하 여 IAT를 원래 형식으로 다시 설정 합니다. 지금은 잘못 된 포인터를 덮어씁니다. IAT는 원래 IAT의 복사본 주소 (있는 경우)를 포함 하는 [ImgDelayDescr](calling-conventions-parameters-and-return-type.md) 의 필드입니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>주석

지연 로드 된 DLL 언로드에 대 한 중요 정보:

- \VC7\INCLUDE\DELAYHLP. 파일에서 **__FUnloadDelayLoadedDLL2** 함수의 구현을 찾을 수 있습니다. .CPP.

- **__FUnloadDelayLoadedDLL2** 함수의 name 매개 변수는 가져오기 라이브러리에 포함 된 내용 (대/소문자 포함)을 정확히 일치 해야 합니다 (해당 문자열은 이미지의 가져오기 테이블에도 해당). [DUMPBIN/종속](dependents.md)항목을 사용 하 여 가져오기 라이브러리의 콘텐츠를 볼 수 있습니다. 대/소문자를 구분 하지 않는 문자열 일치가 필요한 경우 CRT 문자열 함수 또는 Windows API 호출 중 하나를 사용 하도록 **__FUnloadDelayLoadedDLL2** 를 업데이트할 수 있습니다.

자세한 내용은 [Delay-Loaded DLL 언로드를](unloading-a-delay-loaded-dll.md) 참조 하세요.

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)

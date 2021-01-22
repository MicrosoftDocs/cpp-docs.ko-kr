---
description: '자세히 알아보기: 지연 로드 된 DLL의 명시적 언로드'
title: 지연 로드 된 DLL을 명시적으로 언로드
ms.date: 01/19/2021
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.openlocfilehash: b4e137f293c6497e234a7bb93bd16b5bb6887741
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666890"
---
# <a name="explicitly-unload-a-delay-loaded-dll"></a>지연 로드 된 DLL을 명시적으로 언로드

[`/delay:unload`](delay-delay-load-import-settings.md)링커 옵션을 사용 하면 코드에서 지연 로드 된 DLL을 명시적으로 언로드할 수 있습니다. 기본적으로 코드에서 DLL을 언로드할 때 지연 로드 된 가져오기는 IAT (가져오기 주소 테이블)에 남아 있습니다. 그러나 링커 명령줄에서를 사용 하는 경우 **`/delay:unload`** 도우미 함수는 호출을 통해 DLL의 명시적 언로드를 지원 `__FUnloadDelayLoadedDLL2` 하 고 IAT를 원래 형식으로 다시 설정 합니다. 지금은 잘못 된 포인터를 덮어씁니다. IAT는 [`ImgDelayDescr`](calling-conventions-parameters-and-return-type.md) 원래 iat의 복사본 주소 (있는 경우)가 포함 된 구조의 필드입니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```C
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

- `__FUnloadDelayLoadedDLL2`VC 디렉터리에서 파일의 함수 구현을 찾을 수 있습니다 *`delayhlp.cpp`* *`include`* .

- *`name`* 함수의 매개 변수는 `__FUnloadDelayLoadedDLL2` 가져오기 라이브러리에 포함 된 것과 정확히 일치 해야 합니다 (대/소문자 포함). 이 문자열은 이미지의 가져오기 테이블에도 있습니다. 를 사용 하 여 가져오기 라이브러리의 내용을 볼 수 있습니다 [`DUMPBIN /DEPENDENTS`](dependents.md) . 대/소문자를 구분 하지 않는 문자열 일치를 선호 하는 경우 `__FUnloadDelayLoadedDLL2` 대/소문자를 구분 하지 않는 CRT 문자열 함수 또는 WINDOWS API 호출 중 하나를 사용 하도록를 업데이트할 수 있습니다.

자세한 내용은 [지연 로드 된 DLL 언로드](unloading-a-delay-loaded-dll.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md)

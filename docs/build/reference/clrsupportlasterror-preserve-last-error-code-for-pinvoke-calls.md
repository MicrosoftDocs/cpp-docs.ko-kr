---
title: /CLRSUPPORTLASTERROR(PInvoke 호출의 마지막 오류 코드 유지)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: ccf13971bf77fb8e960b781e4a1aa2a0e06a5d61
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686105"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR(PInvoke 호출의 마지막 오류 코드 유지)

기본적으로 설정 된 **/CLRSUPPORTLASTERROR**는 P/Invoke 메커니즘을 통해 호출 된 함수의 마지막 오류 코드를 유지 합니다 .이를 통해 **/clr**로 컴파일된 코드에서 dll의 네이티브 함수를 호출할 수 있습니다.

## <a name="syntax"></a>구문

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>설명

마지막 오류 코드를 유지 하면 성능이 저하 되는 것을 의미 합니다.  마지막 오류 코드를 유지 하는 경우 성능에 영향을 주지 않으려면  **/CLRSUPPORTLASTERROR: NO**와 연결 합니다.

시스템 Dll의 함수에 대 한 마지막 오류 코드만 유지 하는 **/CLRSUPPORTLASTERROR: SYSTEMDLL**과 연결 하 여 성능 영향을 최소화할 수 있습니다.

> [!NOTE]
> 동일한 모듈에서 CLR 코드에 사용 되는 관리 되지 않는 함수에는 마지막 오류를 유지 하는 기능이 지원 되지 않습니다.

- 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](clr-common-language-runtime-compilation.md)를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="examples"></a>예제

다음 샘플에서는 마지막 오류를 수정 하는 하나의 내보낸 함수를 사용 하 여 네이티브 DLL을 정의 합니다.

```cpp
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

다음 샘플에서는 **/CLRSUPPORTLASTERROR**를 사용 하는 방법을 보여 주는 DLL을 사용 합니다.

```cpp
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>추가 정보

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

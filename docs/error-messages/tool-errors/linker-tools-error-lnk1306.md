---
description: '자세한 정보: 링커 도구 오류 LNK1306'
title: 링커 도구 오류 LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: aa6386da7c836eea8365d8a4ffde0bbd80d0fa81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193658"
---
# <a name="linker-tools-error-lnk1306"></a>링커 도구 오류 LNK1306

> DLL 진입점 함수를 관리할 수 없습니다. 네이티브로 컴파일

`DllMain` MSIL로 컴파일할 수 없습니다. 네이티브로 컴파일해야 합니다.

이 문제를 해결 하려면

- **/Clr** 을 사용 하지 않고 진입점을 포함 하는 파일을 컴파일합니다.

- 진입점을 섹션에 배치 `#pragma unmanaged` 합니다.

자세한 내용은 다음을 참조하세요.

- [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)

- [관리되는, 관리되지 않는](../../preprocessor/managed-unmanaged.md)

- [혼합 어셈블리 초기화](../../dotnet/initialization-of-mixed-assemblies.md)

- [DLL 및 Visual C++ 런타임 라이브러리 동작](../../build/run-time-library-behavior.md)

## <a name="example"></a>예제

다음 샘플에서는 LNK1306를 생성 합니다.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

이 문제를 해결 하려면 다음 예제와 같이/clr 옵션을 사용 하 여이 파일을 컴파일하거나, 지시문을 사용 `#pragma` 하 여 관리 되지 않는 섹션에 진입점 정의를 추가 합니다.

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```

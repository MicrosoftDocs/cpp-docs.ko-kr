---
description: '자세한 정보: 방법:/clr 컴파일 검색'
title: '방법: clr 컴파일 검색'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 25cd241a08f79bcae629c05fb3c7982a387120ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175718"
---
# <a name="how-to-detect-clr-compilation"></a>방법: /clr 컴파일 감지

`_MANAGED` `_M_CEE` 모듈이 **/clr** 로 컴파일되는지 여부를 확인 하려면 또는 매크로를 사용 합니다. 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

매크로에 대 한 자세한 내용은 [미리 정의 된 매크로](../preprocessor/predefined-macros.md)를 참조 하세요.

## <a name="example"></a>예제

```cpp
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

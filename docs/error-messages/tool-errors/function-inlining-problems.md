---
description: '자세한 정보: 함수 인라이닝 문제'
title: 함수 인라이닝 문제
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: 3c9c82c8b948acf7a64600c46fe87e17294fa844
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261738"
---
# <a name="function-inlining-problems"></a>함수 인라이닝 문제

함수 인라인 함수를 사용 하는 경우 다음을 수행 해야 합니다.

- 포함 하는 헤더 파일에 인라인 함수를 구현 합니다.

- 헤더 파일에서 인라인이 설정 되어 있어야 합니다.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

그리고

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

컴파일러 지시문을 사용 하는 경우 `#pragma inline_depth` 값이 2 이상으로 설정 되어 있는지 확인 합니다. 0 값은 인라이닝을 해제 합니다. 또한 **/Pv1** 또는 **/ob2** 컴파일러 옵션을 사용 하 고 있는지 확인 합니다.

여러 모듈에서 인라인 및 비 인라인 컴파일 옵션을 혼합 하면 문제가 발생할 수 있습니다. 함수 인라이닝을 on으로 설정 하 여 c + + 라이브러리를 만든 경우 ([/Ob1](../../build/reference/ob-inline-function-expansion.md) 또는 [/dev2](../../build/reference/ob-inline-function-expansion.md)) 함수를 설명 하는 해당 헤더 파일에 인라인 해제 (옵션 없음)가 설정 되어 있으면 오류가 발생 합니다. 함수는 헤더 파일의 코드에 인라인 되지 않지만 라이브러리 파일에 있지 않기 때문에 참조를 확인 하는 주소가 없습니다.

마찬가지로 함수 인라이닝을 사용 하는 프로젝트에서 헤더 파일 대신 .cpp 파일에 함수를 정의 하는 경우에도 LNK2019가 발생 합니다. 헤더 파일은 적절 하 게 간주 되는 모든 위치에 포함 되지만 .cpp 파일이 컴파일러를 통해 전달 될 때만 함수가 인라인 됩니다. 따라서 링커에서는 다른 모듈에서 사용 될 때 함수를 확인 되지 않은 외부 참조로 볼 수 있습니다.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

그런 다음

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

그런 다음

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>참고 항목

[링커 도구 오류 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)

---
description: '다음에 대 한 자세한 정보: include_alias pragma'
title: include_alias pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: 1a1855ce4c908c6678cfce7617c98aa671c57fac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236518"
---
# <a name="include_alias-pragma"></a>include_alias pragma

지시문에서 *alias_filename* 발견 되 면 `#include` 컴파일러는 대신 *actual_filename* 를 대체 하도록 지정 합니다.

## <a name="syntax"></a>Syntax

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)**\
> **#pragma include_alias (** \<*alias_filename*> **,** \<*actual_filename*> **)**

## <a name="remarks"></a>설명

**Include_alias** pragma 지시어를 사용 하 여 소스 파일에 포함 된 파일 이름에 대 한 이름이 나 경로가 다른 파일을 대체할 수 있습니다. 예를 들어 일부 파일 시스템은 8.3 FAT 파일 시스템 제한 보다 긴 헤더 파일 이름을 허용 합니다. 긴 헤더 파일 이름의 처음 8 개 문자가 고유 하지 않을 수 있으므로 컴파일러는 긴 이름을 8.3로 잘라낼 수 없습니다. 컴파일러가 지시문에서 *alias_filename* 문자열을 볼 때마다 `#include` 대신 이름 *actual_filename* 를 대체 합니다. 그런 다음 *actual_filename* 헤더 파일을 로드 합니다. 이 pragma는 해당 `#include` 지시문 앞에 배치되어야 합니다. 예를 들어:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

검색할 별칭이 사양과 정확히 일치 해야 합니다. Case, 철자 및 큰따옴표 또는 꺾쇠 괄호를 사용 하는 경우 모두 일치 해야 합니다. **Include_alias** pragma는 파일 이름에 대 한 단순 문자열 일치를 수행 합니다. 다른 파일 이름 유효성 검사는 수행 되지 않습니다. 예를 들어 다음과 같은 지시문에서는

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

헤더 파일 문자열이 정확 하 게 일치 하지 않으므로 별칭 대체가 수행 되지 않습니다. 또한 및 컴파일러 옵션에 대 한 인수로 사용 되는 헤더 파일 이름 `/Yu` `/Yc` 또는 `hdrstop` pragma는 대체 되지 않습니다. 예를 들어 소스 파일에 다음 지시문이 포함된 경우,

```cpp
#include <AppleSystemHeaderStop.h>
```

해당 컴파일러 옵션은 다음과 같이 됩니다.

> **/YcAppleSystemHeaderStop.h**

**Include_alias** pragma를 사용 하 여 모든 헤더 파일 이름을 다른 파일에 매핑할 수 있습니다. 예를 들어:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

큰따옴표로 묶인 파일 이름을 꺾쇠 괄호로 묶은 파일 이름과 혼합 하지 마세요. 예를 들어 위의 두 지시문이 지정 된 경우 `#pragma include_alias` 컴파일러는 다음 지시문을 대체 하지 않습니다 `#include` .

```cpp
#include <api.h>
#include "stdio.h"
```

또한 다음 지시문은 오류를 생성합니다.

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

오류 메시지에 보고 되는 파일 이름 또는 미리 정의 된 매크로의 값은 `__FILE__` 대체가 완료 된 후의 파일 이름입니다. 예를 들어 다음 지시문 뒤의 출력을 참조 하세요.

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

VERYLONGFILENAME에서 오류가 발생 했습니다 *. H* 는 다음과 같은 오류 메시지를 생성 합니다.

```Output
myfile.h(15) : error C2059 : syntax error
```

또한 전이성은 지원 되지 않습니다. 다음과 같은 지시문이 주어진 경우

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

컴파일러는 *세 개의 .h* 대신 *파일을* 검색 합니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

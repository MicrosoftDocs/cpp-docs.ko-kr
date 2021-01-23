---
description: pragmaMicrosoft C/c + +의 hdrstop 지시문에 대해 자세히 알아보세요.
title: hdrstop pragma
ms.date: 01/22/2021
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragma, hdrstop
no-loc:
- pragma
ms.openlocfilehash: caeaeb4a44182b6ba2edfa385a1504fde998cc43
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713612"
---
# <a name="hdrstop-no-locpragma"></a>`hdrstop` pragma

는 컴파일 상태가 저장 되는 위치에 대해 미리 컴파일 파일 이름에 대 한 더 많은 제어를 제공 합니다.

## <a name="syntax"></a>구문

> **`#pragma hdrstop`** [("*파일 이름*")]

## <a name="remarks"></a>설명

*Filename* 은 또는의 지정 여부에 따라 사용 하거나 만들 미리 컴파일된 헤더 파일의 이름입니다 [`/Yu`](../build/reference/yu-use-precompiled-header-file.md) [`/Yc`](../build/reference/yc-create-precompiled-header-file.md) . *Filename* 에 경로 사양이 없으면 미리 컴파일된 헤더 파일은 소스 파일과 동일한 디렉터리에 있는 것으로 간주 됩니다.

로 컴파일될 때 C 또는 c + + 파일에이 포함 되어 있으면 **`hdrstop`** pragma **`/Yc`** 컴파일러는 컴파일 상태를의 위치에 저장 합니다 pragma . 뒤에 오는 코드의 컴파일된 상태는 pragma 저장 되지 않습니다.

*Filename* 을 사용 하 여 컴파일된 상태가 저장 되는 미리 컴파일된 헤더 파일의 이름을 사용 합니다. **`hdrstop`** 과 *파일 이름* 사이의 공백은 선택 사항입니다. 에 지정 된 파일 이름은 **`hdrstop`** pragma 문자열이 며 모든 C 또는 c + + 문자열의 제약 조건이 적용 됩니다. 특히, 큰따옴표로 묶고 이스케이프 문자 (백슬래시, **`\`** )를 사용 하 여 디렉터리 이름을 지정 해야 합니다. 예:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

미리 컴파일된 헤더 파일의 이름은 다음 규칙에 따라 우선 순위대로 결정됩니다.

1. 컴파일러 옵션에 대 한 인수 **`/Fp`**

2. *파일 이름* 인수`#pragma hdrstop`

3. PCH 확장이 있는 소스 파일의 기본 이름입니다.

**`/Yc`** 및 **`/Yu`** 옵션 또는가 **`hdrstop`** pragma 파일 이름을 지정 하지 않으면 소스 파일의 기본 이름이 미리 컴파일된 헤더 파일의 기본 이름으로 사용 됩니다.

다음과 같이 전처리 명령을 사용하여 매크로 대체를 수행할 수도 있습니다.

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

다음 규칙은를 배치할 수 있는 위치를 제어 합니다 **`hdrstop`** pragma .

- hdrstop pragma가 데이터나 함수 선언 또는 정의 외부에 나타나야 합니다.

- hdrstop pragma가 헤더 파일 내부가 아닌 소스 파일에 지정되어야 합니다.

## <a name="example"></a>예제

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

이 예제에서는 **`hdrstop`** pragma 두 개의 파일이 포함 되 고 인라인 함수를 정의한 후에 표시 됩니다. 이 위치는 처음에에 대 한 홀수 배치 인 것 처럼 보일 수 있습니다 pragma . 그러나 수동 미리 컴파일 옵션 **`/Yc`** 및를 사용 하면 **`/Yu`** **`hdrstop`** pragma 전체 소스 파일 또는 인라인 코드를 미리 컴파일할 수 있습니다. Microsoft 컴파일러는 데이터 선언만 미리 컴파일하는 것으로 제한 하지 않습니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)

---
description: '자세한 정보: hdrstop pragma'
title: hdrstop pragma
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: 1fec99503adfb1d81f7da324db83e4c2b56a3912
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167515"
---
# <a name="hdrstop-pragma"></a>hdrstop pragma

는 컴파일 상태가 저장 되는 위치에 대해 미리 컴파일 파일 이름에 대 한 추가 제어를 제공 합니다.

## <a name="syntax"></a>Syntax

> **#pragma hdrstop** [("*파일 이름*")]

## <a name="remarks"></a>설명

*Filename* 은 [/yu](../build/reference/yu-use-precompiled-header-file.md) 또는 [/yc](../build/reference/yc-create-precompiled-header-file.md) 가 지정 되었는지에 따라 사용 하거나 만들 미리 컴파일된 헤더 파일의 이름입니다. *Filename* 에 경로 사양이 없으면 미리 컴파일된 헤더 파일은 소스 파일과 동일한 디렉터리에 있는 것으로 간주 됩니다.

로 컴파일될 때 C 또는 c + + 파일에 **hdrstop** pragma가 포함 되어 있으면 `/Yc` 컴파일러는 컴파일 상태를 pragma의 위치에 저장 합니다. Pragma 뒤에 오는 코드의 컴파일된 상태는 저장 되지 않습니다.

*Filename* 을 사용 하 여 컴파일된 상태가 저장 되는 미리 컴파일된 헤더 파일의 이름을 사용 합니다. **Hdrstop** 과 *filename* 사이의 공백은 선택 사항입니다. **Hdrstop** pragma에 지정 된 파일 이름은 문자열이 며 모든 C 또는 c + + 문자열의 제약 조건이 적용 됩니다. 특히, 이름을 따옴표로 묶고 이스케이프 문자(백슬래시)를 사용하여 디렉터리 이름을 지정해야 합니다. 예를 들어:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

미리 컴파일된 헤더 파일의 이름은 다음 규칙에 따라 우선 순위대로 결정됩니다.

1. 컴파일러 옵션에 대 한 인수 `/Fp`

2. *파일 이름* 인수`#pragma hdrstop`

3. 확장명이 .PCH인 소스 파일의 기본 이름

`/Yc`및 옵션의 경우 `/Yu` 두 컴파일 옵션과 **hdrstop** pragma가 모두 파일 이름을 지정 하지 않는 경우 소스 파일의 기본 이름이 미리 컴파일된 헤더 파일의 기본 이름으로 사용 됩니다.

다음과 같이 전처리 명령을 사용하여 매크로 대체를 수행할 수도 있습니다.

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

다음 규칙은 **hdrstop** pragma를 배치할 수 있는 위치를 제어 합니다.

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

이 예제에서 **hdrstop** pragma는 두 개의 파일이 포함 되 고 인라인 함수가 정의 된 후에 나타납니다. 처음에는이 위치가 pragma에 대 한 홀수 배치가 될 수 있습니다. 그러나 및를 사용 하 여 수동 미리 컴파일 옵션을 사용 하면 `/Yc` `/Yu` 인라인 코드  를 비롯 한 전체 소스 파일을 미리 컴파일할 수 있습니다. Microsoft 컴파일러는 데이터 선언만 미리 컴파일하도록 제한하지 않습니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

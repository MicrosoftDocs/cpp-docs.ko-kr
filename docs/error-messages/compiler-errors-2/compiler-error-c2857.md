---
description: '자세한 정보: 컴파일러 오류 C2857'
title: 컴파일러 오류 C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 85f2a9cffc8a96998a102d9e8219d9656cb3386f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337522"
---
# <a name="compiler-error-c2857"></a>컴파일러 오류 C2857

> /Yc *filename* 명령줄 옵션과 함께 지정한 ' #include ' 문이 소스 파일에 없습니다.

[/Yc](../../build/reference/yc-create-precompiled-header-file.md) 옵션은 컴파일되는 소스 파일에 포함 되지 않은 포함 파일의 이름을 지정 합니다.

## <a name="remarks"></a>설명

소스 파일에서 **/yc**<em>filename</em> 옵션을 사용 하 여 미리 컴파일된 헤더 (PCH) 파일을 만드는 경우 해당 원본 파일에는 파일 *이름* 헤더 파일이 포함 되어야 합니다. 지정 된 파일 *이름을* 포함 하 여 소스 파일에 포함 된 모든 파일은 PCH 파일에 포함 됩니다. **/Yu**<em>filename</em> 옵션을 사용 하 여 컴파일된 다른 소스 파일에서 PCH 파일을 사용 하는 경우 파일 *이름* 포함이 파일의 첫 번째 비 주석 줄 이어야 합니다. 이를 포함 하기 전에 컴파일러는 소스 파일에서 모든 항목을 무시 합니다.

이 오류는 `#include "filename"` PCH 소스 파일에서 컴파일되지 않은 조건부 컴파일 블록의 문에 의해 발생할 수 있습니다.

## <a name="example"></a>예제

일반적인 사용에서 프로젝트의 원본 파일 하나는 PCH 소스 파일로 지정 되 고 하나의 헤더 파일은 PCH 헤더 파일로 사용 됩니다. 일반적인 PCH 헤더 파일에는 프로젝트에 사용 되는 모든 라이브러리 헤더가 있지만 아직 개발 중인 로컬 헤더는 없습니다. 이 샘플에서 PCH 헤더 파일의 이름은 *my_pch. h* 입니다.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

PCH 소스 파일은 **/yc**<em>my_pch. h</em> 옵션을 사용 하 여 컴파일됩니다. 컴파일러가이 PCH 헤더 파일의 포함을 찾지 못하면 C2857을 생성 합니다.

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

이 PCH 파일을 사용 하려면 **/yu**<em>my_pch. h</em> 옵션을 사용 하 여 소스 파일을 컴파일해야 합니다. Pch 헤더 파일은 PCH를 사용 하는 소스 파일에 먼저 포함 되어야 합니다.

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```

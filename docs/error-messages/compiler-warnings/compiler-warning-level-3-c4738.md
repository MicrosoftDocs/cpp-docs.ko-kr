---
title: 컴파일러 경고(수준 3) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: 5162a03b213b35913ed1fc7f39360796ccf2c4a0
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189405"
---
# <a name="compiler-warning-level-3-c4738"></a>컴파일러 경고(수준 3) C4738

32비트 float 결과를 메모리에 저장하면 성능이 저하될 수 있습니다.

C4738는 할당, 캐스트, 전달 된 인수 또는 기타 작업의 결과를 반올림 하거나 작업에서 레지스터를 모두 실행 하 고 메모리를 사용 하는 데 필요한 (분산)를 경고 합니다. 이로 인해 성능이 저하 될 수 있습니다.

이 경고를 해결 하 고 반올림을 방지 하려면 [/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md) 로 컴파일하거나 `float`대신 `double`를 사용 합니다.

이 경고를 해결 하 고 레지스터의 실행을 방지 하려면 계산 순서를 변경 하 고 인라인 사용을 수정 합니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4738를 생성 합니다.

```cpp
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```
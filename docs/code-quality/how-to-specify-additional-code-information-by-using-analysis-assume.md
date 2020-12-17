---
description: _Analysis_assume_ 를 사용 하 여 추가 코드 정보를 지정 하는 방법에 대해 자세히 알아보세요.
title: 코드 분석 힌트에 _Analysis_assume_ 사용
ms.date: 12/16/2020
ms.topic: conceptual
f1_keywords:
- _Analysis_assume_
helpviewer_keywords:
- _Analysis_assume_
ms.openlocfilehash: f4244a896d4334cb6c5e857e63b39be0cd53b08b
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645126"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume_"></a>을 사용 하 여 추가 코드 정보를 지정 하는 방법 `_Analysis_assume_`

분석 프로세스에 도움이 되는 C/c + + 코드의 코드 분석 도구에 대 한 힌트를 제공 하 고 경고를 줄일 수 있습니다. 추가 정보를 제공 하려면 다음 함수 매크로를 사용 합니다.

`_Analysis_assume( expr )`

*`expr`* -true로 평가 되는 것으로 간주 되는 식입니다.

코드 분석 도구는 식이 나타내는 조건이 *`expr`* 함수가 표시 되는 지점에서 true 인 것으로 가정 합니다. 예를 들어 *`expr`* 변수에 대 한 할당 등이 변경 될 때까지 true로 유지 됩니다.

> [!NOTE]
> `_Analysis_assume_` 코드 최적화에 영향을 주지 않습니다. 코드 분석 도구 외부에서 `_Analysis_assume_` 는 no op로 정의 됩니다.

## <a name="example"></a>예

다음 코드에서는를 사용 하 여 `_Analysis_assume_` 코드 분석 경고 [C6388](../code-quality/c6388.md)을 수정 합니다.

```cpp
#include <windows.h>
#include <codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume_(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>참고 항목

- [__assume](../intrinsics/assume.md)

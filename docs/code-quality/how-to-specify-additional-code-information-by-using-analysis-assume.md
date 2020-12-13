---
description: '자세히 알아보기: 방법: _Analysis_assume 사용 하 여 추가 코드 정보 지정'
title: 코드 분석 힌트에 _Analysis_assume 사용
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
ms.openlocfilehash: 1960fae929f1bd0ffbac4979b76541fd0d396e42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151556"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>방법: _Analysis_assume를 사용 하 여 추가 코드 정보 지정

분석 프로세스에 도움이 되는 C/c + + 코드의 코드 분석 도구에 대 한 힌트를 제공 하 고 경고를 줄일 수 있습니다. 추가 정보를 제공 하려면 다음 함수를 사용 합니다.

`_Analysis_assume(`  `expr`  `)`

`expr` -true로 평가 되는 것으로 간주 되는 식입니다.

코드 분석 도구는 함수가 표시 되는 지점에서 식이 나타내는 조건이 true 인 것으로 가정 합니다. 예를 들어 변수에 대 한 할당을 통해 식이 변경 될 때까지 true로 유지 됩니다.

> [!NOTE]
> `_Analysis_assume` 코드 최적화에 영향을 주지 않습니다. 코드 분석 도구 외부에서 `_Analysis_assume` 는 no op로 정의 됩니다.

## <a name="example"></a>예제

다음 코드에서는를 사용 하 여 `_Analysis_assume` 코드 분석 경고 [C6388](../code-quality/c6388.md)을 수정 합니다.

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>참고 항목

- [__assume](../intrinsics/assume.md)

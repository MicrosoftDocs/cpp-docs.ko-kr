---
description: '자세한 정보: pragma optimize'
title: 최적화 pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 9c7f07e44a31144c469bb13c936bc16d5fda39df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333210"
---
# <a name="optimize-pragma"></a>최적화 pragma

함수 별로 최적화를 지정 합니다.

## <a name="syntax"></a>Syntax

> **#pragma optimize ("** [ *최적화-목록* ] **",** { **on**  |  **off** } **)**

## <a name="remarks"></a>설명

**Optimize** pragma는 함수 외부에 표시 되어야 합니다. Pragma가 표시 된 후에 정의 된 첫 번째 함수에 적용 됩니다. **On** 및 **off** 인수는 *최적화 목록* 에 지정 된 옵션을 on 또는 off로 설정 합니다.

*최적화 목록은* 다음 표에 표시 된 0 개 이상의 매개 변수를 사용할 수 있습니다.

### <a name="parameters-of-the-optimize-pragma"></a>optimize Pragma의 매개 변수

| 매개 변수 | 최적화 형식 |
|--------------------|--------------------------|
| **g** | 전역 최적화를 활성화합니다. |
| **s** 또는 **t** | 짧거나 빠른 기계어 코드 시퀀스를 지정합니다. |
| **y** | 프로그램 스택에서 프레임 포인터를 생성합니다. |

이러한 매개 변수는 [/o](../build/reference/o-options-optimize-code.md) 컴파일러 옵션과 함께 사용 되는 동일한 문자입니다. 예를 들어 다음 pragma는 `/Os` 컴파일러 옵션과 동일합니다.

```cpp
#pragma optimize( "s", on )
```

**Optimize** pragma를 빈 문자열 (**""**)과 함께 사용 하는 것은 특별 한 형태의 지시문입니다.

**Off** 매개 변수를 사용 하는 경우 모든 최적화, **g**, **s**, **t** 및 **y** 가 해제 됩니다.

On 매개 변수를 사용 하는 경우 **에** 는 [/o](../build/reference/o-options-optimize-code.md) 컴파일러 옵션을 사용 하 여 지정한 대로 최적화를 다시 설정 합니다.

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

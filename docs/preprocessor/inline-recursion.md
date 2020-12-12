---
description: '다음에 대 한 자세한 정보: inline_recursion pragma'
title: inline_recursion pragma
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 1688eb724a9a76ce3f173c7f9eac7d52032fbe13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236375"
---
# <a name="inline_recursion-pragma"></a>inline_recursion pragma

직접 또는 상호 재귀 함수 호출의 인라인 확장을 제어합니다.

## <a name="syntax"></a>Syntax

> **#pragma inline_recursion (** [{ **on**  |  **off** }] **)**

## <a name="remarks"></a>설명

이 pragma를 사용 하 여 [인라인으로](../cpp/inline-functions-cpp.md) 표시 된 함수와 컴파일러에서 자동으로 확장 하는 함수를 [__inline](../cpp/inline-functions-cpp.md) 하거나 함수를 제어 `/Ob2` 합니다. 이 pragma를 사용 하려면 [/Ob](../build/reference/ob-inline-function-expansion.md) 컴파일러 옵션을 1 또는 2로 설정 해야 합니다. **Inline_recursion** 의 기본 상태는 off입니다. 이 pragma는 pragma가 표시 된 후 첫 번째 함수 호출에서 적용 되며 함수 정의에는 영향을 주지 않습니다.

**Inline_recursion** pragma는 재귀 함수를 확장 하는 방법을 제어 합니다. **Inline_recursion** 해제 되어 있고 인라인 함수에서 직접 또는 간접적으로 자신을 호출 하는 경우 함수는 한 번만 확장 됩니다. **Inline_recursion** on 이면 함수가 [inline_depth](../preprocessor/inline-depth.md) pragma를 사용 하 여 설정 된 값에 도달할 때까지 여러 번 확장 되거나, pragma에 의해 정의 된 재귀 함수의 기본값 또는 용량 제한에 도달할 때까지 여러 번 확장 됩니다 `inline_depth` .

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (인라인 함수 확장)](../build/reference/ob-inline-function-expansion.md)

---
description: '다음에 대 한 자세한 정보: inline_depth pragma'
title: inline_depth pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 10ac7f5543108018eb7b51e8916dfed149363899
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236401"
---
# <a name="inline_depth-pragma"></a>inline_depth pragma

인라인 추론 검색 깊이를 지정 합니다. 호출 그래프에서 지정 된 값 보다 큰 깊이의 함수는 인라인되지 않습니다.

## <a name="syntax"></a>Syntax

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>설명

이 pragma는 [inline](../cpp/inline-functions-cpp.md) 및 [__inline](../cpp/inline-functions-cpp.md)로 표시 된 함수의 인라인을 제어 하거나 옵션 아래에서 자동으로 인라인 처리 합니다 `/Ob` .

*n* 은 0에서 255 사이의 값이 될 수 있습니다. 여기서 255은 호출 그래프에서 무제한 깊이를 의미 합니다. 0 값은 인라인 확장을 금지 합니다. *N* 을 지정 하지 않으면 기본값 254이 사용 됩니다.

**Inline_depth** pragma는 일련의 함수 호출이 확장 될 수 있는 횟수를 제어 합니다. 예를 들어 인라인 깊이가 4 인 것으로 가정 합니다. A가 B를 호출 하 고 B가 C를 호출 하는 경우 세 호출은 모두 인라인으로 확장 됩니다. 그러나 가장 가까운 인라인 수준 확장이 2 인 경우 A와 B만 확장 되 고 C는 함수 호출로 유지 됩니다.

이 pragma를 사용 하려면 `/Ob` 컴파일러 옵션을 1 이상으로 설정 해야 합니다. 이 pragma를 사용하여 설정한 깊이는 pragma 뒤에 오는 첫 번째 함수 호출에 적용됩니다.

인라인 깊이는 확장 하는 동안 감소할 수 있지만 증가 되지는 않습니다. 인라인 깊이가 6이 고 확장 하는 동안 전처리기는 값이 8 인 **inline_depth** pragma를 발견 하면 깊이는 6으로 유지 됩니다.

**Inline_depth** pragma는로 표시 된 함수에는 영향을 주지 않습니다 **`__forceinline`** .

> [!NOTE]
> 재귀 함수는 최대 16 깊이의 호출까지 인라인을 대체할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)

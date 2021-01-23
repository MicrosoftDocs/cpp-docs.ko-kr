---
description: pragmaMicrosoft C/c + +의 loop 지시문에 대해 자세히 알아보세요.
title: 실행 pragma
ms.date: 01/22/2021
f1_keywords:
- loop_CPP
- vc-pragma.loop
helpviewer_keywords:
- loop pragma
- pragma, loop
no-loc:
- pragma
ms.openlocfilehash: 4aac76cb5220e57dd378ac00ff576521c9001218
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713534"
---
# <a name="loop-no-locpragma"></a>`loop` pragma

자동 평행 화 도우미에서 루프 코드를 고려 하는 방법을 제어 하거나 자동 벡터화의 고려 사항에서 루프를 제외 합니다.

## <a name="syntax"></a>구문

> **`#pragma loop( hint_parallel(`***n***`) )`**\
> **`#pragma loop( no_vector )`**\
> **`#pragma loop( ivdep )`**

### <a name="parameters"></a>매개 변수

**`hint_parallel(`***n***`)`**\
*N* 개 스레드 간에이 루프가 병렬화 되어야 하는 컴파일러에 대 한 힌트입니다. 여기서 *n* 은 양의 정수 리터럴 또는 0입니다. *N* 이 0 이면 런타임에 최대 스레드 수가 사용 됩니다. 이는 명령이 아니라 컴파일러에 대 한 힌트입니다. 루프의 병렬 처리를 보장할 수 없습니다. 루프에 데이터 종속성 또는 구조적 문제가 있으면 병렬 처리 되지 않습니다. 예를 들어 루프 본문을 벗어나는 스칼라에를 저장 하는 경우에는 병렬화 되지 않습니다.

컴파일러 스위치를 지정 하지 않으면 컴파일러는이 옵션을 무시 [`/Qpar`](../build/reference/qpar-auto-parallelizer.md) 합니다.

**`no_vector`**\
기본적으로 자동 벡터화는 평가 하는 모든 루프를 벡터화 시도 합니다. 다음을 지정 pragma 하 여 뒤에 오는 루프의 자동 벡터화를 사용 하지 않도록 설정 합니다.

**`ivdep`**\
이 루프의 벡터 종속성을 무시 하는 컴파일러에 대 한 힌트입니다.

## <a name="remarks"></a>설명

를 사용 하려면 **`loop`** pragma 루프 정의가 아닌 바로 앞에 놓습니다. 는 pragma 뒤에 오는 루프의 범위에 적용 됩니다. pragma루프에는 순서에 관계 없이 여러 지시문을 적용할 수 있지만 각 지시문은 별도의 문에 하나씩 표시 해야 합니다 pragma .

## <a name="see-also"></a>참고 항목

[자동 병렬화 및 자동 벡터화](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)

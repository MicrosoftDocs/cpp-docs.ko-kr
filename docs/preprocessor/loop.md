---
description: '자세한 정보: loop pragma'
title: loop pragma
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: b54d62a6c9a29a4688453992ad9647d9bc21afd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167463"
---
# <a name="loop-pragma"></a>loop pragma

자동 평행 화 도우미에서 루프 코드를 고려 하는 방법을 제어 하거나 자동 벡터화의 고려 사항에서 루프를 제외 합니다.

## <a name="syntax"></a>Syntax

> **#pragma 루프 (hint_parallel (** *n* **))**\
> **#pragma 루프 (no_vector)**\
> **#pragma 루프 (ivdep)**

### <a name="parameters"></a>매개 변수

**hint_parallel (** *n* **)**\
*N* 개 스레드 간에이 루프가 병렬화 되어야 하는 컴파일러에 대 한 힌트입니다. 여기서 *n* 은 양의 정수 리터럴 또는 0입니다. *N* 이 0 이면 런타임에 최대 스레드 수가 사용 됩니다. 이는 명령이 아니라 컴파일러에 대 한 힌트입니다. 루프의 병렬 처리를 보장할 수 없습니다. 루프에 데이터 종속성 또는 구조적 문제가 있으면 병렬 처리 되지 않습니다. 예를 들어 루프 본문을 벗어나는 스칼라에를 저장 하는 경우에는 병렬화 되지 않습니다.

[/Qp컴파일러](../build/reference/qpar-auto-parallelizer.md) 스위치를 지정 하지 않으면 컴파일러는이 옵션을 무시 합니다.

**no_vector**\
기본적으로 자동 벡터화는 평가 하는 모든 루프를 벡터화 시도 합니다. 다음 루프에 대 한 자동 벡터화를 사용 하지 않도록 설정 하려면이 pragma를 지정 합니다.

**ivdep**\
이 루프의 벡터 종속성을 무시 하는 컴파일러에 대 한 힌트입니다.

## <a name="remarks"></a>설명

**Loop** pragma를 사용 하려면 루프 정의가 아닌 바로 앞에 놓습니다. 그러면 pragma가 뒤에 오는 루프의 범위에 적용됩니다. 순서에 상관없이 루프에 여러 pragma를 적용할 수 있지만 각 pragma를 별도의 pragma 문에 지정해야 합니다.

## <a name="see-also"></a>참고 항목

[자동 병렬화 및 자동 벡터화](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

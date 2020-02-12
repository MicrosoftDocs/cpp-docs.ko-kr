---
title: '방법: 취소를 사용하여 병렬 루프 중단'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142141"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>방법: 취소를 사용하여 병렬 루프 중단

이 예제에서는 취소를 사용하여 기본적인 병렬 검색 알고리즘을 구현하는 방법을 보여 줍니다.

## <a name="example"></a>예제

다음 예제에서는 취소를 사용하여 배열에서 요소를 검색합니다. `parallel_find_any` 함수는 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘과 [concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) 함수를 사용 하 여 지정 된 값이 포함 된 위치를 검색 합니다. 병렬 루프에서 값을 찾으면 [concurrency:: cancellation_token_source:: cancel](reference/cancellation-token-source-class.md#cancel) 메서드를 호출 하 여 이후 작업을 취소 합니다.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘은 동시에 작동 합니다. 따라서 미리 결정된 순서대로 작업을 수행하지 않습니다. 지정된 값의 인스턴스가 배열에 여러 개 포함되어 있으면 결과는 해당 위치 중 하나가 될 수 있습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나, `parallel-array-search.cpp` 이름이 지정 된 파일에 붙여 넣은 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-array-search**

## <a name="see-also"></a>참고 항목

[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 클래스](../../parallel/concrt/reference/cancellation-token-source-class.md)

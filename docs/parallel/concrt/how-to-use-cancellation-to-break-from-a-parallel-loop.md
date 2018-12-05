---
title: '방법: 취소를 사용하여 병렬 루프 중단'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 2a19c2874ce331be2d4f5840f61cabf7bca9abf6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612747"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>방법: 취소를 사용하여 병렬 루프 중단

이 예제에서는 취소를 사용하여 기본적인 병렬 검색 알고리즘을 구현하는 방법을 보여 줍니다.

## <a name="example"></a>예제

다음 예제에서는 취소를 사용하여 배열에서 요소를 검색합니다. `parallel_find_any` 함수는 [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘과 [run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) 함수를 사용하여 지정된 값을 포함하는 위치를 검색합니다. 병렬 루프에서 값을 찾았을 때,  [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) 메소드를 호출하여 이후의 작업을 취소합니다.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘은 동시에 동작합니다. 따라서 미리 결정된 순서대로 작업을 수행하지 않습니다. 지정된 값의 인스턴스가 배열에 여러 개 포함되어 있으면 결과는 해당 위치 중 하나가 될 수 있습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사하여 Visual Studio 프로젝트 또는 `parallel-array-search.cpp` 파일에 붙여넣고 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행합니다.

**cl.exe /EHsc parallel-array-search.cpp**

## <a name="see-also"></a>참고 항목

[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source 클래스](../../parallel/concrt/reference/cancellation-token-source-class.md)

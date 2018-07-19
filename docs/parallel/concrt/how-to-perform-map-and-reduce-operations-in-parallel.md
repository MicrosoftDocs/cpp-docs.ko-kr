---
title: '방법: 매핑 수행 및 병렬 작업 줄이기 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cda761da013e966f91848fed01a4f96f5d373021
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685930"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>방법: 매핑 수행 및 병렬 작업 줄이기

사용 하는 방법을 보여 주는이 예제는 [concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) 및 [concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) 알고리즘 및 [concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)파일에서 단어가 나타나는 횟수를 계산 하는 클래스입니다.  
  
 A *지도* 작업 시퀀스의 각 값에 함수를 적용 합니다. A *줄일* 작업 하나의 값으로 시퀀스의 요소를 결합 합니다. C + + 표준 라이브러리를 사용할 수 [std:: transform](../../standard-library/algorithm-functions.md#transform) 및 [std:: accumulate](../../standard-library/numeric-functions.md#accumulate) 매핑 수행 및 줄이기 작업을 하는 함수입니다. 그러나 많은 문제에 대해 성능을 향상시키기 위해 `parallel_transform` 알고리즘을 사용하여 매핑 작업을 병렬로 수행하고, `parallel_reduce` 알고리즘을 사용하여 줄이기 작업을 병렬로 수행할 수 있습니다. 경우에 따라 `concurrent_unordered_map`을 사용하여 매핑과 줄이기를 하나의 작업으로 수행할 수도 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 파일에서 단어가 나타나는 횟수를 계산합니다. 사용 하 여 [std:: vector](../../standard-library/vector-class.md) 두 파일의 콘텐츠를 나타내는입니다. 매핑 작업은 각 벡터에서 각 단어가 나타나는 횟수를 계산합니다. 줄이기 작업은 두 벡터의 단어 개수를 누적합니다.  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 코드를 컴파일하려면 코드를 복사 하 고 다음 Visual Studio 프로젝트에 붙여 하거나 라는 파일에 붙여 `parallel-map-reduce.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.  
  
 **cl.exe /EHsc 병렬-맵-reduce.cpp**  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 이 예제에서는 concurrent_unordered_map.h에서 정의된 `concurrent_unordered_map` 클래스를 사용하여 매핑과 줄이기를 하나의 작업으로 수행할 수 있습니다.  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 일반적으로 외부 또는 내부 루프만 평행화합니다. 비교적 적은 파일이 있고 각 파일이 많은 단어를 포함하는 경우 내부 루프를 평행화합니다. 비교적 많은 파일이 있고 각 파일이 적은 단어를 포함하는 경우 외부 루프를 평행화합니다.  
  
## <a name="see-also"></a>참고 항목  
 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform 함수](reference/concurrency-namespace-functions.md#parallel_transform)   
 [parallel_reduce 함수](reference/concurrency-namespace-functions.md#parallel_reduce)   
 [concurrent_unordered_map 클래스](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

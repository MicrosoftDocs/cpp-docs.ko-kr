---
title: '방법: 병렬 컨테이너를 사용 하 여 효율성을 높이기 위해 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0e0d79693bef358a582e878ec2d6d138387752c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696203"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>방법: 병렬 컨테이너를 사용하여 효율성 향상
이 항목에서는 효율적으로 저장 하 고 데이터를 병렬로 액세스할 병렬 컨테이너를 사용 하는 방법을 보여 줍니다.  
  
 예제 코드 소수와 병렬로 카마이클 수의 집합을 계산 합니다. 그런 다음 각 카마이클 번호에 대 한 코드는 수의 소수를 계산 합니다.  
  
## <a name="example"></a>예제  
 다음 예제와 `is_prime` 입력된 값이 소수 인지를 결정 하는 함수 및 `is_carmichael` 입력된 값이 카마이클 수 있는지 여부를 결정 하는 함수입니다.  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## <a name="example"></a>예제  
 다음 예제에서는 `is_prime` 및 `is_carmichael` 소수와 카마이클 수의 집합을 계산 하는 함수입니다. 이 예제에서는 사용은 [concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 및 [concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) 동시에 각 계산 하는 알고리즘을 설정 합니다. 병렬 알고리즘에 대 한 자세한 내용은 참조 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)합니다.  
  
 사용 하 여이 예제는 [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 카마이클 집합을 보유 하는 개체 번호 작업 큐로 해당 개체를 나중에 사용 됩니다. 사용 하 여 한 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 것가 나중에 반복이 소수를 찾으려고 집합 때문에 소수 집합을 보유 하는 개체입니다.  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## <a name="example"></a>예제  
 다음 예제와 `prime_factors_of` 평가판 나누기를 사용 하 여 지정된 된 값의 모든 주요 요소를 검색 하는 함수입니다.  
  
 이 함수는 사용 된 [concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 소수의 컬렉션을 반복 하는 알고리즘입니다. `concurrent_vector` 개체 병렬 루프를 동시에 결과에 소수를 추가할 수 있습니다.  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## <a name="example"></a>예제  
 이 예제에서는 카마이클 수의 큐에 있는 각 요소를 호출 하 여 처리는 `prime_factors_of` 해당 주요 요소를 계산 하는 함수입니다. 동시에이 작업을 수행 하는 작업 그룹을 사용 합니다. 작업 그룹에 대 한 자세한 내용은 참조 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)합니다.  
  
 이 예제는 해당 개수에 최대 4 개의 주요 요인을 각 카마이클 번호에 대 한 주요 요소를 출력 합니다.  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## <a name="example"></a>예제  
 다음 코드에서는 병렬 컨테이너를 사용 하 여 카마이클 숫자의 소수를 계산 하는 전체 예제를 보여 줍니다.  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 이 예제는 다음과 같은 샘플 출력을 생성합니다.  
  
```Output  
Prime factors of 9890881 are: 7 11 13 41 241.  
Prime factors of 825265 are: 5 7 17 19 73.  
Prime factors of 1050985 are: 5 13 19 23 37.  
```  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 예제 코드를 복사 하 고 Visual Studio 프로젝트에 붙여 넣거나 라는 파일에 붙여 `carmichael-primes.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.  
  
 **cl.exe /EHsc 카마이클 primes.cpp**  
  
## <a name="see-also"></a>참고 항목  
 [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)   
 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent_vector 클래스](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent_queue 클래스](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel_invoke 함수](reference/concurrency-namespace-functions.md#parallel_invoke)   
 [parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)   
 [task_group 클래스](reference/task-group-class.md)

---
description: '자세히 알아보기: 방법: Alloc 및 Free를 사용 하 여 메모리 성능 개선'
title: '방법: Alloc 및 Free를 사용하여 메모리 성능 개선'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: ab9a7bb9ad067bd7a5650b9e66d1708f08ffc183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172572"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>방법: Alloc 및 Free를 사용하여 메모리 성능 개선

이 문서에서는 [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) 및 [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) 함수를 사용 하 여 메모리 성능을 향상 시키는 방법을 보여 줍니다. 각각 및 연산자를 지정 하는 세 가지 서로 다른 형식에 대해 배열의 요소를 병렬 처리 하는 데 필요한 시간을 비교 합니다 `new` `delete` .

`Alloc`및 `Free` 함수는 여러 스레드가 및를 모두 자주 호출 하는 경우에 가장 유용 합니다 `Alloc` `Free` . 런타임은 각 스레드에 대해 별도의 메모리 캐시를 보유 합니다. 따라서 런타임은 잠금이나 메모리 장벽을 사용 하지 않고 메모리를 관리 합니다.

## <a name="example-types-that-specify-new-and-delete-operators"></a>예: new 및 delete 연산자를 지정 하는 형식

다음 예제에서는 각각 및 연산자를 지정 하는 세 가지 형식을 보여 줍니다 `new` `delete` . 클래스는 `new_delete` 전역 `new` 및 연산자를 사용 하 고 `delete` , `malloc_free` 클래스는 C 런타임 [malloc](../../c-runtime-library/reference/malloc.md) 및 [free](../../c-runtime-library/reference/free.md) 함수를 사용 하며, `Alloc_Free` 클래스는 동시성 런타임 `Alloc` 및 함수를 사용 합니다 `Free` .

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example-swap-and-reverse_array-functions"></a>예: 함수 바꾸기 및 reverse_array

다음 예제에서는 `swap` 및 `reverse_array` 함수를 보여 줍니다. `swap`함수는 지정 된 인덱스에 있는 배열의 내용을 교환 합니다. 임시 변수에 대해 힙에서 메모리를 할당 합니다. `reverse_array`함수는 많은 배열을 만들고이 배열을 병렬로 여러 번 되돌리는 데 필요한 시간을 계산 합니다.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example-wmain-function"></a>예: wmain 함수

다음 예제에서는 `wmain` 함수가, 및 형식에서 작동 하는 데 필요한 시간을 계산 하는 함수를 보여 줍니다 `reverse_array` `new_delete` . 각 함수는 `malloc_free` `Alloc_Free` 서로 다른 메모리 할당 체계를 사용 합니다.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="complete-code-example"></a>전체 코드 예제

전체 예제는 다음과 같습니다.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

이 예제에서는 4 개의 프로세서가 있는 컴퓨터에 대 한 다음 샘플 출력을 생성 합니다.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

이 예제에서 및 함수를 사용 하는 `Alloc` 형식은 `Free` `Alloc` `Free` 여러 스레드의 메모리 블록을 자주 할당 하 고 해제 하기 위해 및 함수를 최적화 하기 때문에 최상의 메모리 성능을 제공 합니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `allocators.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc 할당자.**

## <a name="see-also"></a>참고 항목

[메모리 관리 함수](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc 함수](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 함수](reference/concurrency-namespace-functions.md#free)

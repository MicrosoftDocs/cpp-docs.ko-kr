---
description: Tile_static 키워드에 대해 자세히 알아보세요.
title: tile_static 키워드
ms.date: 11/04/2016
f1_keywords:
- tile_static_CPP
helpviewer_keywords:
- tile_static keyword
ms.assetid: d78384d4-65d9-45cf-b3df-7e904f489d06
ms.openlocfilehash: c719ab61fd6247800b7e1b6b8ac1a58dd51c6ac5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151413"
---
# <a name="tile_static-keyword"></a>tile_static 키워드

**Tile_static** 키워드는 스레드 타일의 모든 스레드가 액세스할 수 있는 변수를 선언 하는 데 사용 됩니다. 변수의 수명은 실행이 선언 지점에 도달할 때 시작되고 커널 함수가 반환될 때 종료됩니다. 타일 사용에 대 한 자세한 내용은 [타일 사용](../parallel/amp/using-tiles.md)을 참조 하세요.

**Tile_static** 키워드에는 다음과 같은 제한 사항이 있습니다.

- `restrict(amp)` 한정자가 있는 함수 내의 변수에만 사용할 수 있습니다.

- 포인터 또는 참조 형식인 변수에 사용할 수 없습니다.

- **Tile_static** 변수에는 이니셜라이저가 있을 수 없습니다. 기본 생성자 및 소멸자가 자동으로 호출되지 않습니다.

- 초기화 되지 않은 **tile_static** 변수의 값이 정의 되지 않았습니다.

- 에 대 한 비 바둑판식 호출을 기반으로 하는 호출 그래프에 **tile_static** 변수가 선언 된 경우 `parallel_for_each` 경고가 생성 되 고 변수의 동작이 정의 되지 않습니다.

## <a name="example"></a>예제

다음 예제에서는 **tile_static** 변수를 사용 하 여 타일의 여러 스레드 간에 데이터를 누적 하는 방법을 보여 줍니다.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
// Sample data.
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles are:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages.
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.grid and divide the grid into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output.
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="see-also"></a>참고 항목

[Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)<br/>
[C++ AMP 개요](../parallel/amp/cpp-amp-overview.md)<br/>
[parallel_for_each 함수(C++ AMP)](../parallel/amp/reference/concurrency-namespace-functions-amp.md#parallel_for_each)<br/>
[연습: 행렬 곱하기](../parallel/amp/walkthrough-matrix-multiplication.md)

---
title: 타일 사용
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: 6c935134e033d12fc140c8d377ef59d0b47265fc
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518259"
---
# <a name="using-tiles"></a>타일 사용

바둑판식 배열을 사용 하 여 앱의 가속을 최대화할 수 있습니다. 바둑판식 배열은 스레드를 동일한 사각형 하위 집합 또는 *타일로*나눕니다. 적절 한 타일 크기와 바둑판식 알고리즘을 사용 하는 경우 C++ AMP 코드에서 훨씬 더 많은 가속을 얻을 수 있습니다. 바둑판식 배열의 기본 구성 요소는 다음과 같습니다.

- 변수를 `tile_static` 합니다. 바둑판식 배열의 주요 이점은 `tile_static` 액세스의 성능 향상입니다. `tile_static` 메모리의 데이터에 대 한 액세스는 전역 공간의 데이터에 액세스 하는 것 보다 훨씬 빠를 수 있습니다 (`array` 또는 `array_view` 개체). 각 타일에 대해 `tile_static` 변수의 인스턴스가 만들어지고, 타일의 모든 스레드는 변수에 액세스할 수 있습니다. 일반적인 바둑판식 알고리즘에서 데이터는 전역 메모리에서 한 번 `tile_static` 메모리에 복사 된 다음 `tile_static` 메모리에서 여러 번 액세스 됩니다.

- [tile_barrier:: Wait 메서드](reference/tile-barrier-class.md#wait) `tile_barrier::wait`에 대 한 호출은 동일한 타일의 모든 스레드가 `tile_barrier::wait`호출에 도달할 때까지 현재 스레드의 실행을 일시 중단 합니다. 스레드가 실행 되는 순서를 보장할 수 없습니다. 모든 스레드가 호출에 도달할 때까지 `tile_barrier::wait`에 대 한 호출을 넘어 타일의 스레드가 실행 되지 않습니다. 즉, `tile_barrier::wait` 방법을 사용 하면 스레드 단위로 작업을 수행 하는 것이 아니라 타일 단위로 작업을 수행할 수 있습니다. 일반적인 바둑판식 배열 알고리즘에는 전체 타일에 대 한 `tile_static` 메모리를 초기화 하 고 `tile_barrer::wait`를 호출 하는 코드가 있습니다. `tile_barrier::wait` 뒤에 나오는 코드는 모든 `tile_static` 값에 액세스 해야 하는 계산을 포함 합니다.

- 로컬 및 전역 인덱싱. 전체 `array_view` 또는 `array` 개체를 기준으로 하는 스레드 인덱스와 타일을 기준으로 하는 인덱스에 대 한 액세스 권한이 있습니다. 로컬 인덱스를 사용 하면 코드를 더 쉽게 읽고 디버그할 수 있습니다. 일반적으로 로컬 인덱싱을 사용 하 여 `tile_static` 변수에 액세스 하 고 전역 인덱싱을 사용 하 여 `array` 및 `array_view` 변수에 액세스 합니다.

- [클래스](../../parallel/amp/reference/tiled-extent-class.md) 및 [tiled_index 클래스](../../parallel/amp/reference/tiled-index-class.md)를 tiled_extent 합니다. `parallel_for_each` 호출에서 `extent` 개체 대신 `tiled_extent` 개체를 사용 합니다. `parallel_for_each` 호출에서 `index` 개체 대신 `tiled_index` 개체를 사용 합니다.

바둑판식 배열을 활용 하려면 알고리즘에서 계산 도메인을 타일로 분할 한 다음 더 빠른 액세스를 위해 타일 데이터를 `tile_static` 변수에 복사 해야 합니다.

## <a name="example-of-global-tile-and-local-indices"></a>전역, 타일 및 로컬 인덱스의 예

다음 다이어그램은 2x3 타일에 정렬 된 데이터의 8x9 매트릭스를 나타냅니다.

![8&#45;x&#45;9 행렬을 2&#45;x&#45;3 타일로 나눕니다.](../../parallel/amp/media/usingtilesmatrix.png "8&#45;x&#45;9 행렬을 2&#45;x&#45;3 타일로 나눕니다.")

다음 예에서는이 바둑판식 행렬의 전역, 타일 및 로컬 인덱스를 표시 합니다. `Description`형식의 요소를 사용 하 여 `array_view` 개체를 만듭니다. `Description`은 행렬의 요소에 대 한 전역, 타일 및 로컬 인덱스를 포함 합니다. `parallel_for_each` 호출의 코드는 각 요소의 전역, 타일 및 로컬 인덱스 값을 설정 합니다. 출력은 `Description` 구조체의 값을 표시 합니다.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

예제의 주요 작업은 `array_view` 개체의 정의 및 `parallel_for_each`에 대 한 호출입니다.

1. `Description` 구조체의 벡터가 8x9 `array_view` 개체로 복사 됩니다.

2. `parallel_for_each` 메서드는 계산 도메인으로 `tiled_extent` 개체를 사용 하 여 호출 됩니다. `tiled_extent` 개체는 `descriptions` 변수의 `extent::tile()` 메서드를 호출 하 여 만듭니다. `<2,3>``extent::tile()`에 대 한 호출의 형식 매개 변수는 2x3 타일이 만들어지도록 지정 합니다. 따라서 8x9 매트릭스는 12 개의 타일, 4 개의 행 및 3 개의 열에 바둑판식으로 배열 됩니다.

3. `parallel_for_each` 메서드는 인덱스로 `tiled_index<2,3>` 개체 (`t_idx`)를 사용 하 여 호출 됩니다. 인덱스의 형식 매개 변수 (`t_idx`)는 계산 도메인 (`descriptions.extent.tile< 2, 3>()`)의 형식 매개 변수와 일치 해야 합니다.

4. 각 스레드가 실행 될 때 인덱스 `t_idx`는 스레드가 있는 타일 (`tiled_index::tile` 속성)과 타일 내에서의 스레드 위치 (`tiled_index::local` 속성)에 대 한 정보를 반환 합니다.

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>타일 동기화-tile_static 및 tile_barrier:: wait

이전 예제에서는 타일 레이아웃과 인덱스를 보여 주지만 매우 유용 합니다.  타일은 알고리즘에 대 한 정수를 `tile_static` 변수를 활용 하는 경우에 유용 합니다. 타일의 모든 스레드가 `tile_static` 변수에 액세스할 수 있으므로 `tile_barrier::wait`에 대 한 호출은 `tile_static` 변수에 대 한 액세스를 동기화 하는 데 사용 됩니다. 타일의 모든 스레드가 `tile_static` 변수에 액세스할 수 있지만 타일에서 스레드의 실행 순서는 보장 되지 않습니다. 다음 예제에서는 `tile_static` 변수와 `tile_barrier::wait` 메서드를 사용 하 여 각 타일의 평균 값을 계산 하는 방법을 보여 줍니다. 다음은 예제를 이해 하는 데 사용할 키입니다.

1. RawData는 8x8 행렬에 저장 됩니다.

2. 타일 크기는 2x2입니다. 이렇게 하면 바둑판의 4x4 눈금이 만들어지고 평균은 `array` 개체를 사용 하 여 4x4 행렬에 저장할 수 있습니다. AMP 제한 함수에서 참조로 캡처할 수 있는 형식 수는 제한 되어 있습니다. `array` 클래스는 그 중 하나입니다.

3. `array`, `array_view`, `extent`및 `tiled_index`에 대 한 형식 매개 변수는 상수 값 이어야 하므로 행렬 크기와 샘플 크기는 `#define` 문을 사용 하 여 정의 됩니다. `const int static` 선언을 사용할 수도 있습니다. 추가 혜택으로, 4x4 타일에 대 한 평균을 계산 하기 위해 샘플 크기를 변경 하는 것은 간단 합니다.

4. 각 타일에 대해 `tile_static` 2x2 배열의 float 값이 선언 됩니다. 선언이 모든 스레드에 대 한 코드 경로에 있더라도 행렬의 각 타일에 대해 하나의 배열만 생성 됩니다.

5. 각 타일의 값을 `tile_static` 배열에 복사 하는 코드 줄이 있습니다. 각 스레드에 대 한 값이 배열에 복사 된 후에는 `tile_barrier::wait`에 대 한 호출로 인해 스레드에서 실행이 중지 됩니다.

6. 타일의 모든 스레드가 장벽에 도달 하면 평균을 계산할 수 있습니다. 모든 스레드에 대해 코드가 실행 되기 때문에 하나의 스레드에서만 평균을 계산 하는 `if` 문이 있습니다. 평균은 평균 변수에 저장 됩니다. 장애물은 기본적으로 `for` 루프를 사용할 때와 마찬가지로 타일로 계산을 제어 하는 구문입니다.

7. `averages` 변수의 데이터는 `array` 개체 이기 때문에 다시 호스트에 복사 해야 합니다. 이 예에서는 vector 변환 연산자를 사용 합니다.

8. 전체 예제에서는 SAMPLESIZE를 4로 변경 하 고 다른 변경 내용 없이 코드가 제대로 실행 되도록 할 수 있습니다.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESSIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>경합 조건

다음과 같이 `total` 이라는 `tile_static` 변수를 만들고 각 스레드에 대해 해당 변수를 증가 시킬 수 있습니다.

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

이 방법의 첫 번째 문제는 `tile_static` 변수에 이니셜라이저를 사용할 수 없다는 것입니다. 두 번째 문제는 타일의 모든 스레드가 특정 순서로 변수를 액세스할 수 있기 때문에 `total`할당에 대 한 경합 상태가 있다는 것입니다. 다음에 표시 된 것 처럼 하나의 스레드만 각 장벽에 있는 합계에 액세스 하도록 허용 하는 알고리즘을 프로그래밍할 수 있습니다. 그러나이 솔루션은 확장할 수 없습니다.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>메모리 펜스

동기화 해야 하는 두 가지 종류의 메모리 액세스 (전역 메모리 액세스 및 `tile_static` 메모리 액세스)가 있습니다. `concurrency::array` 개체는 전역 메모리만 할당 합니다. `concurrency::array_view`는 생성 된 방법에 따라 전역 메모리, `tile_static` 메모리 또는 둘 다를 참조할 수 있습니다.  동기화 해야 하는 두 가지 종류의 메모리가 있습니다.

- 전역 메모리

- `tile_static`

*메모리 펜스* 는 스레드 타일의 다른 스레드에서 메모리 액세스를 사용할 수 있는지 확인 하 고, 메모리 액세스는 프로그램 순서에 따라 실행 됩니다. 이를 위해 컴파일러 및 프로세서는 fence에서 읽기와 쓰기를 다시 정렬 하지 않습니다. AMP C++ 에서 다음 메서드 중 하나를 호출 하 여 메모리 펜스를 만듭니다.

- [tile_barrier:: Wait 메서드](reference/tile-barrier-class.md#wait): 전역 및 `tile_static` 메모리 주위에 fence를 만듭니다.

- [tile_barrier:: Wait_with_all_memory_fence 메서드](reference/tile-barrier-class.md#wait_with_all_memory_fence): 전역 및 `tile_static` 메모리 주위에 fence를 만듭니다.

- [tile_barrier:: Wait_with_global_memory_fence 메서드](reference/tile-barrier-class.md#wait_with_global_memory_fence): 전역 메모리만 주위에 fence를 만듭니다.

- [tile_barrier:: Wait_with_tile_static_memory_fence 메서드](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): `tile_static` 메모리 주위에만 울타리를 만듭니다.

필요한 특정 fence를 호출 하면 앱의 성능을 향상 시킬 수 있습니다. 장애물 형식은 컴파일러와 하드웨어의 순서 재정리 문 방식에 영향을 줍니다. 예를 들어 전역 메모리 fence를 사용 하는 경우이는 전역 메모리 액세스에만 적용 되므로 컴파일러와 하드웨어는 울타리의 두 면에서 `tile_static` 변수에 대 한 읽기 및 쓰기의 순서를 변경할 수 있습니다.

다음 예제에서 장애물은 `tile_static` 변수로 `tileValues`쓰기를 동기화 합니다. 이 예제에서는 `tile_barrier::wait`대신 `tile_barrier::wait_with_tile_static_memory_fence`가 호출 됩니다.

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>참조

[C++ AMP(C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static 키워드](../../cpp/tile-static-keyword.md)

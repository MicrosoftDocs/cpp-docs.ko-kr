---
title: '연습: 매트릭스 곱'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: d45e731cefe51a815424aa941362dce8ceaa4500
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924352"
---
# <a name="walkthrough-matrix-multiplication"></a>연습: 매트릭스 곱

이 단계별 연습에서는 C++ AMP 사용 하 여 행렬 곱셈의 실행 속도를 가속화 하는 방법을 보여 줍니다. 바둑판식으로 배열 하지 않고 바둑판식 배열을 표시 하는 두 개의 알고리즘이 표시 됩니다.

## <a name="prerequisites"></a>사전 요구 사항

시작하기 전에

- [C++ AMP 개요](../../parallel/amp/cpp-amp-overview.md)를 참조 하세요.

- [타일을 사용 하 여](../../parallel/amp/using-tiles.md)읽습니다.

- Windows 7 또는 Windows Server 2008 R2 이상을 실행 중인지 확인 합니다.

### <a name="to-create-the-project"></a>프로젝트를 만들려면

새 프로젝트를 만드는 방법에 대 한 지침은 설치한 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Visual Studio 2019에서 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **콘솔** 로 설정합니다.

1. 필터링 된 프로젝트 형식 목록에서 **빈 프로젝트** 를 선택 하 고 **다음** 을 선택 합니다. 다음 페이지에서 **이름** 상자에 *MatrixMultiply* 를 입력 하 여 프로젝트 이름을 지정 하 고 원하는 경우 프로젝트 위치를 지정 합니다.

   ![새 콘솔 앱](../../build/media/mathclient-project-name-2019.png "새 콘솔 앱")

1. **만들기** 단추를 선택하여 클라이언트 프로젝트를 만듭니다.

1. **솔루션 탐색기** 에서 **소스 파일** 에 대 한 바로 가기 메뉴를 연 다음 **Add** > **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **c + + 파일 (.cpp)** 을 선택 하 고 **이름** 상자에 *MatrixMultiply* 를 입력 한 다음 **추가** 단추를 선택 합니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Visual Studio 2017 또는 2015에서 프로젝트를 만들려면

1. Visual Studio의 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택 합니다.

1. 템플릿 창에서 **설치 됨** 아래에서 **Visual C++** 을 선택 합니다.

1. **빈 프로젝트** 를 선택 하 고 **이름** 상자에 *MatrixMultiply* 를 입력 한 다음 **확인** 단추를 선택 합니다.

1. **다음** 단추를 선택합니다.

1. **솔루션 탐색기** 에서 **소스 파일** 에 대 한 바로 가기 메뉴를 연 다음 **Add** > **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **c + + 파일 (.cpp)** 을 선택 하 고 **이름** 상자에 *MatrixMultiply* 를 입력 한 다음 **추가** 단추를 선택 합니다.

::: moniker-end

## <a name="multiplication-without-tiling"></a>바둑판식 배열 없이 곱하기

이 섹션에서는 다음과 같이 정의 된 두 행렬 A와 B의 곱셈을 고려 합니다.

![3&#45;2 행렬 A&#45;](../../parallel/amp/media/campmatrixanontiled.png "3&#45;2 행렬 A&#45;")

![2&#45;매트릭스 B&#45;3](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;매트릭스 B&#45;3")

A는 3 x 2 행렬 이며 B는 2/3 행렬입니다. A를 B로 곱한 곱은 다음 3 x 3 매트릭스입니다. 이 제품은 A의 행과 B 요소의 열을 곱하여 계산 됩니다.

![3&#45;3 제품 매트릭스로&#45;](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;3 제품 매트릭스로&#45;")

### <a name="to-multiply-without-using-c-amp"></a>C++ AMP 사용 하지 않고 곱하려면

1. MatrixMultiply를 열고 다음 코드를 사용 하 여 기존 코드를 바꿉니다.

   ```cpp
   #include <iostream>

   void MultiplyWithOutAMP() {
       int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
       int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
       int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

       for (int row = 0; row < 3; row++) {
           for (int col = 0; col < 3; col++) {
               // Multiply the row of A by the column of B to get the row, column of product.
               for (int inner = 0; inner < 2; inner++) {
                   product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
               }
               std::cout << product[row][col] << "  ";
           }
           std::cout << "\n";
       }
   }

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   알고리즘은 행렬 곱셈의 정의를 간단 하 게 구현한 것입니다. 계산 시간을 줄이기 위해 병렬 또는 스레드 알고리즘을 사용 하지 않습니다.

1. 메뉴 모음에서 **파일**  >  **모두 저장** 을 선택 합니다.

1. **F5** 바로 가기 키를 선택 하 여 디버깅을 시작 하 고 출력이 올바른지 확인 합니다.

1. **Enter** 를 선택 하 여 응용 프로그램을 종료 합니다.

### <a name="to-multiply-by-using-c-amp"></a>C++ AMP를 사용 하 여 곱하려면

1. MatrixMultiply에서 메서드 앞에 다음 코드를 추가 합니다 `main` .

   ```cpp
   void MultiplyWithAMP() {
   int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
   int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
   int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

   array_view<int, 2> a(3, 2, aMatrix);

   array_view<int, 2> b(2, 3, bMatrix);

   array_view<int, 2> product(3, 3, productMatrix);

   parallel_for_each(product.extent,
      [=] (index<2> idx) restrict(amp) {
          int row = idx[0];
          int col = idx[1];
          for (int inner = 0; inner <2; inner++) {
              product[idx] += a(row, inner)* b(inner, col);
          }
      });

   product.synchronize();

   for (int row = 0; row <3; row++) {
      for (int col = 0; col <3; col++) {
          //std::cout << productMatrix[row*3 + col] << "  ";
          std::cout << product(row, col) << "  ";
      }
      std::cout << "\n";
     }
   }
   ```

   AMP 코드는 비 AMP 코드와 유사 합니다. 호출은 `parallel_for_each` 의 각 요소에 대해 하나의 스레드를 시작 하 `product.extent` 고 **`for`** 행 및 열에 대 한 루프를 대체 합니다. 행과 열에 있는 셀의 값은에서 사용할 수 있습니다 `idx` . `array_view` `[]` 연산자와 인덱스 변수 또는 `()` 연산자와 행 및 열 변수를 사용 하 여 개체의 요소에 액세스할 수 있습니다. 이 예제에서는 두 메서드를 모두 보여 줍니다. 메서드는 변수의 `array_view::synchronize` 값을 `product` 다시 `productMatrix` 변수에 복사 합니다.

1. `include` **`using`** MatrixMultiply의 맨 위에 다음 및 문을 추가 합니다.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. 메서드를 수정 `main` 하 여 메서드를 호출 `MultiplyWithAMP` 합니다.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. **Ctrl** + **F5** 바로 가기 키를 눌러 디버깅을 시작 하 고 출력이 올바른지 확인 합니다.

1. 응용 프로그램을 종료 하려면 **스페이스바** 를 누릅니다.

## <a name="multiplication-with-tiling"></a>바둑판식 배열을 사용한 곱하기

바둑판식 배열은 데이터를 동일한 크기의 하위 집합 (타일 이라고 함)으로 분할 하는 기술입니다. 바둑판식 배열을 사용할 때 세 가지 항목이 변경 됩니다.

- 변수를 만들 수 있습니다 `tile_static` . 공간에 있는 데이터에 대 한 액세스 `tile_static` 는 전역 공간의 데이터에 액세스 하는 것 보다 많은 시간이 더 빠를 수 있습니다. `tile_static`각 타일에 대해 변수의 인스턴스가 생성 되 고 타일의 모든 스레드가 변수에 액세스할 수 있습니다. 바둑판식 배열의 주요 이점은 액세스로 인 한 성능 향상입니다 `tile_static` .

- [Tile_barrier:: wait](reference/tile-barrier-class.md#wait) 메서드를 호출 하 여 지정 된 코드 줄에서 한 타일의 모든 스레드를 중지할 수 있습니다. 스레드가 실행 되는 순서를 보장할 수 없으며, 한 타일의 모든 스레드가 `tile_barrier::wait` 실행을 계속 하기 전에에 대 한 호출에서 중지 됩니다.

- 전체 개체에 상대적인 스레드 인덱스 `array_view` 와 타일에 상대적인 인덱스에 액세스할 수 있습니다. 로컬 인덱스를 사용 하 여 코드를 더 쉽게 읽고 디버그할 수 있습니다.

행렬 곱셈에서 바둑판식 배열을 활용 하려면 알고리즘은 행렬을 타일로 분할 한 다음 `tile_static` 더 빠른 액세스를 위해 타일 데이터를 변수에 복사 해야 합니다. 이 예제에서 행렬은 같은 크기의 하위 행렬로 분할 됩니다. 이 제품은 submatrices을 곱하여 확인할 수 있습니다. 이 예제에서 두 매트릭스와 해당 제품은 다음과 같습니다.

![4 매트릭스 A&#45;4&#45;](../../parallel/amp/media/campmatrixatiled.png "4 매트릭스 A&#45;4&#45;")

![4 매트릭스 B&#45;4&#45;](../../parallel/amp/media/campmatrixbtiled.png "4 매트릭스 B&#45;4&#45;")

![4&#45;&#45;4 제품 매트릭스](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;&#45;4 제품 매트릭스")

행렬은 4 개의 2x2 행렬로 분할 되며 다음과 같이 정의 됩니다.

![4&#45;2 개의 sub&#45;매트릭스에&#45;의해 2&#45;분할 된&#45;4 행렬](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;2 개의 sub&#45;매트릭스에&#45;의해 2&#45;분할 된&#45;4 행렬")

![4&#45;&#45;4 행렬 B&#45;를&#45;2 개 하위&#45;매트릭스로 분할](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;&#45;4 행렬 B&#45;를&#45;2 개 하위&#45;매트릭스로 분할")

이제 A와 B의 제품을 다음과 같이 작성 하 고 계산할 수 있습니다.

![4&#45;&#45;4 행렬 A B&#45;2 개 하위&#45;매트릭스&#45;로 분할 됨](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;&#45;4 행렬 A B&#45;2 개 하위&#45;매트릭스&#45;로 분할 됨")

매트릭스가 2x2 매트릭스가 기 때문에 `a` `h` 모든 제품 및 합계는 2x2 매트릭스 이기도 합니다. 또한 A와 B의 제품이 예상 대로 4x4 행렬 임을 따르고 있습니다. 알고리즘을 신속 하 게 확인 하려면 제품에서 첫 번째 행의 첫 번째 열에 있는 요소의 값을 계산 합니다. 이 예제에서는의 첫 번째 행과 첫 번째 열에 있는 요소의 값입니다 `ae + bg` . `ae`각 용어에 대해 첫 번째 열인 및의 첫 번째 행만 계산 하면 `bg` 됩니다. 에 대 한 값 `ae` 은입니다 `(1 * 1) + (2 * 5) = 11` . `bg`의 값이 `(3 * 1) + (4 * 5) = 23`인 경우 마지막 값은 이며,이 값은 `11 + 23 = 34` 올바릅니다.

이 알고리즘을 구현 하려면 코드는 다음과 같습니다.

- `tiled_extent`호출에서 개체 대신 개체를 사용 `extent` `parallel_for_each` 합니다.

- `tiled_index`호출에서 개체 대신 개체를 사용 `index` `parallel_for_each` 합니다.

- `tile_static`Submatrices을 저장할 변수를 만듭니다.

- 메서드를 사용 하 여 `tile_barrier::wait` submatrices의 제품 계산에 대 한 스레드를 중지 합니다.

### <a name="to-multiply-by-using-amp-and-tiling"></a>AMP 및 바둑판식 배열을 사용 하 여 곱하려면

1. MatrixMultiply에서 메서드 앞에 다음 코드를 추가 합니다 `main` .

   ```cpp
   void MultiplyWithTiling() {
       // The tile size is 2.
       static const int TS = 2;

       // The raw data.
       int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
       int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
       int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

       // Create the array_view objects.
       array_view<int, 2> a(4, 4, aMatrix);
       array_view<int, 2> b(4, 4, bMatrix);
       array_view<int, 2> product(4, 4, productMatrix);

       // Call parallel_for_each by using 2x2 tiles.
       parallel_for_each(product.extent.tile<TS, TS>(),
           [=] (tiled_index<TS, TS> t_idx) restrict(amp)
           {
               // Get the location of the thread relative to the tile (row, col)
               // and the entire array_view (rowGlobal, colGlobal).
               int row = t_idx.local[0];
               int col = t_idx.local[1];
               int rowGlobal = t_idx.global[0];
               int colGlobal = t_idx.global[1];
               int sum = 0;

               // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
               // For the first tile and the first loop, it copies a into locA and e into locB.
               // For the first tile and the second loop, it copies b into locA and g into locB.
               for (int i = 0; i < 4; i += TS) {
                   tile_static int locA[TS][TS];
                   tile_static int locB[TS][TS];
                   locA[row][col] = a(rowGlobal, col + i);
                   locB[row][col] = b(row + i, colGlobal);
                   // The threads in the tile all wait here until locA and locB are filled.
                   t_idx.barrier.wait();

                   // Return the product for the thread. The sum is retained across
                   // both iterations of the loop, in effect adding the two products
                   // together, for example, a*e.
                   for (int k = 0; k < TS; k++) {
                       sum += locA[row][k] * locB[k][col];
                   }

                   // All threads must wait until the sums are calculated. If any threads
                   // moved ahead, the values in locA and locB would change.
                   t_idx.barrier.wait();
                   // Now go on to the next iteration of the loop.
               }

               // After both iterations of the loop, copy the sum to the product variable by using the global location.
               product[t_idx.global] = sum;
           });

       // Copy the contents of product back to the productMatrix variable.
       product.synchronize();

       for (int row = 0; row <4; row++) {
           for (int col = 0; col <4; col++) {
               // The results are available from both the product and productMatrix variables.
               //std::cout << productMatrix[row*3 + col] << "  ";
               std::cout << product(row, col) << "  ";
           }
           std::cout << "\n";
       }
   }
   ```

   이 예제는 바둑판식 배열 없이 예제와 크게 다릅니다. 이 코드에서는 다음과 같은 개념 단계를 사용 합니다.
   1. 의 타일 [0, 0]의 요소를 `a` 에 복사 `locA` 합니다. 의 타일 [0, 0]의 요소를 `b` 에 복사 `locB` 합니다. 는 `product` 및가 아니라 바둑판식으로 배열 됩니다 `a` `b` . 따라서 전역 인덱스를 사용 하 여 `a, b` , 및에 액세스 `product` 합니다. 에 대 한 호출은 `tile_barrier::wait` 필수입니다. 및가 모두 채워질 때까지 타일에 있는 모든 스레드를 중지 `locA` `locB` 합니다.

   1. 및를 곱하여 `locA` `locB` 결과를에 넣습니다 `product` .

   1. 의 타일 [0, 1]의 요소를 `a` 에 복사 `locA` 합니다. 의 타일 [1, 0]의 요소를 `b` 에 복사 `locB` 합니다.

   1. 및를 곱하여 `locA` `locB` 이미에 있는 결과에 추가 `product` 합니다.

   1. 타일 [0, 0]의 곱셈이 완료 되었습니다.

   1. 다른 네 타일에 대해 반복 합니다. 특히 타일에 대 한 인덱싱이 없으며 스레드를 순서에 관계 없이 실행할 수 있습니다. 각 스레드가 실행 될 때 `tile_static` 각 타일에 대 한 변수가 적절 하 게 생성 되 고에 대 한 호출이 `tile_barrier::wait` 프로그램 흐름을 제어 합니다.

   1. 알고리즘을 자세히 살펴보면 각 submatrix가 메모리에 두 번 로드 되는 것을 알 수 있습니다 `tile_static` . 데이터 전송에 시간이 소요 됩니다. 그러나 데이터가 메모리에 있는 경우에는 `tile_static` 데이터에 대 한 액세스가 훨씬 빠릅니다. 제품을 계산 하려면 submatrices의 값에 대 한 반복적인 액세스가 필요 하므로 전반적인 성능 향상이 있습니다. 각 알고리즘에 대해 최적의 알고리즘과 타일 크기를 찾기 위해 실험이 필요 합니다.

   비 AMP 및 비 타일 예제에서 A와 B의 각 요소는 전역 메모리에서 4 번 액세스 되어 제품을 계산 합니다. 타일 예제에서 각 요소는 전역 메모리에서 두 번 액세스 되 고 메모리에서 4 번 액세스 됩니다 `tile_static` . 이는 상당한 성능상의 이점이 아닙니다. 그러나 A와 B가 1024x1024 매트릭스가 고 타일 크기가 16 인 경우 성능이 크게 향상 됩니다. 이 경우 각 요소는 `tile_static` 메모리에 16 번만 복사 되 고 `tile_static` 메모리 1024 시간에서 액세스 됩니다.

1. 다음과 같이 main 메서드를 수정 하 여 메서드를 호출 합니다 `MultiplyWithTiling` .

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. **Ctrl** + **F5** 바로 가기 키를 눌러 디버깅을 시작 하 고 출력이 올바른지 확인 합니다.

1. 응용 프로그램을 종료 하려면 **공간** 표시줄을 누릅니다.

## <a name="see-also"></a>참고 항목

[C++ AMP(C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[연습: C++ AMP 애플리케이션 디버깅](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)

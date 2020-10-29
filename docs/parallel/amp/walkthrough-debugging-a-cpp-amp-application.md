---
title: '연습: C++ AMP 애플리케이션 디버깅'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 21ce276af9317c06f3b717b41685f419d2362d70
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921687"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>연습: C++ AMP 애플리케이션 디버깅

이 항목에서는 C++ Accelerated Massive Parallelism (C++ AMP)를 사용 하 여 GPU (그래픽 처리 장치)를 활용 하는 응용 프로그램을 디버깅 하는 방법을 보여 줍니다. 이는 정수 배열을 합산 하는 병렬 감소 프로그램을 사용 합니다. 이 연습에서는 다음 작업을 수행합니다.

- GPU 디버거를 시작 합니다.

- GPU 스레드 창에서 GPU 스레드를 검사 합니다.

- **병렬 스택** 창을 사용 하 여 여러 GPU 스레드의 호출 스택을 동시에 관찰 합니다.

- **병렬 조사식** 창을 사용 하 여 동시에 여러 스레드에서 단일 식의 값을 검사 합니다.

- GPU 스레드를 플래그, 고정, 재개 및 그룹화 합니다.

- 타일의 모든 스레드를 코드의 특정 위치에 실행 합니다.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 시작 하기 전에:

- [C++ AMP 개요](../../parallel/amp/cpp-amp-overview.md)를 참조 하세요.

- 줄 번호가 텍스트 편집기에 표시 되는지 확인 합니다. 자세한 내용은 [방법: 편집기에서 줄 번호 표시](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)를 참조 하세요.

- 소프트웨어 에뮬레이터에서 디버깅을 지원 하기 위해 Windows 8 또는 Windows Server 2012 이상을 실행 하 고 있는지 확인 합니다.

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>샘플 프로젝트를 만들려면

프로젝트를 만드는 방법에 대 한 지침은 사용 중인 Visual Studio 버전에 따라 다릅니다. 이 페이지의 왼쪽 위에서 올바른 버전을 선택 했는지 확인 합니다.

::: moniker range="msvc-160"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>Visual Studio 2019에서 샘플 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **콘솔** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **콘솔 앱** 을 선택한 후 **다음** 을 선택합니다. 다음 페이지에서 **이름** 상자에 `AMPMapReduce`를 입력하여 프로젝트 이름을 지정하고 원하는 경우 프로젝트 위치를 지정합니다.

   ![프로젝트 이름](../../build/media/mathclient-project-name-2019.png "프로젝트 이름을")

1. **만들기** 단추를 선택하여 클라이언트 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>Visual Studio 2017 또는 Visual Studio 2015에서 샘플 프로젝트를 만들려면

1. Visual Studio를 시작합니다.

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. 템플릿 창에서 **설치 됨** 아래에서 **Visual C++** 을 선택 합니다.

1. **Win32 콘솔 응용 프로그램** 을 선택 하 고 `AMPMapReduce` **이름** 상자에를 입력 한 다음 **확인** 단추를 선택 합니다.

1. **다음** 단추를 선택합니다.

1. **미리 컴파일된 헤더** 확인란을 선택 취소 한 후 **마침** 단추를 선택 합니다.

1. **솔루션 탐색기** 에서 프로젝트의 *stdafx.h* , *targetver* 및 *stdafx.h* 를 삭제 합니다.

::: moniker-end

다음:

1. AMPMapReduce를 열고 해당 콘텐츠를 다음 코드로 바꿉니다.

```cpp
    // AMPMapReduce.cpp defines the entry point for the program.
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.

    #include <stdio.h>
    #include <tchar.h>
    #include <amp.h>

    const int BLOCK_DIM = 32;

    using namespace concurrency;

    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)
    {
        tile_static int localA[BLOCK_DIM];

        index<1> globalIdx = t_idx.global * stride_size;
        index<1> localIdx = t_idx.local;

        localA[localIdx[0]] =  A[globalIdx];

        t_idx.barrier.wait();

        // Aggregate all elements in one tile into the first element.
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)
        {
            if (localIdx[0] < i)
            {

                localA[localIdx[0]] += localA[localIdx[0] + i];
            }

            t_idx.barrier.wait();
        }

        if (localIdx[0] == 0)
        {
            A[globalIdx] = localA[0];
        }
    }

    int size_after_padding(int n)
    {
        // The extent might have to be slightly bigger than num_stride to
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;
    }

    int reduction_sum_gpu_kernel(array<int, 1> input)
    {
        int len = input.extent[0];

        //Tree-based reduction control that uses the CPU.
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)
        {
            // Number of useful values in the array, given the current
            // stride size.
            int num_strides = len / stride_size;

            extent<1> e(size_after_padding(num_strides));

            // The sum kernel that uses the GPU.
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)
            {
                sum_kernel_tiled(idx, input, stride_size);
            });
        }

        array_view<int, 1> output = input.section(extent<1>(1));
        return output[0];
    }

    int cpu_sum(const std::vector<int> &arr) {
        int sum = 0;
        for (size_t i = 0; i < arr.size(); i++) {
            sum += arr[i];
        }
        return sum;
    }

    std::vector<int> rand_vector(unsigned int size) {
        srand(2011);

        std::vector<int> vec(size);
        for (size_t i = 0; i < size; i++) {
            vec[i] = rand();
        }
        return vec;
    }

    array<int, 1> vector_to_array(const std::vector<int> &vec) {
        array<int, 1> arr(vec.size());
        copy(vec.begin(), vec.end(), arr);
        return arr;
    }

    int _tmain(int argc, _TCHAR* argv[])
    {
        std::vector<int> vec = rand_vector(10000);
        array<int, 1> arr = vector_to_array(vec);

        int expected = cpu_sum(vec);
        int actual = reduction_sum_gpu_kernel(arr);

        bool passed = (expected == actual);
        if (!passed) {
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);
        }
        printf("sum: %s\n", passed  "Passed!" : "Failed!");

        getchar();

        return 0;
    }
```

1. 메뉴 모음에서 **파일**  >  **모두 저장** 을 선택 합니다.

1. **솔루션 탐색기** 에서 **AMPMapReduce** 의 바로 가기 메뉴를 열고 **속성** 을 선택 합니다.

1. **속성 페이지** 대화 상자의 **구성 속성** 에서 **C/c + +**  >  **미리 컴파일된 헤더** 를 선택 합니다.

1. **미리 컴파일된 헤더** 속성의 경우 **미리 컴파일된 헤더 사용 안 함** 을 선택한 다음 **확인** 단추를 선택 합니다.

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

## <a name="debugging-the-cpu-code"></a>CPU 코드 디버그

이 절차에서는 로컬 Windows 디버거를 사용 하 여이 응용 프로그램의 CPU 코드가 올바른지 확인 합니다. 이 응용 프로그램에서 특히 흥미로운 CPU 코드의 세그먼트는 **`for`** 함수의 루프입니다 `reduction_sum_gpu_kernel` . GPU에서 실행 되는 트리 기반 병렬 감소를 제어 합니다.

### <a name="to-debug-the-cpu-code"></a>CPU 코드를 디버깅 하려면

1. **솔루션 탐색기** 에서 **AMPMapReduce** 의 바로 가기 메뉴를 열고 **속성** 을 선택 합니다.

2. **속성 페이지** 대화 상자의 **구성 속성** 에서 **디버깅** 을 선택 합니다. **실행할 디버거** 목록에서 **로컬 Windows 디버거** 가 선택 되어 있는지 확인 합니다.

3. **코드 편집기** 로 돌아갑니다.

4. 다음 그림에 표시 된 코드 줄에 중단점을 설정 합니다 (약 67 줄 70).

   ![CPU 중단점](../../parallel/amp/media/campcpubreakpoints.png "CPU 중단점") <br/>
   CPU 중단점

5. 메뉴 모음에서 **디버그**  >  **디버깅 시작** 을 선택 합니다.

6. **지역** 창에서 `stride_size` 70 줄의 중단점에 도달할 때까지 값을 관찰 합니다.

7. 메뉴 모음에서 **디버그**  >  **디버깅 중지** 를 선택 합니다.

## <a name="debugging-the-gpu-code"></a>GPU 코드 디버그

이 섹션에서는 함수에 포함 된 코드 인 GPU 코드를 디버깅 하는 방법을 보여 줍니다 `sum_kernel_tiled` . GPU 코드는 각 "블록"의 정수 합계를 병렬로 계산 합니다.

### <a name="to-debug-the-gpu-code"></a>GPU 코드를 디버깅 하려면

1. **솔루션 탐색기** 에서 **AMPMapReduce** 의 바로 가기 메뉴를 열고 **속성** 을 선택 합니다.

2. **속성 페이지** 대화 상자의 **구성 속성** 에서 **디버깅** 을 선택 합니다.

3. **실행할 디버거** 목록에서 **로컬 Windows 디버거** 를 선택합니다.

4. **디버거 형식** 목록에서 **자동** 이 선택 되어 있는지 확인 합니다.

    **Auto** 는 기본값입니다. Windows 10 이전에는 **GPU만** **자동** 이 아닌 필수 값입니다.

5. **확인** 단추를 선택합니다.

6. 다음 그림과 같이 줄 30에서 중단점을 설정 합니다.

   ![GPU 중단점](../../parallel/amp/media/campgpubreakpoints.png "GPU 중단점") <br/>
   GPU 중단점

7. 메뉴 모음에서 **디버그**  >  **디버깅 시작** 을 선택 합니다. 67 및 70 줄에서 CPU 코드의 중단점은 CPU에서 해당 코드 줄이 실행 되기 때문에 GPU 디버깅 중에 실행 되지 않습니다.

### <a name="to-use-the-gpu-threads-window"></a>GPU 스레드 창을 사용 하려면

1. **Gpu 스레드** 창을 열려면 메뉴 모음에서 **디버그**  >  **Windows**  >  **GPU 스레드** 를 선택 합니다.

   표시 되는 **Gpu 스레드** 창에서 gpu 스레드 상태를 검사할 수 있습니다.

2. Visual Studio 아래쪽에 **GPU 스레드** 창을 도킹 합니다. **스레드 확장 스위치** 단추를 선택 하 여 타일 및 스레드 텍스트 상자를 표시 합니다. **Gpu 스레드** 창에는 다음 그림과 같이 활성 및 차단 된 gpu 스레드의 총 수가 표시 됩니다.

   ![4개의 활성 스레드가 있는 GPU 스레드 창](../../parallel/amp/media/campc.png "4개의 활성 스레드가 있는 GPU 스레드 창") <br/>
   GPU 스레드 창

   이 계산에 할당 된 313 타일이 있습니다. 각 타일에는 32 스레드가 포함 되어 있습니다. 로컬 GPU 디버깅은 소프트웨어 에뮬레이터에서 발생 하므로 4 개의 활성 GPU 스레드가 있습니다. 네 개의 스레드가 명령을 동시에 실행 한 다음, 다음 명령으로 함께 이동 합니다.

   **Gpu 스레드** 창에는 네 개의 gpu 스레드를 활성으로, 28 gpu 스레드는 about 줄 21 ()에 정의 된 [tile_barrier:: wait](reference/tile-barrier-class.md#wait) 문에 의해 차단 됩니다 `t_idx.barrier.wait();` . 모든 32 GPU 스레드는 첫 번째 타일에 속합니다 `tile[0]` . 화살표는 현재 스레드를 포함 하는 행을 가리킵니다. 다른 스레드로 전환 하려면 다음 방법 중 하나를 사용 합니다.

    - **GPU 스레드** 창에서 전환할 스레드의 행에서 바로 가기 메뉴를 열고 **스레드로 전환** 을 선택 합니다. 행이 둘 이상의 스레드를 나타내는 경우 스레드 좌표에 따라 첫 번째 스레드로 전환 합니다.

    - 해당 텍스트 상자에 스레드의 타일 및 스레드 값을 입력 한 다음 **스레드 전환** 단추를 선택 합니다.

   **호출 스택** 창에는 현재 GPU 스레드의 호출 스택이 표시 됩니다.

### <a name="to-use-the-parallel-stacks-window"></a>병렬 스택 창을 사용 하려면

1. **병렬 스택** 창을 열려면 메뉴 모음에서 **디버그**  >  **Windows**  >  **병렬 스택** 을 선택 합니다.

   **병렬 스택** 창을 사용 하 여 여러 GPU 스레드의 스택 프레임을 동시에 검사할 수 있습니다.

2. **병렬 스택** 창을 Visual Studio 아래쪽에 도킹 합니다.

3. 왼쪽 위 모퉁이의 목록에서 **스레드** 가 선택 되어 있는지 확인 합니다. 다음 그림의 **병렬 스택** 창에는 **gpu 스레드** 창에서 보았던 gpu 스레드의 호출 스택 중심 뷰가 표시 됩니다.

   ![4개의 활성 스레드가 있는 병렬 스택 창](../../parallel/amp/media/campd.png "4개의 활성 스레드가 있는 병렬 스택 창") <br/>
   병렬 스택 창

   32 스레드가 `_kernel_stub` 함수 호출의 람다 문으로 이동한 `parallel_for_each` 다음 `sum_kernel_tiled` 병렬 감소가 발생 하는 함수로 이동 했습니다. 32 스레드의 28 개는 [tile_barrier:: wait](reference/tile-barrier-class.md#wait) 문으로 진행 되 고 줄 22에서 차단 된 상태로 유지 되지만 나머지 4 개 스레드는 줄 30의 함수에서 활성 상태로 유지 됩니다 `sum_kernel_tiled` .

   **병렬 스택** 창의 풍부한 DataTip에서 **gpu 스레드** 창에서 사용할 수 있는 gpu 스레드의 속성을 검사할 수 있습니다. 이렇게 하려면 **sum_kernel_tiled** 의 스택 프레임에 마우스 포인터를 놓습니다. 다음 그림에서는 DataTip을 보여 줍니다.

   ![병렬 스택용 DataTip 창](../../parallel/amp/media/campe.png "병렬 스택용 DataTip 창") <br/>
   GPU 스레드 DataTip

   **병렬 스택** 창에 대 한 자세한 내용은 [병렬 스택 창 사용](/visualstudio/debugger/using-the-parallel-stacks-window)을 참조 하세요.

### <a name="to-use-the-parallel-watch-window"></a>병렬 조사식 창를 사용 하려면

1. **병렬 조사식** 창을 열려면 메뉴 모음에서 **디버그**  >  **Windows**  >  **병렬 조사식**  >  **병렬 조사식 1** 을 선택 합니다.

   **병렬 조사식** 창을 사용 하 여 여러 스레드에서 식의 값을 검사할 수 있습니다.

2. **병렬 조사식 1** 창을 Visual Studio 아래쪽에 도킹 합니다. **병렬 조사식** 창의 테이블에는 32 개의 행이 있습니다. 각는 GPU 스레드 창과 **병렬 스택** 창에 모두 표시 되는 gpu 스레드에 해당 합니다. 이제 모든 32 GPU 스레드 간에 검사할 값이 있는 식을 입력할 수 있습니다.

3. 조사식 열 **추가** 헤더를 선택 하 `localIdx` 고를 입력 한 다음 **enter** 키를 선택 합니다.

4. 조사식 열 **추가** 헤더를 다시 선택 하 `globalIdx` 고을 입력 한 다음 **Enter** 키를 선택 합니다.

5. 조사식 열 **추가** 헤더를 다시 선택 하 `localA[localIdx[0]]` 고을 입력 한 다음 **Enter** 키를 선택 합니다.

   해당 열 머리글을 선택 하 여 지정 된 식으로 정렬할 수 있습니다.

   **Locala [Locala [0]]** 열 머리글을 선택 하 여 열을 정렬 합니다. 다음 그림에서는 **Locala [Locala [0]]** 을 기준으로 정렬 한 결과를 보여 줍니다.

   ![정렬된 결과가 포함된 병렬 조사식 창](../../parallel/amp/media/campf.png "정렬된 결과가 포함된 병렬 조사식 창") <br/>
   정렬 결과

   **Excel** 단추를 선택 하 고 **excel에서 열기** 를 선택 하 여 **병렬 조사식** 창의 콘텐츠를 excel로 내보낼 수 있습니다. 개발 컴퓨터에 Excel이 설치 되어 있는 경우 콘텐츠가 포함 된 Excel 워크시트가 열립니다.

6. **병렬 조사식** 창의 오른쪽 위 모퉁이에는 부울 식을 사용 하 여 콘텐츠를 필터링 하는 데 사용할 수 있는 필터 컨트롤이 있습니다. `localA[localIdx[0]] > 20000`필터 제어 텍스트 상자에를 입력 한 다음 **enter** 키를 선택 합니다.

   이제 창에는 `localA[localIdx[0]]` 값이 2만 보다 큰 스레드만 포함 됩니다. 콘텐츠는 아직 `localA[localIdx[0]]` 앞에서 수행한 정렬 작업 인 열을 기준으로 정렬 됩니다.

## <a name="flagging-gpu-threads"></a>GPU 스레드 플래그

**Gpu 스레드** 창, **병렬 조사식** 창 또는 **병렬 스택** 창의 DataTip에 플래그를 지정 하 여 특정 GPU 스레드를 표시할 수 있습니다. GPU 스레드 창의 행에 두 개 이상의 스레드가 포함 된 경우 해당 행에 플래그를 추가 하면 행에 포함 된 모든 스레드에 플래그를 추가 합니다.

### <a name="to-flag-gpu-threads"></a>GPU 스레드에 플래그를 지정 하려면

1. **병렬 조사식 1** 창의 **[스레드]** 열 머리글을 선택 하 여 타일 인덱스 및 스레드 인덱스를 기준으로 정렬 합니다.

2. 메뉴 모음에서 **디버그**  >  **계속** 을 선택 하 여 활성 상태인 네 개의 스레드가 다음 장벽 (AMPMapReduce의 줄 32에 정의 됨)으로 진행 되도록 합니다.

3. 현재 활성화 되어 있는 4 개의 스레드를 포함 하는 행의 왼쪽에서 플래그 기호를 선택 합니다.

   다음 그림은 **GPU 스레드** 창에서 4 개의 활성 플래그가 지정 된 스레드를 보여 줍니다.

   ![플래그 지정된 스레드가 있는 GPU 스레드 창](../../parallel/amp/media/campg.png "플래그 지정된 스레드가 있는 GPU 스레드 창") <br/>
   GPU 스레드 창의 활성 스레드

   병렬 **조사식** 창 및 **병렬 스택** 창의 DataTip은 모두 플래그가 지정 된 스레드를 표시 합니다.

4. 플래그가 지정 된 네 개의 스레드에 집중 하려면 **GPU 스레드** , **병렬 조사식** 및 **병렬 스택** 창에서 플래그가 지정 된 스레드만 표시 하도록 선택할 수 있습니다.

   Windows 또는 **디버그 위치** 도구 모음에서 **플래그가 지정 된 항목만 표시** 단추를 선택 합니다. 다음 그림에서는 **디버그 위치** 도구 모음의 **플래그가 지정 된 항목만 표시** 단추를 보여 줍니다.

   ![플래그 설정된 항목만 표시 아이콘이 있는 디버그 위치 도구 모음](../../parallel/amp/media/camph.png "플래그 설정된 항목만 표시 아이콘이 있는 디버그 위치 도구 모음") <br/>
   **플래그가 지정 된 항목만 표시** 단추

   이제 **GPU 스레드** , **병렬 조사식** 및 **병렬 스택** 창에는 플래그가 지정 된 스레드만 표시 됩니다.

## <a name="freezing-and-thawing-gpu-threads"></a>GPU 스레드 고정 및 재개

**Gpu 스레드** 창이 나 **병렬 조사식** 창에서 gpu 스레드를 중지 (일시 중단) 및 재개 (다시 시작) 할 수 있습니다. 동일한 방식으로 CPU 스레드를 중지 하 고 재개 할 수 있습니다. 자세한 내용은 [방법: 스레드 창 사용](/visualstudio/debugger/how-to-use-the-threads-window)을 참조 하세요.

### <a name="to-freeze-and-thaw-gpu-threads"></a>GPU 스레드를 중지 및 재개 하려면

1. **플래그가 지정 된 항목만** 표시 단추를 선택 하 여 모든 스레드를 표시 합니다.

2. 메뉴 모음에서 **디버그**  >  **계속** 을 선택 합니다.

3. 활성 행의 바로 가기 메뉴를 열고 **고정** 을 선택 합니다.

   다음 **GPU 스레드** 창 그림은 4 개의 스레드가 모두 고정 되어 있음을 보여 줍니다.

   ![고정된 스레드를 표시하는 GPU 스레드 창](../../parallel/amp/media/campk.png "고정된 스레드를 표시하는 GPU 스레드 창") <br/>
   **GPU 스레드** 창의 고정 스레드

   마찬가지로 **병렬 조사식** 창에는 네 개의 스레드가 모두 고정 되어 있음을 보여 줍니다.

4. 메뉴 모음에서 **디버그**  >  **계속** 을 선택 하 여 다음 4 개의 GPU 스레드가 22 줄의 장애물을 벗어나 진행 되도록 허용 하 고 줄 30에서 중단점에 도달 합니다. **GPU 스레드** 창에는 이전에 고정 된 네 개의 스레드가 고정 되어 활성 상태로 유지 되는 것으로 표시 됩니다.

5. 메뉴 모음에서 **디버그** , **계속** 을 선택 합니다.

6. **병렬 조사식** 창에서 개별 또는 다중 GPU 스레드를 재개 할 수도 있습니다.

### <a name="to-group-gpu-threads"></a>GPU 스레드를 그룹화 하려면

1. **GPU 스레드** 창에 있는 스레드 중 하나에 대 한 바로 가기 메뉴에서 **그룹화 방법** , **주소** 를 선택 합니다.

   **GPU 스레드** 창의 스레드는 주소로 그룹화 됩니다. 주소는 각 스레드 그룹이 위치한 디스어셈블리의 명령에 해당 합니다. 24 개의 스레드는 [tile_barrier:: Wait 메서드가](reference/tile-barrier-class.md#wait) 실행 되는 줄 22에 있습니다. 12 개의 스레드는 줄 32의 장벽에 대 한 명령에 있습니다. 이러한 스레드 중 4 개에 플래그가 지정 됩니다. 8 개의 스레드는 줄 30의 중단점에 있습니다. 이러한 스레드 중 4 개는 고정 되어 있습니다. 다음 그림은 **GPU 스레드** 창의 그룹화 된 스레드를 보여 줍니다.

   ![주소로 그룹화된 스레드가 있는 GPU 스레드 창](../../parallel/amp/media/campl.png "주소로 그룹화된 스레드가 있는 GPU 스레드 창") <br/>
   **GPU 스레드** 창의 그룹화 된 스레드

2. **병렬 조사식** 창의 데이터 표에 대 한 바로 가기 메뉴를 열고 **그룹화** 방법을 선택한 다음 스레드를 그룹화 할 방법에 해당 하는 메뉴 항목을 선택 하 여 **그룹화** 방법 작업을 수행할 수도 있습니다.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>코드의 특정 위치에 모든 스레드 실행

**현재 타일을 커서까지 실행을** 사용 하 여 지정 된 타일의 모든 스레드를 커서를 포함 하는 선으로 실행 합니다.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>모든 스레드를 커서로 표시 된 위치에 실행 하려면

1. 고정 된 스레드에 대 한 바로 가기 메뉴에서 **재개** 를 선택 합니다.

2. **코드 편집기** 에서 줄 30에 커서를 놓습니다.

3. **코드 편집기** 에 대 한 바로 가기 메뉴에서 **현재 타일을 커서까지 실행** 을 선택 합니다.

   이전에 줄 21의 장벽에서 차단 된 24 개의 스레드가 32 줄로 진행 되었습니다. **GPU 스레드** 창에 표시 됩니다.

## <a name="see-also"></a>참고 항목

[C++ AMP 개요](../../parallel/amp/cpp-amp-overview.md)<br/>
[GPU 코드 디버그](/visualstudio/debugger/debugging-gpu-code)<br/>
[방법: GPU 스레드 창 사용](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[방법: 병렬 조사식 창 사용](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[동시성 시각화 도우미를 사용 하 여 C++ AMP 코드 분석](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

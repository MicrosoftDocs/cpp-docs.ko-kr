---
title: C++ AMP 개요
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: 0eeda43a279be74ea71669b55356603e980cab40
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344750"
---
# <a name="c-amp-overview"></a>C++ AMP 개요

C++ Accelerated Massive Parallelism (C++ AMP)는 개별 그래픽 카드의 GPU (그래픽 처리 장치)와 같은 데이터 병렬 하드웨어를 활용 하 여 c + + 코드의 실행을 가속화 합니다. C++ AMP를 사용 하면 다른 유형의 하드웨어에서 병렬 처리를 사용 하 여 실행 속도를 가속화 하기 위해 다차원 데이터 알고리즘을 코딩할 수 있습니다. C++ AMP 프로그래밍 모델에는 다차원 배열, 인덱싱, 메모리 전송, 바둑판식 배열 및 수학 함수 라이브러리가 포함됩니다. C++ AMP 언어 확장을 사용 하 여 CPU에서 GPU로 데이터를 이동 하는 방법을 제어 하 여 성능을 향상 시킬 수 있습니다.

## <a name="system-requirements"></a>시스템 요구 사항

- Windows 7 이상

- Windows Server 2008 R2 이상

- DirectX 11 기능 수준 11.0 이상 하드웨어

- 소프트웨어 에뮬레이터에서 디버깅 하려면 Windows 8 또는 Windows Server 2012가 필요 합니다. 하드웨어에서 디버깅하는 경우에는 사용 중인 그래픽 카드의 드라이버를 설치해야 합니다. 자세한 내용은 [GPU 코드 디버깅](/visualstudio/debugger/debugging-gpu-code)을 참조하세요.

- 참고: AMP는 현재 ARM64에서 지원 되지 않습니다.

## <a name="introduction"></a>소개

다음 두 예제에서는 C++ AMP의 기본 구성 요소를 보여 줍니다. 2 1 차원 배열의 해당 요소를 추가 하려고 한다고 가정 합니다. 예를 들어를 추가 하 `{1, 2, 3, 4, 5}` 고 가져올 수 있습니다 `{6, 7, 8, 9, 10}` `{7, 9, 11, 13, 15}` . C++ AMP를 사용 하지 않고 숫자를 추가 하 고 결과를 표시 하는 다음 코드를 작성할 수 있습니다.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

코드의 중요한 부분은 다음과 같습니다.

- 데이터: 데이터는 세 개의 배열로 구성 됩니다. 모든의 순위 (1)와 길이 (5)가 동일 합니다.

- 반복: 첫 번째 **`for`** 루프는 배열의 요소를 반복 하는 메커니즘을 제공 합니다. 합계를 계산 하기 위해 실행 하려는 코드는 첫 번째 블록에 포함 되어 있습니다 **`for`** .

- Index: `idx` 변수가 배열의 개별 요소에 액세스 합니다.

C++ AMP를 사용 하 여 다음 코드를 대신 작성할 수 있습니다.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

동일한 기본 요소가 있지만 C++ AMP 구문이 사용 됩니다.

- 데이터: c + + 배열을 사용 하 여 세 개의 C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) 개체를 생성 합니다. 개체를 생성 하는 네 가지 값을 제공 합니다 `array_view` . 데이터 값, 순위, 요소 형식 및 `array_view` 각 차원에 있는 개체의 길이입니다. Rank 및 형식은 형식 매개 변수로 전달 됩니다. 데이터 및 길이는 생성자 매개 변수로 전달 됩니다. 이 예제에서 생성자에 전달 되는 c + + 배열은 1 차원입니다. 차수와 길이는 개체에서 데이터의 사각형 모양을 생성 하는 데 사용 되 `array_view` 고 데이터 값은 배열을 채우는 데 사용 됩니다. 런타임 라이브러리에는 클래스와 유사한 인터페이스가 있고이 문서의 뒷부분에서 설명 하는 [배열 클래스](../../parallel/amp/reference/array-class.md)도 포함 되어 있습니다 `array_view` .

- 반복: [Parallel_for_each 함수 (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 는 데이터 요소 또는 *계산 도메인* 을 반복 하는 메커니즘을 제공 합니다. 이 예제에서 계산 도메인은에 의해 지정 됩니다 `sum.extent` . 실행 하려는 코드는 람다 식 또는 *커널 함수* 에 포함 되어 있습니다. 는 `restrict(amp)` C++ AMP 가속화 될 수 있는 c + + 언어의 하위 집합만 사용 됨을 나타냅니다.

- 인덱스: [인덱스 클래스](../../parallel/amp/reference/index-class.md) 변수는 `idx` 개체의 순위와 일치 하는 순위 1로 선언 됩니다 `array_view` . 인덱스를 사용 하 여 개체의 개별 요소에 액세스할 수 있습니다 `array_view` .

## <a name="shaping-and-indexing-data-index-and-extent"></a>데이터 셰이핑 및 인덱싱: 인덱스 및 범위

커널 코드를 실행 하기 전에 데이터 값을 정의 하 고 데이터의 셰이프를 선언 해야 합니다. 모든 데이터는 배열 (사각형)으로 정의 되며 차수 (차원 수)를 포함 하도록 배열을 정의할 수 있습니다. 데이터는 모든 차원의 크기에 제한이 없습니다.

### <a name="index-class"></a>index 클래스

[Index 클래스](../../parallel/amp/reference/index-class.md) 는 `array` `array_view` 각 차원의 원본에서의 오프셋을 하나의 개체로 캡슐화 하 여 또는 개체의 위치를 지정 합니다. 배열의 특정 위치에 액세스 하는 경우 `index` 정수 인덱스 목록 대신 개체를 인덱싱 연산자에 전달 `[]` 합니다. [Array:: operator () 연산자](reference/array-class.md#operator_call) 또는 [array_view:: Operator () 연산자](reference/array-view-class.md#operator_call)를 사용 하 여 각 차원의 요소에 액세스할 수 있습니다.

다음 예에서는 1 차원 개체의 세 번째 요소를 지정 하는 1 차원 인덱스를 만듭니다 `array_view` . 인덱스는 개체의 세 번째 요소를 인쇄 하는 데 사용 됩니다 `array_view` . 출력은 3입니다.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

다음 예에서는 2 차원 개체에서 행이 1이 고 열이 2 인 요소를 지정 하는 2 차원 인덱스를 만듭니다 `array_view` . 생성자의 첫 번째 매개 변수는 `index` 행 구성 요소이 고 두 번째 매개 변수는 열 구성 요소입니다. 출력은 6입니다.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

다음 예에서는 깊이 = 0, 행 = 1 및 3 차원 개체의 열 = 3 인 요소를 지정 하는 3 차원 인덱스를 만듭니다 `array_view` . 첫 번째 매개 변수는 깊이 구성 요소이 고, 두 번째 매개 변수는 행 구성 요소 이며, 세 번째 매개 변수는 열 구성 요소입니다. 출력은 8입니다.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent 클래스

[익스텐트 클래스](../../parallel/amp/reference/extent-class.md) 는 또는 개체의 각 차원에 있는 데이터의 길이를 지정 합니다 `array` `array_view` . 익스텐트를 만든 다음이를 사용 하 여 또는 개체를 만들 수 있습니다 `array` `array_view` . 기존 또는 개체의 범위를 검색할 수도 있습니다 `array` `array_view` . 다음 예에서는 개체의 각 차원에서 익스텐트의 길이를 인쇄 합니다 `array_view` .

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

다음 예제에서는 `array_view` 이전 예제에서 개체와 크기가 같은 개체를 만들지만이 예제에서는 `extent` 생성자에서 명시적 매개 변수를 사용 하는 대신 개체를 사용 합니다 `array_view` .

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>액셀러레이터로 데이터 이동: array 및 array_view

데이터를 액셀러레이터 키로 이동 하는 데 사용 되는 두 개의 데이터 컨테이너는 런타임 라이브러리에 정의 됩니다. [배열 클래스](../../parallel/amp/reference/array-class.md) 와 [array_view 클래스](../../parallel/amp/reference/array-view-class.md)입니다. `array`클래스는 개체가 생성 될 때 데이터의 전체 복사본을 만드는 컨테이너 클래스입니다. `array_view`클래스는 커널 함수가 데이터에 액세스할 때 데이터를 복사 하는 래퍼 클래스입니다. 원본 장치에서 데이터가 필요한 경우에는 데이터가 다시 복사 됩니다.

### <a name="array-class"></a>array 클래스

개체를 `array` 생성 하면 데이터 집합에 대 한 포인터를 포함 하는 생성자를 사용 하는 경우 데이터의 전체 복사본이 액셀러레이터에 생성 됩니다. Kernel 함수는 액셀러레이터의 복사본을 수정 합니다. 커널 함수 실행이 완료 되 면 데이터를 원본 데이터 구조로 다시 복사 해야 합니다. 다음 예제에서는 벡터의 각 요소를 10으로 곱합니다. 커널 함수를 완료 한 후에는를 `vector conversion operator` 사용 하 여 데이터를 벡터 개체에 다시 복사 합니다.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view 클래스

에는 `array_view` 클래스와 거의 같은 멤버가 `array` 있지만 기본 동작은 동일 하지 않습니다. 생성자에 전달 된 데이터는 생성자를 사용 하는 것 `array_view` 처럼 GPU에서 복제 되지 않습니다 `array` . 대신 커널 함수를 실행할 때 데이터가 액셀러레이터 키에 복사 됩니다. 따라서 `array_view` 동일한 데이터를 사용 하는 두 개체를 만드는 경우 두 `array_view` 개체가 동일한 메모리 공간을 참조 합니다. 이렇게 하면 다중 스레드 액세스를 동기화 해야 합니다. 클래스를 사용할 경우의 주요 이점은 `array_view` 필요한 경우에만 데이터가 이동 된다는 것입니다.

### <a name="comparison-of-array-and-array_view"></a>array와 array_view 비교

다음 표에서는 및 클래스 간의 유사점과 차이점을 요약 하 여 보여 줍니다 `array` `array_view` .

|Description|array 클래스|array_view 클래스|
|-----------------|-----------------|-----------------------|
|Rank가 결정 된 경우|컴파일 시간에.|컴파일 시간에.|
|범위가 결정 되 면|런타임에.|런타임에.|
|셰이프|모양의.|모양의.|
|데이터 스토리지|는 데이터 컨테이너입니다.|는 데이터 래퍼입니다.|
|복사|정의의 명시적 및 전체 복사본입니다.|커널 함수에서 액세스할 때의 암시적 복사입니다.|
|데이터 검색|CPU 스레드의 개체에 배열 데이터를 다시 복사 합니다.|개체에 대 한 직접 액세스 `array_view` 또는 [array_view:: synchronize 메서드](reference/array-view-class.md#synchronize) 를 호출 하 여 원래 컨테이너의 데이터에 계속 액세스 합니다.|

### <a name="shared-memory-with-array-and-array_view"></a>배열 및 array_view 공유 메모리

공유 메모리는 CPU와 가속기 모두에서 액세스할 수 있는 메모리입니다. 공유 메모리를 사용 하면 CPU와 가속기 간에 데이터를 복사 하는 오버 헤드가 감소 하거나 크게 줄어듭니다. 메모리가 공유 되더라도 CPU와 가속기 모두 동시에 액세스할 수 없으며, 이렇게 하면 정의 되지 않은 동작이 발생 합니다.

`array` 개체를 사용 하 여 연결 된 가속기가 지 원하는 경우 공유 메모리 사용에 대 한 세분화 된 제어를 지정할 수 있습니다. 액셀러레이터 키가 공유 메모리를 지원 하는지 여부는 [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) **`true`** 공유 메모리가 지원 될 때 반환 되는 액셀러레이터의 supports_cpu_shared_memory 속성에 의해 결정 됩니다. 공유 메모리가 지원 되는 경우 액셀러레이터에 대 한 메모리 할당에 대 한 기본 [Access_type 열거형](reference/concurrency-namespace-enums-amp.md#access_type) 은 속성에 의해 결정 됩니다 `default_cpu_access_type` . 기본적으로 `array` 및 `array_view` 개체는 연결 된 `access_type` 기본와 동일 하 게 사용 `accelerator` 됩니다.

의 [array:: Cpu_access_type 데이터 멤버](reference/array-class.md#cpu_access_type) 속성을 `array` 명시적으로 설정 하면 공유 메모리가 사용 되는 방식에 대 한 세분화 된 제어를 실행 하 여 계산 커널의 메모리 액세스 패턴에 따라 하드웨어의 성능 특성에 맞게 앱을 최적화할 수 있습니다. 는 `array_view` 연결 된와 동일한를 반영 `cpu_access_type` `array` 하거나, array_view 데이터 소스 없이 생성 된 경우에는 `access_type` 먼저 저장소를 할당 하도록 하는 환경을 반영 합니다. 즉, 호스트 (CPU)에서 처음으로 액세스 하는 경우에는 CPU 데이터 소스에 대해 생성 된 것 처럼 동작 하 고 캡처와 연결 된의를 공유 합니다. 그러나에서 처음으로 액세스 하는 경우에는에서 `access_type` `accelerator_view` 만든에 `accelerator_view` 대해 만들어진 것 처럼 동작 하 `array` `accelerator_view` 고의를 공유 합니다 `array` `access_type` .

다음 코드 예제에서는 기본 가속기에서 공유 메모리를 지원 하는지 여부를 확인 하는 방법을 보여 줍니다. 그러면 cpu_access_type 구성이 서로 다른 여러 배열이 생성 됩니다.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>데이터에 대해 코드 실행: parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 함수는 또는 개체의 데이터에 대해 액셀러레이터 키에서 실행 하려는 코드를 정의 합니다 `array` `array_view` . 이 항목의 소개 부분에서 다음 코드를 고려 합니다.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

`parallel_for_each`메서드는 계산 도메인 및 람다 식의 두 인수를 사용 합니다.

*계산 도메인* 은 `extent` `tiled_extent` 병렬 실행을 위해 만들 스레드 집합을 정의 하는 개체 또는 개체입니다. 계산 도메인의 각 요소에 대해 하나의 스레드가 생성 됩니다. 이 경우 `extent` 개체는 1 차원 이며 5 개의 요소가 있습니다. 따라서 5 개의 스레드가 시작 됩니다.

*람다 식은* 각 스레드에서 실행할 코드를 정의 합니다. 캡처 절은 `[=]` 람다 식의 본문이 캡처된 모든 변수에 값으로 액세스 하도록 지정 합니다 .이 경우에는, `a` `b` 및 `sum` 입니다. 이 예에서 매개 변수 목록은 라는 1 차원 변수를 만듭니다 `index` `idx` . 의 값은 `idx[0]` 첫 번째 스레드에서 0이 고 각 후속 스레드에서 1 씩 늘어납니다. 는 `restrict(amp)` C++ AMP 가속화 될 수 있는 c + + 언어의 하위 집합만 사용 됨을 나타냅니다.  Restrict 한정자가 있는 함수에 대 한 제한 사항은 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)에 설명 되어 있습니다. 자세한 내용은 [람다 식 구문](../../cpp/lambda-expression-syntax.md)을 참조 하세요.

람다 식은 실행할 코드를 포함 하거나 별도의 커널 함수를 호출할 수 있습니다. 커널 함수는 한정자를 포함 해야 합니다 `restrict(amp)` . 다음 예제는 이전 예제와 동일 하지만 별도의 커널 함수를 호출 합니다.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>가속 코드: 타일 및 장벽

바둑판식 배열을 사용 하 여 추가 가속을 얻을 수 있습니다. 바둑판식 배열은 스레드를 동일한 사각형 하위 집합 또는 *타일로* 나눕니다. 코딩 하는 알고리즘 및 데이터 집합에 따라 적절 한 타일 크기를 결정 합니다. 각 스레드에 대해 전체를 기준으로 하는 데이터 요소의 *전역* 위치에 액세스 하 `array` `array_view` 고 타일을 기준으로 *로컬* 위치에 액세스할 수 있습니다. 로컬 인덱스 값을 사용 하면 인덱스 값을 전역에서 로컬으로 변환 하는 코드를 작성할 필요가 없기 때문에 코드가 간단해 집니다. 바둑판식 배열을 사용 하려면 메서드에서 compute 도메인에 대해 [익스텐트:: Tile 메서드](reference/extent-class.md#tile) 를 호출 하 `parallel_for_each` 고 람다 식에 [tiled_index](../../parallel/amp/reference/tiled-index-class.md) 개체를 사용 합니다.

일반적인 응용 프로그램에서 타일의 요소는 어떤 방식으로든 관련 되며, 코드는 타일 전체에서 값을 액세스 하 고 추적 해야 합니다. [Tile_static 키워드](../../cpp/tile-static-keyword.md) 키워드 및 [tile_barrier:: wait 메서드](reference/tile-barrier-class.md#wait) 를 사용 하 여이 작업을 수행 합니다. **Tile_static** 키워드를 포함 하는 변수는 전체 타일에서 범위를 가지 며 각 타일에 대해 변수의 인스턴스가 생성 됩니다. 변수에 대 한 타일 스레드 액세스의 동기화를 처리 해야 합니다. [Tile_barrier:: Wait 메서드](reference/tile-barrier-class.md#wait) 는 타일의 모든 스레드가에 대 한 호출에 도달할 때까지 현재 스레드의 실행을 중지 합니다 `tile_barrier::wait` . 따라서 **tile_static** 변수를 사용 하 여 타일에서 값을 누적 시킬 수 있습니다. 그런 다음 모든 값에 액세스 해야 하는 모든 계산을 완료할 수 있습니다.

다음 다이어그램은 타일로 정렬 된 샘플링 데이터의 2 차원 배열을 나타냅니다.

![바둑판식 범위의 인덱스 값](../../parallel/amp/media/camptiledgridexample.png "바둑판식 범위의 인덱스 값")

다음 코드 예제에서는 이전 다이어그램의 샘플링 데이터를 사용 합니다. 이 코드는 타일의 각 값을 타일에 있는 값의 평균으로 바꿉니다.

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
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>수학 라이브러리

C++ AMP는 두 가지 수학 라이브러리를 포함 합니다. [Concurrency::p Recise_math 네임 스페이스](../../parallel/amp/reference/concurrency-precise-math-namespace.md) 의 배정밀도 라이브러리는 배정밀도 함수를 지원 합니다. 하드웨어에 대 한 배정밀도 지원이 여전히 필요 하지만 단 정밀도 함수를 지원 합니다. [C99 사양 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887)을 준수 합니다. 액셀러레이터는 완전 한 배정밀도를 지원 해야 합니다. [Accelerator:: Supports_double_precision 데이터 멤버](reference/accelerator-class.md#supports_double_precision)의 값을 확인 하 여 수행 여부를 결정할 수 있습니다. [Concurrency:: Fast_math 네임 스페이스](../../parallel/amp/reference/concurrency-fast-math-namespace.md)의 fast math 라이브러리에는 다른 수학 함수 집합이 포함 되어 있습니다. 피연산자만 지 원하는 이러한 함수는 **`float`** 보다 빠르게 실행 되지만 배정밀도 수학 라이브러리의 함수 만큼 정확 하지는 않습니다. 함수는 헤더 파일에 포함 되 \<amp_math.h> 고 모든 함수는로 선언 됩니다 `restrict(amp)` . 헤더 파일의 함수는 \<cmath> `fast_math` 및 `precise_math` 네임 스페이스로 모두 가져옵니다. **`restrict`** 키워드는 \<cmath> 버전과 C++ AMP 버전을 구분 하는 데 사용 됩니다. 다음 코드는 compute 도메인에 있는 각 값에 대해 fast 메서드를 사용 하 여 밑이 10 인 로그를 계산 합니다.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>그래픽 라이브러리

C++ AMP는 가속 그래픽 프로그래밍을 위해 디자인 된 그래픽 라이브러리를 포함 합니다. 이 라이브러리는 기본 그래픽 기능을 지 원하는 장치 에서만 사용 됩니다. 메서드는 [Concurrency:: Graphics 네임 스페이스](../../parallel/amp/reference/concurrency-graphics-namespace.md) 에 있으며 헤더 파일에 포함 되어 있습니다 \<amp_graphics.h> . 그래픽 라이브러리의 주요 구성 요소는 다음과 같습니다.

- [질감 클래스](../../parallel/amp/reference/texture-class.md): 질감 클래스를 사용 하 여 메모리 또는 파일에서 질감을 만들 수 있습니다. 질감은 데이터를 포함 하 고 있으며 할당 및 복사 생성과 관련 하 여 c + + 표준 라이브러리의 컨테이너와 유사 하기 때문에 배열과 비슷합니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../../standard-library/stl-containers.md)를 참조하세요. 클래스에 대 한 템플릿 매개 변수는 `texture` 요소 형식 및 순위입니다. 순위는 1, 2 또는 3 일 수 있습니다. 요소 형식은이 문서의 뒷부분에서 설명 하는 짧은 벡터 형식 중 하나일 수 있습니다.

- [Writeonly_texture_view 클래스](../../parallel/amp/reference/writeonly-texture-view-class.md): 질감에 대 한 쓰기 전용 액세스를 제공 합니다.

- Short vector Library: **`int`** ,, `uint` **`float`** , **`double`** , 일반 또는 [unorm](../../parallel/amp/reference/unorm-class.md) [norm](../../parallel/amp/reference/norm-class.md)을 기반으로 하는 길이 2, 3 및 4의 짧은 벡터 형식 집합을 정의 합니다.

## <a name="universal-windows-platform-uwp-apps"></a>UWP(유니버설 Windows 플랫폼) 앱

다른 c + + 라이브러리와 마찬가지로 UWP 앱에서 C++ AMP를 사용할 수 있습니다. 이러한 문서에서는 c + +, c #, Visual Basic 또는 JavaScript를 사용 하 여 만든 앱에 C++ AMP 코드를 포함 하는 방법을 설명 합니다.

- [UWP 앱에서 C++ AMP 사용](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [연습: c + +에서 기본 Windows 런타임 구성 요소 만들기 및 JavaScript에서 호출](/previous-versions/windows/apps/hh755833(v=vs.140))

- [JavaScript 및 c + +의 Window 스토어 앱 인 Bing 지도 여행 최적화 프로그램](/previous-versions/windows/apps/hh699893(v=vs.140))

- [Windows 런타임를 사용 하 여 c #에서 C++ AMP를 사용 하는 방법](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [C에서 C++ AMP를 사용 하는 방법 #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [관리 코드에서 네이티브 함수 호출](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP 및 동시성 시각화 도우미

동시성 시각화 도우미에는 C++ AMP 코드의 성능 분석에 대 한 지원이 포함 되어 있습니다. 다음 문서에서는 이러한 기능에 대해 설명 합니다.

- [GPU 작업 그래프](/visualstudio/profiling/gpu-activity-graph)

- [GPU 작업(페이징)](/visualstudio/profiling/gpu-activity-paging)

- [GPU 작업(이 프로세스)](/visualstudio/profiling/gpu-activity-this-process)

- [GPU 작업(다른 프로세스)](/visualstudio/profiling/gpu-activity-other-processes)

- [채널(스레드 뷰)](/visualstudio/profiling/channels-threads-view)

- [동시성 시각화 도우미를 사용 하 여 C++ AMP 코드 분석](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>성능 권장 사항

부호 없는 정수의 모듈러스 및 나누기는 부호 있는 정수의 모듈러스 및 나누기 보다 성능이 훨씬 뛰어납니다. 가능 하면 부호 없는 정수를 사용 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[C++ AMP(C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[람다 식 구문](../../cpp/lambda-expression-syntax.md)<br/>
[참조(C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[네이티브 코드 블로그의 병렬 프로그래밍](/archive/blogs/nativeconcurrency/)

---
description: '자세한 정보: accelerator 및 accelerator_view 개체 사용'
title: accelerator 및 accelerator_view 개체 사용
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 270b517764b8060efbaea9d00c20e24aa1746818
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314492"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>accelerator 및 accelerator_view 개체 사용

[액셀러레이터 키](../../parallel/amp/reference/accelerator-class.md) 및 [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) 클래스를 사용 하 여 C++ AMP 코드를 실행할 장치 또는 에뮬레이터를 지정할 수 있습니다. 시스템에는 메모리 양, 공유 메모리 지원, 디버깅 지원 또는 배정밀도 지원과 같은 여러 장치나 에뮬레이터가 있을 수 있습니다. C++ Accelerated Massive Parallelism (C++ AMP)는 사용 가능한 액셀러레이터를 검사 하 고,이를 기본값으로 설정 하 고, parallel_for_each에 대 한 여러 호출에 여러 accelerator_views을 지정 하 고, 특수 디버깅 작업을 수행할 수 있는 Api를 제공 합니다.

## <a name="using-the-default-accelerator"></a>기본 액셀러레이터 키 사용

특정 항목을 선택 하는 코드를 작성 하지 않은 경우 C++ AMP 런타임은 기본 액셀러레이터를 선택 합니다. 런타임은 다음과 같이 기본 액셀러레이터를 선택 합니다.

1. 응용 프로그램이 디버그 모드에서 실행 되는 경우 디버깅을 지 원하는 액셀러레이터입니다.

2. 그렇지 않으면 CPPAMP_DEFAULT_ACCELERATOR 환경 변수로 지정 된 액셀러레이터 (설정 된 경우)입니다.

3. 그렇지 않은 경우에는 에뮬레이트된 장치가 아닙니다.

4. 그렇지 않으면 사용 가능한 메모리가 가장 많은 장치입니다.

5. 그렇지 않으면 디스플레이에 연결 되지 않은 장치입니다.

또한 런타임은 `access_type` `access_type_auto` 기본 액셀러레이터에 대 한의를 지정 합니다. 이는 기본 가속기가 지원 되는 경우 공유 메모리를 사용 하 고 성능 특성 (대역폭 및 대기 시간)을 전용 (비공유) 메모리와 동일 하 게 알고 있음을 의미 합니다.

기본 액셀러레이터 키를 생성 하 고 해당 속성을 검사 하 여 기본 액셀러레이터의 속성을 확인할 수 있습니다. 다음 코드 예제에서는 경로, 액셀러레이터 메모리의 양, 공유 메모리 지원, 배정밀도 지원, 기본 액셀러레이터의 제한 된 배정밀도 지원 등을 인쇄 합니다.

```cpp
void default_properties() {
    accelerator default_acc;
    std::wcout << default_acc.device_path << "\n";
    std::wcout << default_acc.dedicated_memory << "\n";
    std::wcout << (accs[i].supports_cpu_shared_memory ?
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";
    std::wcout << (accs[i].supports_double_precision ?
        "double precision: true" : "double precision: false") << "\n";
    std::wcout << (accs[i].supports_limited_double_precision ?
        "limited double precision: true" : "limited double precision: false") << "\n";
}
```

### <a name="cppamp_default_accelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 환경 변수

CPPAMP_DEFAULT_ACCELERATOR 환경 변수를 설정 하 여 기본 액셀러레이터의를 지정할 수 있습니다 `accelerator::device_path` . 하드웨어에 종속 된 경로입니다. 다음 코드에서는 함수를 사용 하 여 `accelerator::get_all` 사용 가능한 액셀러레이터 목록을 검색 한 다음 각 액셀러레이터의 경로 및 특성을 표시 합니다.

```cpp
void list_all_accelerators()
{
    std::vector<accelerator> accs = accelerator::get_all();

    for (int i = 0; i <accs.size(); i++) {
        std::wcout << accs[i].device_path << "\n";
        std::wcout << accs[i].dedicated_memory << "\n";
        std::wcout << (accs[i].supports_cpu_shared_memory ?
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";
        std::wcout << (accs[i].supports_double_precision ?
            "double precision: true" : "double precision: false") << "\n";
        std::wcout << (accs[i].supports_limited_double_precision ?
            "limited double precision: true" : "limited double precision: false") << "\n";
    }
}
```

## <a name="selecting-an-accelerator"></a>액셀러레이터 키 선택

액셀러레이터 키를 선택 하려면 메서드를 사용 하 여 `accelerator::get_all` 사용 가능한 액셀러레이터 목록을 검색 한 다음 속성에 따라 하나를 선택 합니다. 이 예제에서는 메모리가 가장 많은 액셀러레이터를 선택 하는 방법을 보여 줍니다.

```cpp
void pick_with_most_memory()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];

    for (int i = 0; i <accs.size(); i++) {
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {
            acc_chosen = accs[i];
        }
    }

    std::wcout << "The accelerator with the most memory is "
        << acc_chosen.device_path << "\n"
        << acc_chosen.dedicated_memory << ".\n";
}
```

> [!NOTE]
> 에서 반환 하는 액셀러레이터 중 하나가 `accelerator::get_all` CPU 가속기입니다. CPU 가속기에서 코드를 실행할 수 없습니다. CPU 가속기를 필터링 하려면에서 반환 하는 액셀러레이터의 [device_path](reference/accelerator-class.md#device_path) 속성 값을 `accelerator::get_all` [accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)의 값과 비교 합니다. 자세한 내용은이 문서의 "특수 액셀러레이터" 섹션을 참조 하세요.

## <a name="shared-memory"></a>공유 메모리

공유 메모리는 CPU와 가속기 모두에서 액세스할 수 있는 메모리입니다. 공유 메모리를 사용 하면 CPU와 가속기 간에 데이터를 복사 하는 오버 헤드가 감소 하거나 크게 줄어듭니다. 메모리가 공유 되더라도 CPU와 가속기 모두 동시에 액세스할 수 없으며, 이렇게 하면 정의 되지 않은 동작이 발생 합니다. 액셀러레이터 키 [](reference/accelerator-class.md#supports_cpu_shared_memory) **`true`** 가 공유 메모리를 지원 하 고 [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) 속성이에 할당 된 메모리에 대 한 기본 [access_type](reference/concurrency-namespace-enums-amp.md#access_type) 를 가져옵니다. 예를 들어,에 할당 된 메모리에 대 한 기본을 가져옵니다 `accelerator`  `accelerator` `array_view` `accelerator` . supports_cpu_shared_memory

C++ AMP 런타임은 각각에 대해 가장 적합 한 기본값을 자동으로 선택 `access_type` `accelerator` 하지만 공유 메모리의 성능 특성 (대역폭 및 대기 시간)은 cpu에서 읽거나 cpu에서 쓰거나 둘 다를 수행할 때 전용 (비공유) 가속기 메모리의 성능 특성 보다 낮을 수 있습니다. 공유 메모리와 CPU에서 읽기 및 쓰기를 위한 전용 메모리가 모두 사용 되는 경우 런타임은 기본적으로로 설정 되 고 `access_type_read_write` , 그렇지 않으면 런타임에서 보다 보수적인 기본값을 선택 하 `access_type` 고 응용 프로그램에서 계산 커널의 메모리 액세스 패턴이 다른를 활용 하는 경우이를 재정의할 수 있습니다 `access_type` .

다음 코드 예제에서는 기본 액셀러레이터 키가 공유 메모리를 지원 하는지 여부를 확인 하 고 해당 기본 액세스 형식을 재정의 하 여이를 만드는 방법을 보여 줍니다 `accelerator_view` .

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
    acc.set_default_cpu_access_type(access_type_read_write);

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view reflects the default_cpu_access_type of the
    // accelerator it’s associated with.
    accelerator_view acc_v = acc.default_view;
}
```

는 `accelerator_view` 항상 연결 된의를 반영 `default_cpu_access_type` `accelerator` 하며를 재정의 하거나 변경 하는 인터페이스를 제공 하지 않습니다 `access_type` .

## <a name="changing-the-default-accelerator"></a>기본 액셀러레이터 키 변경

메서드를 호출 하 여 기본 액셀러레이터 키를 변경할 수 있습니다 `accelerator::set_default` . 기본 액셀러레이터는 앱 실행 당 한 번만 변경할 수 있으며 GPU에서 코드가 실행 되기 전에 변경 해야 합니다. 액셀러레이터 키 반환을 변경 하는 후속 함수 호출 **`false`** 입니다. 에 대 한 호출에서 다른 액셀러레이터를 사용 하려는 경우 `parallel_for_each` 이 문서의 "여러 액셀러레이터 사용" 섹션을 참조 하세요. 다음 코드 예제에서는 기본 액셀러레이터를 에뮬레이션 되지 않은 항목으로 설정 하 고, 표시에 연결 되지 않고, 배정밀도를 지원 합니다.

```cpp
bool pick_accelerator()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;

    auto result = std::find_if(accs.begin(), accs.end(),
        [] (const accelerator& acc) {
            return !acc.is_emulated &&
                acc.supports_double_precision &&
                !acc.has_display;
        });

    if (result != accs.end()) {
        chosen_one = *(result);
    }

    std::wcout <<chosen_one.description <<std::endl;
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;
}
```

## <a name="using-multiple-accelerators"></a>여러 액셀러레이터 사용

앱에서 여러 액셀러레이터를 사용 하는 방법에는 두 가지가 있습니다.

- [Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 메서드에 대한 호출에 `accelerator_view`개체를 전달할 수 있습니다.

- 특정 개체를 사용 하 여 **배열** 개체를 생성할 수 있습니다 `accelerator_view` . C + AMP 런타임은 `accelerator_view` 람다 식의 캡처된 **배열** 개체에서 개체를 선택 합니다.

## <a name="special-accelerators"></a>특수 액셀러레이터

세 가지 특수 한 액셀러레이터의 장치 경로는 클래스의 속성으로 사용할 수 있습니다 `accelerator` .

- [accelerator::d Irect3d_ref 데이터 멤버](reference/accelerator-class.md#direct3d_ref):이 단일 스레드 가속기는 CPU의 소프트웨어를 사용 하 여 일반 그래픽 카드를 에뮬레이션 합니다. 기본적으로 디버깅에 사용 되지만 하드웨어 가속기 보다 속도가 느리므로 프로덕션에서는 유용 하지 않습니다. 또한 DirectX SDK 및 Windows SDK 에서만 사용할 수 있으며, 고객의 컴퓨터에 설치 될 가능성은 거의 없습니다. 자세한 내용은 [GPU 코드 디버깅](/visualstudio/debugger/debugging-gpu-code)을 참조하세요.

- [accelerator::d Irect3d_warp 데이터 멤버](reference/accelerator-class.md#direct3d_warp):이 액셀러레이터는 SSE (스트리밍 SIMD 확장)를 사용 하는 다중 코어 cpu에서 C++ AMP 코드를 실행 하기 위한 대체 (fallback) 솔루션을 제공 합니다.

- [accelerator:: Cpu_accelerator 데이터 멤버](reference/accelerator-class.md#cpu_accelerator):이 액셀러레이터를 사용 하 여 준비 배열을 설정할 수 있습니다. C++ AMP 코드를 실행할 수 없습니다. 자세한 내용은 네이티브 코드의 병렬 프로그래밍 블로그의 C++ AMP 게시물에서 [준비 배열](/archive/blogs/nativeconcurrency/staging-arrays-in-c-amp) 을 참조 하세요.

## <a name="interoperability"></a>상호 운용성

C++ AMP 런타임은 `accelerator_view` 클래스와 Direct3D [ID3D11Device 인터페이스](/windows/win32/api/d3d11/nn-d3d11-id3d11device)간의 상호 운용성을 지원 합니다. [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) 메서드는 인터페이스를 사용 `IUnknown` 하 고 개체를 반환 합니다 `accelerator_view` . [Get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) 메서드는 개체를 사용 `accelerator_view` 하 여 인터페이스를 반환 합니다 `IUnknown` .

## <a name="see-also"></a>참고 항목

[C++ AMP(C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[GPU 코드 디버그](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view 클래스](../../parallel/amp/reference/accelerator-view-class.md)

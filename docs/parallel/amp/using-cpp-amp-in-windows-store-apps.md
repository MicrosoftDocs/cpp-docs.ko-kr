---
description: '자세한 정보: UWP 앱에서 C++ AMP 사용'
title: UWP 앱에서 C++ AMP 사용
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 91c7b147ff89a1fe19ebe1b18e465533053542d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314479"
---
# <a name="using-c-amp-in-uwp-apps"></a>UWP 앱에서 C++ AMP 사용

UWP (유니버설 Windows 플랫폼) 앱에서 C++ AMP (C++ Accelerated Massive Parallelism)를 사용 하 여 GPU (그래픽 처리 장치) 또는 기타 계산 액셀러레이터에 대 한 계산을 수행할 수 있습니다. 그러나, C++ AMP는 Windows Runtime 형식으로 직접 작업하기 위한 API를 제공하지 않으며, Windows 런타임은 C++ AMP에 대한 래퍼를 제공하지 않습니다. 코드(본인이 직접 만든 형식 포함)에 Windows 런타임 형식을 사용할 경우 C++ AMP와 호환되는 형식으로 변환해야 합니다.

## <a name="performance-considerations"></a>성능 고려 사항

Visual C++ 구성 요소 확장 c + +/CX를 사용 하 여 UWP (유니버설 Windows 플랫폼) 앱을 만드는 경우 `std::vector` C++ AMP와 함께 사용 되는 데이터에 대해 연속 저장소 (예: 또는 C 스타일 배열)와 함께 POD (일반-이전 데이터) 형식을 사용 하는 것이 좋습니다. 이렇게 하면 마샬링을 수행할 필요가 없기 때문에 비 POD 형식 또는 Windows RT 컨테이너를 사용 하는 것 보다 성능을 향상 시킬 수 있습니다.

C++ AMP 커널에서 이러한 방식으로 저장 된 데이터에 액세스 하려면 `std::vector` 또는 배열 저장소를에 래핑하고 `concurrency::array_view` 루프에서 배열 뷰를 사용 하면 됩니다 `concurrency::parallel_for_each` .

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Windows 런타임 형식 마샬링

Windows 런타임 Api를 사용 하는 경우 `Platform::Array<T>^` **ref** 키워드나 **value** 키워드를 사용 하 여 선언 된 클래스 또는 구조체와 같은 복잡 한 데이터 형식 또는와 같은 Windows 런타임 컨테이너에 저장 된 데이터에 대 한 C++ AMP를 사용할 수 있습니다. 이러한 상황에서는 데이터를 C++ AMP 사용할 수 있도록 하기 위해 몇 가지 추가 작업을 수행 해야 합니다.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: Array \<T> ^, 여기서 T는 POD 형식입니다.

이 발생 하 `Platform::Array<T>^` 고 T가 POD 형식이 면 멤버 함수를 사용 하 여 기본 저장소에 액세스할 수 있습니다 `get` .

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

T가 POD 형식이 아닌 경우에는 다음 섹션에 설명 된 기술을 사용 하 여 C++ AMP 데이터를 사용 합니다.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows 런타임 형식: ref 클래스 및 값 클래스

C++ AMP은 복합 데이터 형식을 지원 하지 않습니다. 여기에는 비 POD 형식 및 **ref** 키워드나 **value** 키워드를 사용 하 여 선언 된 모든 형식이 포함 됩니다. 컨텍스트에서 지원 되지 않는 형식을 사용 하는 경우 `restrict(amp)` 컴파일 타임 오류가 생성 됩니다.

지원 되지 않는 형식이 발생 하는 경우 해당 데이터의 흥미로운 부분을 개체로 복사할 수 있습니다 `concurrency::array` . 이 수동 복사 방법은 데이터를 C++ AMP 사용할 수 있도록 하는 것 외에도 데이터 집약성을 극대화 하 고 사용 되지 않는 데이터가 액셀러레이터 키에 복사 되지 않도록 하 여 성능을 향상 시킬 수 있습니다. *준비 배열을* 사용 하 여 성능을 향상 시킬 수 있습니다 .이 배열을 사용 하 여 `concurrency::array` 지정 된 액셀러레이터의 다른 배열 간에 자주 전송 하도록 배열을 최적화 해야 함을 AMP 런타임에 힌트를 제공 합니다.

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>참고 항목

[C + +를 사용 하 여 첫 번째 UWP 앱 만들기](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[C++로 Windows Runtime 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)

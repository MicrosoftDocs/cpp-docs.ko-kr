---
title: 그래픽(C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 97fd433387aac809053ea6dd8ac59a56207a4fc8
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344724"
---
# <a name="graphics-c-amp"></a>그래픽(C++ AMP)

C++ AMP에는 [Concurrency:: graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) 네임 스페이스의 몇 가지 api가 포함 되어 있으며,이 api를 사용 하 여 gpu에서 질감 지원에 액세스할 수 있습니다. 몇 가지 일반적인 시나리오는 다음과 같습니다.

- [질감](../../parallel/amp/reference/texture-class.md) 클래스를 계산에 대 한 데이터 컨테이너로 사용 하 고 질감 캐시의 *공간* 위치 및 GPU 하드웨어의 레이아웃을 활용할 수 있습니다. 공간 집약성은 물리적으로 서로 인접한 데이터 요소의 속성입니다.

- 런타임에서 비컴퓨팅 셰이더와의 효율적인 상호 운용성을 제공합니다. 픽셀, 꼭짓점, 공간 분할(tessellation) 및 헐 셰이더는 C++ AMP 계산에 사용할 수 있는 텍스처를 자주 사용하거나 생성합니다.

- C++ AMP의 그래픽 API가 sub-word 압축 버퍼에 액세스하는 다른 방법을 제공합니다. 8 비트 또는 16 비트 스칼라 구성 된 *텍셀* (질감 요소)를 나타내는 형식이 있는 질감은 이러한 압축 된 데이터 저장소에 대 한 액세스를 허용 합니다.

## <a name="the-norm-and-unorm-types"></a>norm 및 unorm 형식

`norm`및 `unorm` 형식은 값의 범위를 제한 하는 스칼라 형식 **`float`** 입니다 .이를 *고정* 라고 합니다. 이러한 형식은 다른 스칼라 형식에서 명시적으로 생성될 수 있습니다. 캐스팅에서 값은 먼저로 캐스팅 된 **`float`** 다음 일반 [-1.0, 1.0] 또는 unorm [0.0, 1.0]에서 허용 하는 해당 지역으로 고정 됩니다. +/- 무한대에서 캐스팅하는 경우 +/-1이 반환됩니다. NaN에서의 캐스팅은 정의되지 않았습니다. norm은 unorm에서 암시적으로 생성될 수 있으며 데이터는 손실되지 않습니다. 이러한 형식에는 float로의 암시적 변환 연산자가 정의되어 있습니다. 이항 연산자는 이러한 형식과 및와 같은 기타 기본 제공 스칼라 형식 ( **`float`** **`int`** +,-, \* ,/, = =,! =, >, \<, > =, <=) 사이에 정의 됩니다. 복합 할당 연산자 (+ =,-=, \* =,/=)도 지원 됩니다. norm 형식에 대해서는 단항 부정 연산자(-)가 정의되어 있습니다.

## <a name="short-vector-library"></a>short 벡터 라이브러리

Short Vector 라이브러리는 HLSL에 정의 된 [Vector 형식의](/windows/win32/direct3dhlsl/dx-graphics-hlsl-vector) 일부 기능을 제공 하며 일반적으로 텍셀를 정의 하는 데 사용 됩니다. short 벡터는 동일한 형식의 값을 1~4개 포함하는 데이터 구조입니다. 지원 되는 형식은 **`double`** , **`float`** , **`int`** , `norm` , `uint` 및 `unorm` 입니다. 다음 표에는 형식 이름이 나와 있습니다. 각 형식에 대해 **`typedef`** 이름에 밑줄이 없는 해당도 있습니다. 밑줄이 있는 형식은 [Concurrency:: Graphics 네임 스페이스](../../parallel/amp/reference/concurrency-graphics-namespace.md)에 있습니다. 밑줄이 없는 형식은 [동시성:: graphics::d Irect3d 네임 스페이스](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) 에 포함 되어 **`__int8`** 있으며,와 같은 유사한 이름의 기본 형식에서 명확 하 게 구분 **`__int16`** 됩니다.

|유형|길이 2|길이 3|길이 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|Int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>연산자

두 short 벡터 간에 연산자가 정의되면 short 벡터와 스칼라 간에도 연산자가 정의됩니다. 또한 다음 조건 중 하나가 충족되어야 합니다.

- 스칼라 형식이 short 벡터의 요소 형식과 동일해야 합니다.

- 스칼라 형식이 하나의 사용자 정의 변환만 사용하여 벡터의 요소 형식으로 변환될 수 있습니다.

연산은 short 벡터의 각 구성 요소와 스칼라 간에 구성 요소 수준에서 수행됩니다. 다음은 유효한 연산자입니다.

|연산자 유형|유효한 유형|
|-------------------|-----------------|
|이항 연산자|모든 형식에 대해 유효함: +,-, \* ,/,<br /><br /> 정수 형식에 대해 유효함:%, ^, &#124;, &, <\<, >><br /><br /> 두 벡터의 크기가 동일해야 하고 결과는 동일한 크기의 벡터여야 합니다.|
|관계형 연산자|모든 형식에 대해 유효함: == 및 !=|
|복합 할당 연산자|모든 형식에 대해 유효함: + =,-=, \* =,/=<br /><br /> 정수 형식에 대해 유효함:% =, ^ =, &#124;=, &=, <\<=, >>=|
|증가 및 감소 연산자|모든 형식에 대해 유효함: ++, --<br /><br /> 전위와 후위가 모두 유효해야 합니다.|
|비트 NOT 연산자(~)|정수 형식에 대해 유효함|
|단항 연산자|`unorm` 및 `uint`을 제외한 모든 형식에 대해 유효함|

### <a name="swizzling-expressions"></a>재구성 식

short 벡터 라이브러리는 short 벡터의 구성 요소에 액세스할 수 있도록 `vector_type.identifier` 접근자 구문을 지원합니다. `identifier` *재구성 식* 이라고 하는는 벡터의 구성 요소를 지정 합니다. 식은 l-value 또는 r-value일 수 있습니다. 식별자의 개별 문자는 x, y, z 및 w 일 수 있습니다. 또는 r, g, b 및 a입니다. "x"와 "r"은 0 번째 구성 요소를 의미 하 고, "y"와 "g"는 첫 번째 구성 요소를 의미 합니다. ("X"와 "r"은 동일한 식별자에 사용할 수 없습니다.) 따라서 "rgba" 및 "xyzw"는 동일한 결과를 반환 합니다. "x" 및 "y"와 같은 단일 구성 요소 접근자는 스칼라 값 형식입니다. 다중 구성 요소 접근자는 short 벡터 형식입니다. 예를 들어 2, 4, 6, 8 값을 가진 `int_4`라는 `fourInts` 벡터를 생성한 경우 `fourInts.y`는 정수 4를 반환하고 `fourInts.rg`는 2와 4 값을 가진 `int_2` 개체를 반환합니다.

## <a name="texture-classes"></a>Texture 클래스

대부분의 GPU에는 픽셀과 텍셀을 가져오고 이미지와 텍스처를 렌더링하는 데 최적화된 하드웨어 및 캐시가 있습니다. 텍셀 개체에 대 한 컨테이너 클래스인 [질감 \<T,N> ](../../parallel/amp/reference/texture-class.md) 클래스는 이러한 gpu의 질감 기능을 노출 합니다. 텍셀은 다음 형식일 수 있습니다.

- **`int`** ,, `uint` , **`float`** , **`double`** `norm` 또는 `unorm` 스칼라입니다.

- 구성 요소가 두 개 또는 네 개인 short 벡터. 유일한 예외는 `double_4`이며 이 형식은 허용되지 않습니다.

`texture` 개체의 차수는 1, 2 또는 3일 수 있습니다. `texture` 개체는 `parallel_for_each` 호출의 람다에 있는 참조를 통해서만 캡처될 수 있습니다. 텍스처는 Direct3D 텍스처 개체로 GPU에 저장됩니다. Direct3D의 질감 및 텍셀에 대 한 자세한 내용은 [direct3d 11의 질감 소개](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-intro)를 참조 하세요.

사용하는 텍셀 형식은 그래픽 프로그래밍에 사용되는 다양한 텍스처 형식 중 하나일 수 있습니다. 예를 들어 RGBA 형식은 R, G, B, A 스칼라 요소 각각에 8비트씩 총 32비트를 사용할 수 있습니다. 그래픽 카드의 텍스처 하드웨어는 형식에 따라 개별 요소에 액세스할 수 있습니다. 예를 들어 RGBA 형식을 사용하는 경우 텍스처 하드웨어는 각 8비트 요소를 32비트 형식으로 추출할 수 있습니다. C++ AMP에서는 텍셀의 스칼라 요소당 비트 수를 설정하여 비트 시프트를 사용하지 않고 코드의 개별 스칼라 요소에 자동으로 액세스할 수 있습니다.

### <a name="instantiating-texture-objects"></a>텍스처 개체 인스턴스화

텍스처 개체를 초기화하지 않고 선언할 수 있습니다. 다음 코드 예제에서는 여러 개의 텍스처 개체를 선언합니다.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

생성자를 사용하여 `texture` 개체를 선언하고 초기화할 수도 있습니다. 다음 코드 예제에서는 `texture` 개체의 벡터에서 `float_4` 개체를 인스턴스화합니다. 스칼라 요소당 비트 수는 기본값으로 설정됩니다. `norm`, `unorm`이나 `norm` 및 `unorm`의 short 벡터에는 스칼라 요소당 기본 비트 수가 없기 때문에 이 생성자를 사용할 수 없습니다.

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

소스 데이터에 대한 포인터, 소스 데이터의 크기(바이트) 및 스칼라 요소당 비트 수를 사용하는 생성자 오버로드를 사용하여 `texture` 개체를 선언하고 초기화할 수도 있습니다.

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

이러한 예에 나오는 텍스처는 기본 액셀러레이터의 기본 보기에 만들어집니다. `accelerator_view` 개체를 지정하려는 경우 생성자의 다른 오버로드를 사용할 수 있습니다. CPU 액셀러레이터에는 텍스처 개체를 만들 수 없습니다.

다음 표에 표시된 것과 같이 `texture` 개체의 각 차원에는 크기 제한이 있습니다. 제한을 초과할 경우 런타임 오류가 생성됩니다.

|질감|차원 당 크기 제한|
|-------------|---------------------|
|질감\<T,1>|16384|
|질감\<T,2>|16384|
|질감\<T,3>|2048|

### <a name="reading-from-texture-objects"></a>텍스처 개체에서 읽기

`texture` [텍스처: \[ \] : operator](reference/texture-class.md#operator_at), [텍스처:: operator () 연산자](reference/texture-class.md#operator_call)또는 [질감:: get 메서드](reference/texture-class.md#get)를 사용 하 여 개체에서 읽을 수 있습니다. 두 연산자는 참조가 아니라 값을 반환 합니다. 따라서 `texture`를 사용하여 `texture::operator\[\]` 개체에 쓸 수 없습니다.

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

다음 코드 예제에서는 텍스처 채널을 short 벡터에 저장한 다음 short 벡터의 속성으로 개별 스칼라 요소에 액세스하는 방법을 보여 줍니다.

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

다음 표에는 각 short 벡터 형식에 유효한 채널당 비트 수가 나와 있습니다.

|텍스처 데이터 형식|스칼라 요소당 유효한 비트 수|
|-----------------------|-----------------------------------|
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|
|int_3, uint_3|32|
|float, float_2, float_4|16, 32|
|float_3|32|
|double, double_2|64|
|norm, norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>텍스처 개체에 쓰기

[텍스처:: set](reference/texture-class.md#set) 메서드를 사용 하 여 개체에 씁니다 `texture` . 텍스처 개체는 읽기 전용 또는 읽기/쓰기일 수 있습니다. 텍스처 개체를 읽고 쓸 수 있으려면 다음 조건이 충족되어야 합니다.

- T에 스칼라 구성 요소가 하나만 있습니다. short 벡터는 허용되지 않습니다.

- T가 **`double`** , `norm` 또는이 아닌 `unorm` 경우

- `texture::bits_per_scalar_element` 속성이 32입니다.

세 가지 조건이 모두 충족되지 않으면 `texture` 개체가 읽기 전용입니다. 처음 두 조건은 컴파일하는 동안 확인됩니다. `readonly` 텍스처 개체에 쓰기를 시도하는 코드가 있으면 컴파일 오류가 생성됩니다. 의 조건은 `texture::bits_per_scalar_element` 런타임에 검색 되며 읽기 전용 개체에 쓰려고 하면 런타임에서 [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) 예외가 생성 됩니다 `texture` .

다음 코드 예제에서는 텍스처 개체에 값을 씁니다.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>텍스처 개체 복사

다음 코드 예제와 같이 [copy](reference/concurrency-namespace-functions-amp.md#copy) 함수 또는 [copy_async](reference/concurrency-namespace-functions-amp.md#copy_async) 함수를 사용 하 여 질감 개체 간에 복사할 수 있습니다.

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

[질감:: copy_to](reference/texture-class.md#copy_to) 메서드를 사용 하 여 한 질감에서 다른 질감으로 복사할 수도 있습니다. 두 텍스처가 서로 다른 액셀러레이터 보기에 있어도 됩니다. `writeonly_texture_view` 개체에 복사하는 경우 데이터가 내부 `texture` 개체에 복사됩니다. 소스 및 대상 `texture` 개체에서 스칼라 요소당 비트 수 및 범위가 동일해야 합니다. 이러한 요구 사항이 충족되지 않으면 런타임 예외가 throw됩니다.

## <a name="texture-view-classes"></a>텍스처 보기 클래스

C++ AMP Visual Studio 2013에서 [Texture_view 클래스](../../parallel/amp/reference/texture-view-class.md) 를 소개 합니다. 질감 보기는 질감 [클래스](../../parallel/amp/reference/texture-class.md)와 동일한 텍셀 형식 및 순위를 지원 하지만 텍스처와 달리 질감 샘플링 및 mip 맵을 같은 추가 하드웨어 기능에 대 한 액세스를 제공 합니다. 텍스처 보기는 내부 텍스처 데이터에 대한 읽기 전용, 쓰기 전용 및 읽기/쓰기 액세스를 지원합니다.

- 읽기 전용 액세스는 `texture_view<const T, N>` 템플릿 특수화를 통해 제공되며 구성 요소가 1, 2, 4개인 요소, 텍스처 샘플링, 보기가 인스턴스화될 때 결정되는 다양한 Mip 맵 수준에 대한 동적 액세스를 지원합니다.

- 쓰기 전용 액세스는 특수화되지 않은 템플릿 클래스 `texture_view<T, N>`을 통해 제공되며 구성 요소가 2개 또는 4개인 요소를 지원하고 보기가 인스턴스화될 때 결정되는 하나의 Mip 맵 수준에 액세스할 수 있습니다. 샘플링은 지원하지 않습니다.

- 읽기-쓰기 액세스는 특수화되지 않은 템플릿 클래스 `texture_view<T, N>`을 통해 제공되고 텍스처와 마찬가지로 구성 요소가 하나뿐인 요소를 지원하며 보기가 인스턴스화될 때 결정되는 하나의 Mip 맵 수준에 액세스할 수 있습니다. 샘플링은 지원하지 않습니다.

질감 보기는 배열 뷰와 유사 하지만 [Array_view 클래스가](../../parallel/amp/reference/array-view-class.md) [배열 클래스](../../parallel/amp/reference/array-class.md)를 통해 제공 하는 자동 데이터 관리 및 이동 기능을 제공 하지 않습니다. `texture_view`는 내부 텍스처 데이터가 있는 액셀러레이터 보기에서만 액세스할 수 있습니다.

### <a name="writeonly_texture_view-deprecated"></a>더 이상 사용되지 않는 writeonly_texture_view

Visual Studio 2013의 경우 C++ AMP는 [Writeonly_texture_view 클래스](../../parallel/amp/reference/writeonly-texture-view-class.md)에서 지원할 수 없는 샘플링 및 mip 맵을 같은 하드웨어 질감 기능에 대해 더 나은 지원을 제공 합니다. 새로 도입된 `texture_view` 클래스는 `writeonly_texture_view`에 있는 기능의 상위 집합을 지원하므로 `writeonly_texture_view`는 더 이상 사용되지 않습니다.

따라서 새로 작성하는 코드에서는 이전에 `texture_view`를 통해 제공되었던 기능에 액세스할 때 `writeonly_texture_view`를 사용하는 것이 좋습니다. 구성 요소가 두 개인 텍스처 개체(int_2)에 쓰는 다음 두 코드 예제를 비교해 보십시오. 두 예제 모두에서 `wo_tv4`라는 보기는 람다 식의 값을 통해 캡처되어야 합니다. 다음은 새 `texture_view` 클래스를 사용하는 예제입니다.

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

다음은 더 이상 사용되지 않는 `writeonly_texture_view` 클래스입니다.

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

두 예제에서 볼 수 있듯이 기본 Mip 맵 수준에 쓰는 것이 수행하려는 작업의 전부일 때는 두 코드 예제가 거의 동일합니다. 기존 코드에 `writeonly_texture_view`를 사용했고 코드를 더 효율적으로 바꿀 계획이 없는 경우 변경하지 않아도 됩니다. 하지만 코드를 개선하려는 경우에는 새로운 하드웨어 텍스처 기능을 지원하는 향상된 `texture_view`를 사용하도록 코드를 다시 작성하는 것이 좋습니다. 이러한 새로운 기능에 대한 자세한 내용을 보려면 이 문서를 끝까지 읽어보십시오.

사용 중단에 대 한 자세한 내용은 `writeonly_texture_view` 네이티브 코드의 병렬 프로그래밍 블로그의 [C++ AMP에서 질감 뷰 디자인 개요](/archive/blogs/nativeconcurrency/overview-of-the-texture-view-design-in-c-amp) 를 참조 하세요.

### <a name="instantiating-texture-view-objects"></a>텍스처 보기 개체 인스턴스화

을 선언 `texture_view` 하는 것은 배열과 연결 된를 선언 하는 것과 비슷합니다 `array_view` . **array** 다음 코드 예제에서는 `texture` 개체 및 이 개체와 연결된 `texture_view` 개체를 여러 개 선언합니다.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

요소 형식이 non-const이고 구성 요소가 하나인 텍스처 보기는 읽기-쓰기이지만 요소 형식이 non-const이고 구성 요소가 둘 이상인 텍스처 보기는 쓰기 전용입니다. 요소 형식이 const인 텍스처 보기는 항상 읽기 전용이지만 요소 형식이 non-const인 경우에는 요소에 포함된 구성 요소 수에 따라 읽기-쓰기인지(구성 요소가 1개) 또는 쓰기 전용인지(구성 요소가 여러 개)가 결정됩니다.

`texture_view`의 요소 형식 즉, 텍스처 보기의 상수성과 함께 텍스처 보기의 구성 요소 수는 보기에서 텍스처 샘플링을 지원하는지 여부 및 Mip 맵 수준에 액세스하는 방법을 결정하는 데도 영향을 줍니다.

|유형|구성 요소|읽기|쓰기|샘플링|Mip 맵 액세스|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N>|1, 2, 4|예|아니요(1)|예|예, 인덱싱 가능. 인스턴스화할 때 범위가 결정됩니다.|
|Texture_view\<T, N>|1<br /><br /> 2, 4|예<br /><br /> 아니요 (2)|예<br /><br /> 예|아니요(1)<br /><br /> 아니요(1)|예, 한 수준. 인스턴스화할 때 수준이 결정됩니다.<br /><br /> 예, 한 수준. 인스턴스화할 때 수준이 결정됩니다.|

이 표를 보면 읽기 전용 텍스처 보기는 새로운 기능을 완전하게 지원하는 대신 보기에 쓸 수는 없습니다. 쓰기 가능 텍스처 보기는 하나의 Mip 맵 수준에만 액세스할 수 있다는 점에서 제한이 따릅니다. 읽기-쓰기 텍스처 보기는 텍스처 보기의 요소 형식에 구성 요소가 하나뿐이어야 한다는 점에서 쓰기 가능 텍스처 보기보다 더 특수합니다. 샘플링은 읽기 기반 작업이므로 쓰기 가능 텍스처 보기에는 지원되지 않습니다.

### <a name="reading-from-texture-view-objects"></a>텍스처 보기 개체에서 읽기

텍스처는 참조를 통해 캡처되고 텍스처 보기는 값을 통해 캡처된다는 점을 제외하면 텍스처 보기를 통한 샘플링되지 않은 텍스처 데이터 읽기는 텍스처 자체에서 읽는 것과 같습니다. 다음 두 코드 예제에서는 이를 잘 보여 줍니다. 첫 번째 예제에서는 `texture`만 사용합니다.

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

다음은 `texture_view` 클래스를 사용한다는 점을 제외하면 위와 동일한 예제입니다.

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

텍스처 보기의 요소가 float, float_2 또는 float_4와 같은 부동 소수점 형식에 기반을 둔 경우 다양한 필터링 모드 및 주소 지정 모드에 대한 하드웨어 지원을 활용하기 위해 텍스처 샘플링을 사용하여 텍스처 보기를 읽을 수 있습니다. C++ AMP에서는 컴퓨팅 시나리오에서 가장 일반적인 두 가지 필터링 모드인 점 필터링(가장 인접한 항목) 및 선형 필터링(가중 평균)과 네 가지 주소 지정 모드인 래핑, 미러링, 고정 및 테두리를 지원합니다. 주소 지정 모드에 대 한 자세한 내용은 [Address_mode 열거](reference/concurrency-graphics-namespace-enums.md#address_mode)를 참조 하세요.

C++ AMP에서 직접적으로 지원하는 모드 외에도, Interop API를 통해 플랫폼 API를 직접 사용하여 생성된 텍스처 샘플러를 사용하면 플랫폼의 다른 필터링 모드 및 주소 지정 모드에 액세스할 수 있습니다. 예를 들어 Direct3D는 이방성 필터링과 같은 다른 필터링 모드를 지원하며 텍스처의 각 차원에 서로 다른 주소 지정 모드를 적용할 수 있습니다. Direct3D API를 사용하여 좌표가 세로로 래핑되고 가로로 미러링되며 이방성 필터링을 사용하여 샘플링되는 텍스처 샘플러를 만든 다음 `make_sampler` Interop API를 사용하여 C++ AMP 코드에 이 샘플러를 사용할 수 있습니다. 자세한 내용은 네이티브 코드의 병렬 프로그래밍 블로그의 [C++ AMP의 질감 샘플링](/archive/blogs/nativeconcurrency/texture-sampling-in-c-amp) 을 참조 하세요.

텍스처 보기는 Mip 맵 읽기도 지원합니다. 읽기 전용 텍스처 보기(요소 형식이 const인 텍스처 보기)는 동적으로 샘플링 가능한 Mip 맵 수준(보기가 인스턴스화될 때 결정됨)이 광범위하며 구성 요소가 1, 2 또는 4개인 요소를 지원하므로 융통성이 가장 뛰어납니다. 구성 요소가 하나인 요소를 포함하는 읽기-쓰기 텍스처도 Mip 맵을 지원하지만 보기가 인스턴스화될 때 결정되는 수준에 대해서만 지원됩니다. 자세한 내용은 네이티브 코드의 병렬 프로그래밍 블로그에서 [mip 맵을를 사용](/archive/blogs/nativeconcurrency/texture-with-mipmaps) 하 여 텍스처를 참조 하세요.

### <a name="writing-to-texture-view-objects"></a>텍스처 보기 개체에 쓰기

[Texture_view:: Get 메서드](reference/texture-view-class.md#get) 를 사용 하 여 개체를 통해 내부에 씁니다. `texture` `texture_view` 텍스처 보기는 읽기 전용, 읽기-쓰기 또는 쓰기 전용일 수 있습니다. 텍스처 보기가 쓰기 가능 텍스처 보기가 되려면 해당 요소의 형식이 non-const여야 합니다. 텍스처 보기가 읽기 가능 및 쓰기 가능 텍스처 보기가 되려면 해당 요소 형식에 구성 요소가 하나만 있어야 합니다. 그렇지 않으면 텍스처 보기가 읽기 전용입니다. 텍스처 보기를 통해 한 번에 하나의 텍스처 Mip 맵 수준에만 액세스할 수 있으며 이 수준은 보기가 인스턴스화될 때 지정됩니다.

다음 예제에서는 Mip 맵 수준이 4개인 텍스처에서 두 번째로 자세한 Mip 맵 수준에 쓰는 방법을 보여 줍니다. 가장 자세한 Mip 맵 수준은 0입니다.

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>상호 운용성

C++ AMP 런타임은와 `texture<T,1>` [ID3D11Texture1D 인터페이스](/windows/win32/api/d3d11/nn-d3d11-id3d11texture1d)간의 상호 운용성, `texture<T,2>` 와 [ID3D11Texture2D 인터페이스](/windows/win32/api/d3d11/nn-d3d11-id3d11texture2d)사이, 및 `texture<T,3>` [ID3D11Texture3D 인터페이스](/windows/win32/api/d3d11/nn-d3d11-id3d11texture3d)간의 상호 운용성을 지원 합니다. [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) 메서드는 개체를 사용 `texture` 하 여 인터페이스를 반환 합니다 `IUnknown` . [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) 메서드는 `IUnknown` 인터페이스와 개체를 사용 `accelerator_view` 하 고 개체를 반환 합니다 `texture` .

## <a name="see-also"></a>참고 항목

[double_2 클래스](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3 클래스](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4 클래스](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2 클래스](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3 클래스](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4 클래스](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2 클래스](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3 클래스](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4 클래스](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2 클래스](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3 클래스](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4 클래스](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector 구조체](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits 구조체](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2 클래스](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3 클래스](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4 클래스](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2 클래스](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3 클래스](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4 클래스](../../parallel/amp/reference/unorm-4-class.md)

---
description: '자세히 알아보기: Concurrency:: graphics 네임 스페이스'
title: Concurrency::graphics 네임스페이스
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: f4ab25a6bc6e7bfd318ea58bb6a7efe403c51a89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132836"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 네임스페이스

Graphics 네임 스페이스는 그래픽 프로그래밍을 위해 디자인 된 형식 및 함수를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
namespace graphics;
```

## <a name="members"></a>멤버

### <a name="namespaces"></a>네임스페이스

|Name|설명|
|----------|-----------------|
|[Concurrency:: graphics::d irect3d 네임 스페이스](concurrency-graphics-direct3d-namespace.md)|Direct3D interop에 대 한 함수를 제공 합니다.|

### <a name="typedefs"></a>Typedefs

|Name|설명|
|----------|-----------------|
|`uint`|[Uint_2 클래스](uint-2-class.md), [uint_3 클래스](uint-3-class.md)및 [uint_4 클래스](uint-4-class.md)의 요소 형식입니다. `typedef unsigned int uint;`로 정의됩니다.|

### <a name="enumerations"></a>열거형

|Name|설명|
|----------|-----------------|
|[Address_mode 열거형](concurrency-graphics-namespace-enums.md#address_mode)입니다.|질감 샘플링에 지원 되는 주소 모드를 지정 합니다.|
|[filter_mode 열거형](concurrency-graphics-namespace-enums.md#filter_mode)|질감 샘플링에 지원 되는 필터 모드를 지정 합니다.|

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[질감 클래스](texture-class.md)|질감은 익스텐트 도메인의 accelerator_view에 대 한 데이터 집계입니다. 익스텐트 도메인의 각 요소에 대 한 변수의 컬렉션입니다. 각 변수는 c + + 기본 형식 (unsigned int, int, float, double) 또는 스칼라 형식에 해당 하는 값을 보유 하거나 (concurrency:: graphics에 정의 됨), concurrency:: graphics에 정의 된 적격 약식 벡터 형식에 해당 하는 값을 보유 합니다.|
|[writeonly_texture_view 클래스](writeonly-texture-view-class.md)|Writeonly_texture_view은 질감에 대 한 writeonly 액세스를 제공 합니다.|
|[double_2 클래스](double-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 **`double`** .|
|[double_3 클래스](double-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 **`double`** .|
|[double_4 클래스](double-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 **`double`** .|
|[float_2 클래스](float-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 **`float`** .|
|[float_3 클래스](float-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 **`float`** .|
|[float_4 클래스](float-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 **`float`** .|
|[int_2 클래스](int-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 **`int`** .|
|[int_3 클래스](int-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 **`int`** .|
|[int_4 클래스](int-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 **`int`** .|
|[norm_2 클래스](norm-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 `norm` .|
|[norm_3 클래스](norm-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 `norm` .|
|[norm_4 클래스](norm-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 `norm` .|
|[uint_2 클래스](uint-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 `uint` .|
|[uint_3 클래스](uint-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 `uint` .|
|[uint_4 클래스](uint-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 `uint` .|
|[unorm_2 클래스](unorm-2-class.md)|2 개 값의 짧은 벡터를 나타냅니다 `unorm` .|
|[unorm_3 클래스](unorm-3-class.md)|3 개 값의 짧은 벡터를 나타냅니다 `unorm` .|
|[unorm_4 클래스](unorm-4-class.md)|4 개 값의 짧은 벡터를 나타냅니다 `unorm` .|
|[샘플러 클래스](sampler-class.md)|질감 샘플링에 사용 되는 샘플러 구성을 나타냅니다.|
|[short_vector 구조체](short-vector-structure.md)|Short 값 벡터의 기본 구현을 제공 합니다.|
|[short_vector_traits 구조체](short-vector-traits-structure.md)|짧은 벡터의 길이와 형식에 대 한 검색을 제공 합니다.|
|[texture_view 클래스](texture-view-class.md)|질감에 대 한 읽기 권한 및 쓰기 권한을 제공 합니다.|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|오버로드됨. 원본 질감의 내용을 대상 호스트 버퍼에 복사 합니다.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|오버로드됨. 소스 질감의 내용을 대상 호스트 버퍼에 비동기적으로 복사 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics. h

**네임스페이스:** 동시성

## <a name="see-also"></a>참고 항목

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)

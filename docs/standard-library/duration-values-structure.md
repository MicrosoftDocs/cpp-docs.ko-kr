---
description: '다음에 대 한 자세한 정보: duration_values 구조체'
title: duration_values 구조체
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: 9bf784b0976a06c6d395498084508251d9ebd4bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324477"
---
# <a name="duration_values-structure"></a>duration_values 구조체

[duration](../standard-library/duration-class.md) 템플릿 매개 변수 `Rep`에 대한 특정 값을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[max](#max)|정적. `Rep` 형식 값의 상한을 지정합니다.|
|[min](#min)|정적. `Rep` 형식 값의 하한을 지정합니다.|
|[반환](#zero)|정적. `Rep(0)`를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<chrono>

**네임스페이스:** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a> duration_values:: max

형식 `Ref`의 값에 대한 상한을 반환하는 정적 메서드입니다.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>반환 값

실제로 `numeric_limits<Rep>::max()`를 반환합니다.

### <a name="remarks"></a>설명

`Rep`가 사용자 정의 형식인 경우 반환 값은 [duration_values::zero](#zero)보다 커야 합니다.

## <a name="duration_valuesmin"></a><a name="min"></a> duration_values:: min

`Ref` 형식의 값에 대한 하한값을 반환하는 정적 메서드입니다.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>반환 값

실제로 `numeric_limits<Rep>::lowest()`를 반환합니다.

### <a name="remarks"></a>설명

`Rep`가 사용자 정의 형식인 경우 반환 값은 [duration_values:: zero](#zero)보다 작아야 합니다.

## <a name="duration_valueszero"></a><a name="zero"></a> duration_values:: 0

`Rep(0)`를 반환합니다.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>설명

`Rep`가 사용자 정의 형식인 경우 반환 값은 가산적 무한대를 나타내야 합니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)

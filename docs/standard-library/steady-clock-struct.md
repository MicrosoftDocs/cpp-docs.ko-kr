---
description: '다음에 대 한 자세한 정보: steady_clock 구조체'
title: steady_clock 구조체
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: 066a98f4eba6670e640e9fcc9b79eb017859a3d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169075"
---
# <a name="steady_clock-struct"></a>steady_clock 구조체

*안정적인* 클록을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
struct steady_clock;
```

## <a name="remarks"></a>설명

Windows에서 `steady_clock` 함수를 래핑합니다 `QueryPerformanceCounter` .

`now`에 대한 첫 번째 호출에서 반환되는 값이 항상 `now`에 대한 순차적 호출에서 반환되는 값보다 작거나 같을 경우 클록은 *단조* 입니다. 클록이 *단조* 이고 클록 틱 간 시간이 지속적이면 해당 클록은 *지속* 입니다.

`high_resolution_clock` 는에 대 한 typedef입니다 `steady_clock` .

### <a name="public-typedefs"></a>Public typedef

|Name|설명|
|----------|-----------------|
|`steady_clock::duration`|에 `nanoseconds` 정의 된의 동의어 \<chrono> 입니다.|
|`steady_clock::period`|에 `nano` 정의 된의 동의어 \<ratio> 입니다.|
|`steady_clock::rep`|의 동의어로 **`long long`** ,의 포함 된 인스턴스화에 있는 클록 틱 수를 나타내는 데 사용 되는 형식입니다 `duration` .|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>`의 동의어입니다.|

## <a name="public-functions"></a>공용 함수

|함수|설명|
|--------------|-----------------|
|`now`|현재 시간을 값으로 반환 합니다 `time_point` .|

## <a name="public-constants"></a>Public 상수

|Name|설명|
|----------|-----------------|
|`steady_clock::is_steady`|보유 **`true`** 합니다. `steady_clock`은 *지속* 입니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<chrono>

**네임스페이스:** std::chrono

## <a name="see-also"></a>참고 항목

- [헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 구조체](../standard-library/system-clock-structure.md)

---
title: high_resolution_clock 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341cae04742d72fdcc7483e74977bf413854df82
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039653"
---
# <a name="high_resolution_clock-struct"></a>high_resolution_clock 구조체

*High_resolution* clock을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class high_resolution_clock
```

## <a name="members"></a>멤버

### <a name="typedefs"></a>Typedefs

|Name|Description|
|----------|-----------------|
|`duration`|에 `nanoseconds` 정의 된의 동의어 \<chrono> 입니다.|
|`period`|에 `nano` 정의 된의 동의어 \<ratio> 입니다.|
|`rep`|의 동의어로 **`long long`** ,의 포함 된 인스턴스화에 있는 클록 틱 수를 나타내는 데 사용 되는 형식입니다 `duration` .|
|`time_point`|`chrono::time_point<high_resolution_clock>`의 동의어입니다.|

## <a name="functions"></a>Functions

|Name|Description|
|-|-|
|`now`|현재 시간을 값으로 반환 합니다 `time_point` .|

## <a name="constants"></a>상수

|Name|Description|
|----------|-----------------|
|`is_steady`|보유 **`true`** 합니다. `high_resolution_clock`은 *지속*입니다.|

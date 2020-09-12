---
title: endian 열거형
description: 스칼라 형식의 endian를 지정 하는 데 사용 되는 열거형입니다.
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: b535bc009fbdc0b047444a6bc2ca36eed7a6d1cb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040082"
---
# <a name="endian-enum"></a>endian 열거형

모든 스칼라 형식의 endian을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
enum class endian {
    little = 0,
    big = 1,
    native = little
 };
```

### <a name="members"></a>멤버

|요소|Description|
|-|-|
| `little` | 스칼라 형식이 작은 endian 임을 나타냅니다. 즉, 최하위 바이트는 가장 작은 주소에 저장 됩니다. 예를 들어 `0x1234` 는 저장 됩니다 `0x34` `0x12` .  |
| `big` | 스칼라 형식이 빅 endian 임을 나타냅니다. 즉, 가장 중요 한 바이트는 가장 작은 주소에 저장 됩니다. 예를 들어 `0x1234` 는 저장 됩니다 `0x12` `0x34` .  |

## <a name="remarks"></a>설명

대상 (x86, x64, ARM, ARM64)을 Microsoft Visual C++ 하는 플랫폼에 대해서는 모든 네이티브 스칼라 형식이 약간 endian입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<bit>

**네임스페이스:** std

[/std: c + + 최신](../build/reference/std-specify-language-standard-version.md) 항목이 필요 합니다.

## <a name="see-also"></a>참고 항목

[\<bit>](../standard-library/bit.md)  

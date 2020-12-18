---
description: '자세한 정보: C 크기 조정 정수 형식'
title: C 크기 조정 정수 형식
ms.date: 07/22/2020
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: ad50806f52638884da69e109da252379dea0d571
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300127"
---
# <a name="c-sized-integer-types"></a>C 크기 조정 정수 형식

**Microsoft 전용**

Microsoft C는 크기가 지정된 정수 형식을 지원합니다. `__intN` 형식 지정자를 사용하여 8비트, 16비트, 32비트 또는 64비트 정수 변수를 선언할 수 있습니다. 여기서 *`N`* 은 정수 변수의 비트 크기입니다. *n* 의 값은 8, 16, 32 또는 64입니다. 다음 예제에서는 네 가지 형식의 크기가 지정된 정수 각각의 변수 하나를 선언합니다.

```C
__int8  nSmall;     // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

처음 세 가지 형식의 크기가 지정된 정수는 동일한 크기의 ANSI 형식과 동의어입니다. 이들은 여러 플랫폼에서 동일하게 동작하는 이식 가능한 코드를 작성하는 데 유용합니다. **`__int8`** 데이터 형식은 **`char`** 형식과 동의어이고, **`__int16`** 은 **`short`** , **`__int32`** 는 **`int`** , **`__int64`** 는 **`long long`** 와 동의어입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[기본 형식의 스토리지](../c-language/storage-of-basic-types.md)

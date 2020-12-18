---
description: '자세한 정보: 정수 형식'
title: 정수 형식
ms.date: 07/22/2020
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 0142a6c9394851bc65df0150db40eb2228dd0fe3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181841"
---
# <a name="integer-types"></a>정수 형식

모든 정수 상수에는 값과 표현 방식에 따라 형식이 제공됩니다. **`l`** 또는 **`L`** 문자를 상수 끝에 추가하여 모든 정수 상수를 **`long`** 형식으로 지정할 수 있으며, **`u`** 또는 **`U`** 를 값에 추가하여 **`unsigned`** 형식으로 지정할 수 있습니다. 소문자 **l`l`** 는 숫자 1과 혼동할 수 있으므로 사용하지 않아야 합니다. **`long`** 정수 상수의 몇 가지 형태는 다음과 같습니다.

```C
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

상수에 할당하는 형식은 상수가 나타내는 값에 따라 달라집니다. 상수의 값은 상수 형식에 대한 표현 가능한 값의 범위에 있어야 합니다. 상수의 형식에 따라 상수가 식에서 사용될 때나 마이너스 기호( **`-`** )가 적용될 때 수행되는 변환이 결정됩니다. 다음 목록에는 정수 상수에 대한 변환 규칙이 요약되어 있습니다.

- 접미사가 없는 10진수 상수의 형식은 **`int`** , **`long int`** 또는 **`unsigned long int`** 입니다. 상수의 값이 표현될 수 있는 이러한 세 형식 중 첫 번째 형식이 상수에 할당됩니다.

- 접미사가 없는 8진수 및 16진수 상수에 할당되는 형식은 상수의 크기에 따라 **`int`** , **`unsigned int`** , **`long int`** 또는 **`unsigned long int`** 입니다.

- **`u`** 또는 **`U`** 접미사가 있는 상수에 할당되는 형식은 상수의 크기에 따라 **`unsigned int`** 또는 **`unsigned long int`** 입니다.

- **`l`** 또는 **`L`** 접미사가 있는 상수에 할당되는 형식은 상수의 크기에 따라 **`long int`** 또는 **`unsigned long int`** 입니다.

- **`u`** 또는 **`U`** 및 **`l`** 또는 **`L`** 접미사가 있는 상수에 할당되는 형식은 **`unsigned long int`** 입니다.

## <a name="see-also"></a>참조

[C 정수 상수](../c-language/c-integer-constants.md)

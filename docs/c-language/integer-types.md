---
title: 정수 형식 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22392a4f02fb81a7c141aaa0e7966a05988dfece
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076673"
---
# <a name="integer-types"></a>정수 형식

모든 정수 상수에는 값과 표현 방식에 따라 형식이 제공됩니다. **l** 또는 **L** 문자를 상수 끝에 추가하여 모든 정수 상수를 **long** 형식으로 지정할 수 있으며, **u** 또는 **U**를 값에 추가하여 `unsigned` 형식으로 지정할 수 있습니다. 소문자 **l**은 숫자 1과 혼동할 수 있으므로 사용하지 않아야 합니다. **long** 정수 상수의 몇 가지 형태는 다음과 같습니다.

```
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

상수에 할당하는 형식은 상수가 나타내는 값에 따라 달라집니다. 상수의 값은 상수 형식에 대한 표현 가능한 값의 범위에 있어야 합니다. 상수의 형식에 따라 상수가 식에서 사용될 때나 마이너스 기호(**-**)가 적용될 때 수행되는 변환이 결정됩니다. 다음 목록에는 정수 상수에 대한 변환 규칙이 요약되어 있습니다.

- 접미사가 없는 10진수 상수의 형식은 `int`, **long int** 또는 **unsigned long int**입니다. 상수의 값이 표현될 수 있는 이러한 세 형식 중 첫 번째 형식이 상수에 할당됩니다.

- 접미사가 없는 8진수 및 16진수 상수에 할당되는 형식은 상수의 크기에 따라 `int`, `unsigned int`, **long int** 또는 **unsigned long int**입니다.

- **u** 또는 **U** 접미사가 있는 상수에 할당되는 형식은 상수의 크기에 따라 **unsigned int** 또는 **unsigned long int**입니다.

- **l** 또는 **L** 접미사가 있는 상수에 할당되는 형식은 상수의 크기에 따라 **long int** 또는 **unsigned long int**입니다.

- **u** 또는 **U** 접미사와 **l** 또는 **L** 접미사가 있는 상수에 할당되는 형식은 **unsigned long int**입니다.

## <a name="see-also"></a>참고 항목

[C 정수 상수](../c-language/c-integer-constants.md)
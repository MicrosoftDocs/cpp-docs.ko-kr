---
description: '자세히 알아보기: 인라인 어셈블리의 형식 및 변수 크기'
title: 인라인 어셈블리의 형식 및 다양한 크기
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 0d6822537f542c159c40c0ed6f14dca93aa36525
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122020"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>인라인 어셈블리의 형식 및 다양한 크기

**Microsoft 전용**

**길이**, **크기** 및 **형식** 연산자는 인라인 어셈블리에서 제한적입니다. MASM 지시문이나 연산자를 사용하여 데이터를 정의할 수 없으므로 이러한 연산자를 `DUP` 연산자와 함께 사용할 수는 없습니다. 그러나 C 또는 C++ 변수나 형식의 크기를 찾기 위해 사용할 수는 있습니다.

- **LENGTH** 연산자는 배열의 요소 수를 반환할 수 있습니다. 배열이 아닌 변수에 대해 값 1을 반환합니다.

- **Size** 연산자는 c 또는 c + + 변수의 크기를 반환할 수 있습니다. 변수의 크기는 해당 **길이** 와 **형식의** 곱입니다.

- **형식** 연산자는 c 또는 c + + 형식 또는 변수의 크기를 반환할 수 있습니다. 변수가 배열인 경우 **형식은** 배열의 단일 요소 크기를 반환 합니다.

예를 들어 프로그램에 8 개의 요소 배열이 있는 경우 **`int`**

```cpp
int arr[8];
```

다음 C 및 어셈블리 식에서 `arr`과 그 요소의 크기를 구합니다.

|__asm|C|크기|
|-------------|-------|----------|
|**길이** arr|`sizeof(arr)/sizeof(arr[0])`|8|
|**크기** arr|`sizeof(arr)`|32|
|Arr **형식**|`sizeof(arr[0])`|4|

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 어셈블리 언어 사용](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>

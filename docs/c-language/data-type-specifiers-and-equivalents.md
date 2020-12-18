---
title: 데이터 형식 지정자 및 해당 항목
description: Microsoft Visual C 데이터 형식 지정자 및 그에 해당하는 항목에 대해 설명합니다.
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.openlocfilehash: 6a1231bc19617dddf1cc01d4c5e7db2863f1055f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207048"
---
# <a name="data-type-specifiers-and-equivalents"></a>데이터 형식 지정자 및 해당 항목

이 문서에서는 일반적으로 긴 형식이 아니라 다음 표에 나열된 형식 지정자 형식을 사용합니다. 또한 **`char`** 형식에 기본적으로 부호가 있다고 가정합니다. 이 문서 전체에서 **`char`** 는 **`signed char`** 와 동일합니다.

## <a name="type-specifiers-and-equivalents"></a>형식 지정자 및 해당 항목

| 형식 지정자 | 해당 값 |
|--|--|
| **`signed char`** <sup>1</sup> | **`char`** |
| **`signed int`** | **`signed`** , **`int`** |
| **`signed short int`** | **`short`**, **`signed short`** |
| **`signed long int`** | **`long`**, **`signed long`** |
| **`unsigned char`** | — |
| **`unsigned int`** | **`unsigned`** |
| **`unsigned short int`** | **`unsigned short`** |
| **`unsigned long int`** | **`unsigned long`** |
| **`float`** | — |
| **`long double`** <sup>2</sup> | — |

<sup>1</sup> 기본적으로 **`char`** 형식을 만들면( **`/J`** 컴파일러 옵션 지정) **`signed char`** 를 **`char`** 로 줄여 표현할 수 없습니다.

<sup>2</sup> 32비트 및 64비트 운영 체제에서 Microsoft C 컴파일러는 **`long double`** 을 **`double`** 형식에 매핑합니다.

**Microsoft 전용**

**`/J`** 컴파일러 옵션을 지정하여 기본 **`char`** 형식을 **`signed char`** 에서 **`unsigned char`** 로 변경할 수 있습니다. 이 옵션이 적용되면, **`char`** 는 **`unsigned char`** 와 같은 의미가 되기 때문에, 부호 있는 문자 값을 선언하려면 **`signed`** 키워드를 사용해야 합니다. **`char`** 값이 명시적으로 **`signed`** 로 선언되면 **`/J`** 옵션은 이 값에 영향을 주지 않으며, 이 값이 **`int`** 형식으로 확장되는 경우에는 부호 확장됩니다. **`char`** 형식은 **`int`** 형식으로 확장되면 제로 확장됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 형식 지정자](../c-language/c-type-specifiers.md)

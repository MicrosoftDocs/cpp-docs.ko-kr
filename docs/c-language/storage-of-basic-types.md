---
description: '자세한 정보: 기본 형식의 저장소'
title: 기본 형식의 저장소
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: c8ae057de19e04327491fd73e45bcd32c1db7738
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296643"
---
# <a name="storage-of-basic-types"></a>기본 형식의 저장소

다음 표에서는 각 기본 형식과 관련된 스토리지에 대해 요약합니다.

## <a name="sizes-of-fundamental-types"></a>기본 형식의 크기

|형식|스토리지|
|----------|-------------|
|**`char`**, **`unsigned char`**, **`signed char`**|1바이트|
|**`short`**, **`unsigned short`**|2바이트|
|**`int`**, **`unsigned int`**|4바이트|
|**`long`**, **`unsigned long`**|4바이트|
|**`long long`**, **`unsigned long long`**|8바이트|
|**`float`**|4바이트|
|**`double`**|8바이트|
|**`long double`**|8바이트|

C 데이터 형식은 일반 범주로 분류됩니다. 정수 형식에는 **`int`** , **`char`** , **`short`** , **`long`** , **`long long`** 이 포함됩니다. 이러한 형식은 **`signed`** 또는 **`unsigned`** 를 사용하여 정규화할 수 있으며, **`unsigned`** 자체를 **`unsigned int`** 의 축약형으로 사용할 수 있습니다. 열거형 형식( **`enum`** )도 대부분 정수 형식으로 처리됩니다. 부동 형식에는 **`float`** , **`double`** , **`long double`** 이 포함됩니다. ‘산술 형식’에는  모든 부동 및 정수 형식이 포함됩니다.

## <a name="see-also"></a>참조

[선언 및 형식](../c-language/declarations-and-types.md)

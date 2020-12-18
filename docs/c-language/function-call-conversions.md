---
description: '자세한 정보: 함수 호출 변환'
title: 함수 호출 변환
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: f37cf2ef6c35cb8e7c856e1ab722a1efda2da61d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195959"
---
# <a name="function-call-conversions"></a>함수 호출 변환

함수 호출의 인수에서 수행되는 변환 형식은 호출된 함수를 위해 선언된 인수 형식을 포함하는 함수 프로토타입(정방향 선언)의 존재 여부에 따라 달라집니다.

함수 프로토타입이 있고 선언된 인수 형식이 포함된 경우 컴파일러는 형식 확인을 수행합니다([함수](../c-language/functions-c.md) 참조).

함수 프로토타입이 없는 경우 함수 호출의 인수에 대해 일반 산술 변환만 수행됩니다. 이러한 변환은 호출의 각 인수에서 독립적으로 수행됩니다. 이는 **`float`** 값이 **`double`** 로 변환되고, **`char`** 또는 **`short`** 값이 **`int`** 로 변환되고, **`unsigned char`** 또는 **`unsigned short`** 가 **`unsigned int`** 로 변환되는 것을 의미합니다.

## <a name="see-also"></a>참조

[형식 변환](../c-language/type-conversions-c.md)

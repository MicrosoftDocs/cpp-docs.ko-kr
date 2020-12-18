---
description: '자세한 정보: 포인터 형식과의 변환'
title: 포인터 형식과의 변환
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 8eb987358cb3e8375e62b9d03cd21a5e02b9f5c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293094"
---
# <a name="conversions-to-and-from-pointer-types"></a>포인터 형식과의 변환

값의 한 형식에 대한 포인터는 다른 형식에 대한 포인터로 변환될 수 있습니다. 그러나 스토리지의 정렬 요구 사항 및 여러 형식의 크기 때문에 결과가 정의되지 않을 수 있습니다. 개체에 대한 포인터는 형식이 덜 엄격하거나 동일하게 엄격한 스토리지 정렬을 요구하는 개체에 대한 포인터로 변환되고 다시 변경 없이 되돌릴 수 있습니다.

정보의 제한 또는 손실 없이 **`void`** 에 대한 포인터를 포인터에서 임의의 형식으로 또는 임의의 형식에서 포인터로 변환할 수 있습니다. 결과가 원래 형식으로 다시 변환되는 경우 원래 포인터가 복구됩니다.

포인터가 같은 형식의 다른 포인터로 변환되었지만 추가 또는 다른 한정자를 포함하고 있는 경우 새 포인터는 새 한정자의 제한을 제외하고 기존 포인터와 동일합니다.

포인터 값은 정수 계열 값으로도 변환될 수 있습니다. 변환 경로는 다음 규칙에 따라 포인터의 크기와 정수 계열 형식의 크기에 따라 다릅니다.

- 포인터 크기가 정수 계열 형식의 크기보다 크거나 같은 경우 포인터는 부동 소수점 값으로 변환될 수 없다는 점을 제외하고 변환 시 부호 없는 값처럼 동작합니다.

- 포인터가 정수 계열 형식보다 작은 경우 포인터는 먼저 정수 계열 형식과 같은 크기의 포인터로 변환된 다음 정수 계열 형식으로 변환됩니다.

반대로 정수 계열 형식은 다음 규칙에 따라 포인터 형식으로 변환될 수 있습니다.

- 정수 계열 형식이 포인터 형식과 같은 크기인 경우 변환을 수행하면 정수 계열 값이 포인터(부호 없는 정수)로 처리됩니다.

- 정수 계열 형식의 크기가 포인터 형식의 크기와 다른 경우 정수 계열 형식은 먼저 [부호 있는 정수 계열 형식에서 변환](../c-language/conversions-from-signed-integral-types.md) 및 [부호 없는 정수 계열 형식에서 변환](../c-language/conversions-from-unsigned-integral-types.md) 테이블에 지정된 변환 경로를 사용하여 포인터 크기로 변환됩니다. 그런 다음 포인터 값으로 처리됩니다.

값이 0인 정수 상수 식 또는 **`void`** <strong>\*</strong> 형식으로 캐스팅된 식은 형식 캐스팅, 할당 또는 비교를 통해 모든 형식의 포인터로 변환될 수 있습니다. 이 경우 동일한 형식의 다른 null 포인터와 똑같은 null 포인터가 생성되지만 이 null 포인터는 함수 또는 개체에 대한 어떤 포인터와도 같지 않습니다. 상수 0 이외의 정수는 포인터 형식으로 변환될 수 있지만 결과는 이식할 수 없습니다.

## <a name="see-also"></a>참조

[할당 변환](../c-language/assignment-conversions.md)

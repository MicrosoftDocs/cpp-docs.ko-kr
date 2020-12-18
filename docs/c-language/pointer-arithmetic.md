---
description: '자세한 정보: 포인터 산술 연산'
title: 포인터 산술 연산
ms.date: 11/04/2016
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
ms.openlocfilehash: 37ee9fd696f874d1faa84b5d656317cf67f75a6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243122"
---
# <a name="pointer-arithmetic"></a>포인터 산술 연산

포인터와 정수가 포함된 가감 연산은 포인터 피연산자가 배열 멤버의 주소를 지정하고 정수 값이 동일한 배열의 경계 내에서 오프셋을 생성하는 경우에만 의미 있는 결과를 제공합니다. 정수 값이 주소 오프셋으로 변환될 때 컴파일러는 동일한 크기의 메모리 위치만 원래 주소와 오프셋을 더한 주소 사이에 있다고 가정합니다.

이 가정은 배열 멤버에 대해 유효합니다. 정의에 따라 배열은 형식이 동일한 일련의 값입니다. 배열의 요소는 인접한 메모리 위치에 있습니다. 그러나 배열 요소를 제외한 모든 형식의 스토리지는 동일한 형식의 식별자로 채워지도록 보장되지 않습니다. 즉, 공백이 메모리 위치 사이에 나타날 수 있으며, 심지어 동일한 형식의 위치 사이에도 공백이 나타날 수 있습니다. 따라서 배열 요소를 제외한 값의 주소에서 더하거나 뺀 결과는 정의되지 않습니다.

마찬가지로 두 포인터 값을 빼는 경우 변환에서는 공백이 없는 동일한 형식의 값만 피연산자가 제공하는 주소 사이에 있다고 가정합니다.

## <a name="see-also"></a>참조

[C 가감 연산자](../c-language/c-additive-operators.md)

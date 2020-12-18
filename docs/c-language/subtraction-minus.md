---
description: '자세한 정보: 빼기(–)'
title: 빼기(–)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 8e0daf4e1bfdbb844df99e3f79dc2baf5a30e6e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114561"
---
# <a name="subtraction--"></a>빼기(–)

빼기 연산자( **-** )는 두 번째 피연산자를 첫 번째 피연산자에서 뺍니다. 두 피연산자 모두 정수 계열 또는 부동 형식이 되거나 하나는 포인터가 되고 다른 하나는 정수가 될 수 있습니다.

두 포인터를 뺀 후 포인터가 주소를 지정하는 형식의 값 크기로 그 차를 나누어 부호 있는 정수 값으로 변환합니다. 정수 값의 크기는 **ptrdiff_t** 형식에 의해 표준 포함 파일 STDDEF.H에 정의됩니다. 결과는 두 주소 간 해당 형식의 메모리 위치 수를 나타냅니다. [포인터 산술](../c-language/pointer-arithmetic.md)에서 설명한 대로 결과는 같은 배열의 두 요소에 대해서만 의미가 있습니다.

정수 값을 포인터 값에서 빼면 빼기 연산자가 포인터가 주소를 지정하는 값의 크기를 곱하여 정수 값(*i*)을 변환합니다. 변환 후 정수 값은 *i* 메모리 위치를 나타내며 각 위치의 길이는 포인터 형식으로 지정됩니다. 변환된 정수 값을 포인터 값에서 빼면 결과는 원래 주소 앞의 메모리 주소 *i* 위치입니다. 새 포인터는 원래 포인터 값에 의해 주소가 지정된 형식의 값을 가리킵니다.

## <a name="see-also"></a>참조

[C 가감 연산자](../c-language/c-additive-operators.md)

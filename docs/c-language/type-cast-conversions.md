---
description: '자세한 정보: 형식 캐스팅 변환'
title: 형식 캐스팅 변환
ms.date: 11/04/2016
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
ms.openlocfilehash: dfa3e54320c416e4bd69cca06d2677def6244247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242914"
---
# <a name="type-cast-conversions"></a>형식 캐스팅 변환

형식 캐스팅을 사용하여 명시적으로 형식을 변환할 수 있습니다.

**구문**

*cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*단항 식*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *type-name*  **)**  *cast-expression*

*type-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*type-name* 은 형식이고 *cast-expression* 은 해당 형식으로 변환할 값입니다. 형식 캐스팅을 사용하는 식은 l-value가 아닙니다. *cast-expression* 은 *type-name* 형식의 변수에 할당된 것처럼 변환됩니다. 할당에 대한 변환 규칙([할당 변환](../c-language/assignment-conversions.md)에 개괄되어 있음)은 형식 캐스팅에도 적용됩니다. 다음 표에서는 임의의 형식으로 캐스팅될 수 있는 형식을 보여 줍니다.

### <a name="legal-type-casts"></a>올바른 형식 캐스팅

|대상 형식|잠재적 소스|
|-----------------------|-----------------------|
|정수 계열 형식 표|임의의 정수 형식 또는 부동 소수점 형식이나 개체에 대한 포인터|
|부동 소수점|산술 형식|
|개체에 대한 포인터 또는 ( **`void`** <strong>\*</strong>)|임의의 정수 형식, ( **`void`** <strong>\*</strong>), 개체에 대한 포인터 또는 함수 포인터|
|함수 포인터|임의의 정수 계열 형식, 개체에 대한 포인터 또는 함수 포인터|
|구조체, 공용 구조체 또는 배열|없음|
|void 형식|모든 형식|

모든 식별자를 **`void`** 형식으로 캐스팅할 수 있습니다. 그러나 형식 캐스트 식에 지정된 형식이 **`void`** 가 아닌 경우 해당 형식으로 캐스팅되는 식별자가 **`void`** 식이 될 수 없습니다. 모든 식을 **`void`** 로 캐스팅할 수 있지만 **`void`** 형식의 식은 다른 형식으로 캐스팅할 수 없습니다. 예를 들어, **`void`** 반환 형식이 포함된 함수의 반환 형식을 다른 형식으로 캐스팅할 수 없습니다.

**`void`** <strong>\*</strong> 식에는 **`void`** 형식이 아니라 **`void`** 에 대한 형식 포인터가 있습니다. 개체가 **`void`** 형식으로 캐스팅되면 결과 식을 어떠한 항목에도 할당할 수 없습니다. 마찬가지로, 형식 캐스팅 개체가 허용 가능한 l-value가 아니므로 형식 캐스팅 개체에 어떠한 항목도 할당할 수 없습니다.

**Microsoft 전용**

형식 캐스팅은 식별자의 크기가 변경되지 않는 한 l-value 식이 될 수 있습니다. l-value 식에 대한 자세한 내용은 [L-Value 및 R-Value 식](../c-language/l-value-and-r-value-expressions.md)을 참조하세요.

**Microsoft 전용 종료**

캐스팅을 사용하여 식을 **`void`** 형식으로 변환할 수 있지만 결과 식은 값이 필요하지 않은 위치에서만 사용할 수 있습니다. **`void`** <strong>\*</strong>로 변환되었다가 다시 원래 형식으로 변환된 개체 포인터는 해당 원래 값으로 되돌려집니다.

## <a name="see-also"></a>참조

[형식 변환](../c-language/type-conversions-c.md)

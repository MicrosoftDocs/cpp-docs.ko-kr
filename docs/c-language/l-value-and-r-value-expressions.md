---
description: '자세한 정보: L-Value 및 R-Value 식'
title: L-Value 및 R-Value 식
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: 84812e211ddd008226773436bc26e22f6150c852
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181815"
---
# <a name="l-value-and-r-value-expressions"></a>L-Value 및 R-Value 식

메모리 위치를 참조하는 식을 "l-value" 식이라고 합니다. l-value는 스토리지 영역의 "로케이터" 값이나 "왼쪽" 값을 나타내므로 등호( **=** )의 왼쪽에 나타날 수 있습니다. l-value는 대개 식별자입니다.

수정할 수 있는 위치를 참조하는 식을 "수정할 수 있는 l-value"라고 합니다. 수정할 수 있는 l-value는 배열 형식, 불완전한 형식 또는 **`const`** 특성이 있는 형식일 수 없습니다. 구조체와 공용 구조체가 수정할 수 있는 l-value이려면 **`const`** 특성이 있는 멤버를 포함하지 않아야 합니다. 식별자의 이름은 스토리지 위치를 나타내지만, 변수의 값은 해당 위치에 저장된 값입니다.

식별자는 메모리 위치를 참조하고 산술, 구조체, 공용 구조체 또는 포인터 형식인 경우 수정할 수 있는 l-value입니다. 예를 들어 `ptr`이 스토리지 영역에 대한 포인터이면 `*ptr`은 `ptr`이 가리키는 스토리지 영역을 나타내는 수정할 수 있는 l-value입니다.

다음 C 식은 모두 l-value 식일 수 있습니다.

- 정수 계열, 부동 소수점, 포인터, 구조체 또는 공용 구조체 형식의 식별자

- 배열로 평가되지 않는 첨자식( **[ ]** )

- 멤버 선택 식( **->** 또는 **.** )

- 배열을 참조하지 않는 단항 간접 참조 식(<strong>\*</strong>)

- 괄호로 묶인 l-value 식

- **`const`** 개체(수정할 수 없는 l-value)

"r-value"는 식의 값을 설명하고 l-value와 구별하기 위해 때때로 사용됩니다. 모든 l-value는 r-value이지만 모든 r-value가 l-value인 것은 아닙니다.

**Microsoft 전용**

Microsoft C에는 개체의 크기가 캐스팅을 통해 길어지지 않는 한 l-value로 사용하기 위해 l-value를 캐스팅할 수 있도록 허용하는 ANSI C 표준의 확장이 포함되어 있습니다. 자세한 내용은 [형식 캐스팅 변환](../c-language/type-cast-conversions.md)을 참조하세요. 다음 예제에서는 이 기능을 보여 줍니다.

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

기본적으로 Microsoft C에는 Microsoft 확장을 사용하도록 설정되어 있습니다. 이러한 확장을 사용하지 않도록 설정하려면 /Za 컴파일러 옵션을 사용하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[피연산자 및 식](../c-language/operands-and-expressions.md)

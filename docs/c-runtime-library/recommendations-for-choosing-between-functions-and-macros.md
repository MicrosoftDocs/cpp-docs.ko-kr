---
title: 함수와 매크로 중 선택에 대한 권장 사항
description: Microsoft CRT (C 런타임 라이브러리)에서 매크로와 함수를 사용 하는 경우의 차이점에 대해 설명 합니다.
ms.date: 11/04/2016
f1_keywords:
- c.functions
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
ms.openlocfilehash: 67dafc0a9a2c2904fcdd30d5e0177251af8a190a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500730"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>함수와 매크로 중 선택에 대한 권장 사항

대부분의 Microsoft 런타임 라이브러리 루틴은 컴파일되거나 어셈블된 함수입니다. 그러나 일부 루틴은 매크로로 구현됩니다. 항상 함수 선언 이후에 매크로가 나타나기 때문에 헤더 파일에서 함수 버전의 루틴과 매크로 버전의 루틴을 모두 선언할 때 매크로 정의가 우선 적용됩니다. 함수와 매크로 모두로 구현되는 루틴을 호출할 때 컴파일러에서 다음 두 가지 방법으로 함수 버전을 사용하도록 강제 설정할 수 있습니다.

- 루틴 이름을 괄호로 묶습니다.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- 다음 `#undef` 지시문을 사용하여 매크로 정의를 "정의 해제"합니다.

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

라이브러리 루틴의 함수 구현과 매크로 구현 중 하나를 선택해야 하는 경우 다음 사항을 고려해야 합니다.

- **속도 대 크기** 매크로 사용 시 주요 장점은 실행 시간이 보다 빠르다는 점입니다. 전처리하는 동안 매크로는 사용될 때마다 인라인으로 확장됩니다(해당 정의에 의해 교체됨). 함수 정의는 호출 횟수에 관계없이 한 번만 발생합니다. 매크로는 코드 크기를 증가시킬 수 있지만 함수 호출과 관련된 오버헤드는 없습니다.

- **함수 계산** 함수는 주소로 계산되지만 매크로는 주소로 계산되지 않습니다. 따라서 포인터가 필요한 컨텍스트에서 매크로 이름을 사용할 수 없습니다. 예를 들어 함수에 대한 포인터를 선언할 수 있지만 매크로에 대한 포인터는 선언할 수 없습니다.

- **형식 검사** 함수를 선언할 때 컴파일러는 인수 형식을 검사할 수 있습니다. 사용자가 매크로를 선언할 수 없기 때문에 컴파일러에서 매크로 인수 형식을 검사할 수 없습니다. 컴파일러에서는 사용자가 매크로에 전달하는 인수 개수를 검사할 수 있습니다.

## <a name="see-also"></a>참고 항목

[형식-제네릭 수학](tgmath.md)\
[CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)

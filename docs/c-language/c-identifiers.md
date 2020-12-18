---
description: '자세한 정보: C 식별자'
title: C 식별자
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: 926af854e9c6a84e84cac6e063a2b8db710c26b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293549"
---
# <a name="c-identifiers"></a>C 식별자

"식별자" 또는 "기호"는 프로그램에서 변수, 형식, 함수 및 레이블에 제공하는 이름입니다. 식별자 이름은 어떤 키워드와도 철자 및 대/소문자가 달라야 합니다. C 또는 Microsoft 키워드를 식별자로 사용할 수 없습니다. 이러한 키워드는 특별한 용도로 예약되어 있습니다. 식별자는 변수, 형식 또는 함수 선언에서 지정하여 만듭니다. 이 예제에서 `result`는 정수 변수에 대한 식별자이며, `main` 및 `printf`는 함수에 대한 식별자 이름입니다.

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

식별자가 선언되면 이후 프로그램 문에서 식별자를 사용하여 관련 값을 참조할 수 있습니다.

문 레이블이라는 특수한 종류의 식별자는 **`goto`** 문에서 사용할 수 있습니다. 선언은 [선언 및 형식](../c-language/declarations-and-types.md)에서 설명하고, 문 레이블은 [goto 및 Labeled 문](../c-language/goto-and-labeled-statements-c.md)에서 설명합니다.

## <a name="syntax"></a>구문

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

*nondigit*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **_ a b c d e f g h i j k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T U V W X Y Z**

*digit*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

식별자 이름의 첫 번째 문자는 `nondigit`여야 합니다. 즉, 첫 번째 문자는 밑줄 또는 대문자나 소문자여야 합니다. ANSI는 외부 식별자 이름에서 6개의 유효한 문자를 허용하고 내부(함수 내) 식별자의 이름에 대해 31자를 허용합니다. 외부 식별자(글로벌 범위에서 선언되거나 **`extern`** 스토리지 클래스로 선언된 식별자)는 링커 등의 다른 소프트웨어에서 처리되어야 하므로 추가 명명 제한이 적용될 수 있습니다.

**Microsoft 전용**

ANSI는 외부 식별자 이름에서 6개의 유효한 문자를 허용하고 내부(함수 내) 식별자 이름에 대해 31자를 허용하지만, Microsoft C 컴파일러는 내부 또는 외부 식별자 이름에서 247자를 허용합니다. ANSI 호환성을 고려하지 않는 경우 /H(외부 이름의 길이 제한) 옵션을 사용하여 이 기본값을 더 작거나 큰 수로 수정할 수 있습니다.

**Microsoft 전용 종료**

C 컴파일러는 대문자 및 소문자를 고유한 문자로 간주합니다. "대/소문자 구분"이라는 이 기능을 통해 철자는 동일하지만 하나 이상의 문자에 대한 대/소문자가 다른 고유한 식별자를 만들 수 있습니다. 예를 들어 다음 각 식별자는 고유합니다.

```
add
ADD
Add
aDD
```

**Microsoft 전용**

두 개의 밑줄 또는 밑줄 뒤에 대문자로 시작하는 이름을 식별자 이름으로 선택하지 마십시오. ANSI C 표준에서는 이러한 문자 조합으로 시작하는 식별자 이름을 컴파일러용으로 예약할 수 있습니다. 파일 수준 범위의 식별자도 밑줄과 소문자를 처음 두 문자로 사용하여 이름을 지정하면 안 됩니다. 이러한 문자로 시작되는 식별자 이름도 예약되어 있습니다. 규칙에 따라 Microsoft는 밑줄과 대문자를 사용하여 매크로 이름을 시작하고 두 개의 밑줄을 사용하여 Microsoft 관련 키워드 이름을 시작합니다. 명명 충돌을 방지하려면 항상 한두 개의 밑줄로 시작하지 않거나 밑줄 뒤에 대문자로 시작하지 않는 식별자 이름을 선택합니다.

**Microsoft 전용 종료**

ANSI 또는 Microsoft 명명 제한을 따르는 올바른 식별자의 예는 다음과 같습니다.

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Microsoft 전용**

소스 파일의 식별자가 기본적으로 대/소문자를 구분하지만 개체 파일의 기호는 그렇지 않습니다. Microsoft C는 컴파일 단위 내 식별자를 대/소문자를 구분하는 것으로 간주합니다.

Microsoft 링커는 대/소문자를 구분합니다. 대/소문자에 따라 일관성 있게 모든 식별자를 지정해야 합니다.

"소스 문자 집합"은 소스 파일에 나타날 수 있는 올바른 문자 집합입니다. Microsoft C의 경우 소스 집합은 표준 ASCII 문자 집합입니다. 소스 문자 집합과 실행 문자 집합에는 이스케이프 시퀀스로 사용되는 ASCII 문자가 포함됩니다. 실행 문자 집합에 대한 자세한 내용은 [문자 상수](../c-language/c-character-constants.md)를 참조하세요.

**Microsoft 전용 종료**

식별자에는 해당 식별자가 알려져 있는 프로그램의 영역인 "범위"가 있으며 다른 범위의 같은 이름이 같은 식별자를 참조하는지 여부를 결정하는 "링크"가 있습니다. 이러한 항목은 [수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)에 설명되어 있습니다.

## <a name="see-also"></a>참조

[C 요소](../c-language/elements-of-c.md)

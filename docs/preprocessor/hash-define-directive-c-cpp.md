---
description: '자세한 정보: #define 지시문 (C/c + +)'
title: '#define 지시문(C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: 6821f775492671d860f4491354fff77e66150101
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300463"
---
# <a name="define-directive-cc"></a>#define 지시문 (C/c + +)

**#Define** 는 식별자 또는 매개 변수화 된 식별자와 토큰 문자열을 연결 하는 *매크로* 를 만듭니다. 매크로가 정의된 후 컴파일러는 소스 파일에서 발생하는 각 식별자를 토큰 문자열로 대체할 수 있습니다.

## <a name="syntax"></a>Syntax

> **#define** *식별자* *토큰-문자열*<sub>옵트인</sub>\
> **#define** *식별자* **(** *식별자*<sub>옵트인</sub>**,** ... **,** *identifier*<sub>opt</sub> **)** *토큰-문자열*<sub>옵트인</sub>

## <a name="remarks"></a>설명

**#Define** 지시문을 통해 컴파일러는 소스 파일에서 각 *식별자* 발생에 대 한 *토큰 문자열* 을 대체 합니다. *식별자* 는 토큰을 형성 하는 경우에만 대체 됩니다. 즉, 식별자가 주석, 문자열 또는 긴 식별자의 일부로 표시 되는 경우에는 *식별자* 가 대체 되지 않습니다. 자세한 내용은 [토큰](../cpp/character-sets.md)을 참조 하세요.

*토큰 문자열* 인수는 키워드, 상수 또는 완전 한 문과 같은 일련의 토큰으로 구성 됩니다. 하나 이상의 공백 문자는 *식별자* 에서 *토큰 문자열* 을 구분 해야 합니다. 이 공백은 대체 텍스트의 일부 또는 대체 텍스트의 최종 토큰 뒤에 오는 공백으로 간주되지 않습니다.

`#define` *토큰 문자열이* 없는은 소스 파일에서 *식별자* 의 발생을 제거 합니다. *식별자* 는 정의 된 상태로 유지 되며 및 지시문을 사용 하 여 테스트할 수 있습니다 `#if defined` `#ifdef` .

두 번째 구문 형식에서는 매개 변수를 사용하여 함수 형식 매크로를 정의합니다. 이 형식은 괄호 안에 표시되어야 하는 매개 변수의 선택 목록을 허용합니다. 매크로가 정의 된 후 각 후속 *식별자*( *identifier*<sub>opt</sub>, ..., *identifier*<sub>opt</sub> )는 정식 매개 변수를 대체 하는 실제 인수가 있는 *토큰 문자열* 인수 버전으로 대체 됩니다.

정식 매개 변수 이름이 *토큰 문자열* 에 표시 되어 실제 값을 대체 하는 위치를 표시 합니다. 각 매개 변수 이름은 *토큰 문자열* 에 여러 번 나타날 수 있으며 이름은 순서에 관계 없이 나타날 수 있습니다. 호출의 인수 개수는 매크로 정의의 매개 변수 개수와 일치해야 합니다. 괄호를 자유롭게 사용하여 복잡한 실제 인수가 올바르게 해석되도록 합니다.

목록의 형식 매개 변수는 쉼표로 구분됩니다. 목록의 각 이름은 고유해야 하고 목록은 괄호로 묶여야 합니다. *식별자* 와 여는 괄호를 구분할 수 있는 공백은 없습니다. 줄 연결 사용- `\` 여러 소스 줄에서 긴 지시문의 경우 줄 바꿈 문자 바로 앞에 백슬래시 ()를 추가 합니다. 정식 매개 변수 이름의 범위는 *토큰 문자열* 을 종료 하는 새 줄로 확장 됩니다.

매크로가 두 번째 구문 형식으로 정의된 경우, 인수 목록이 그 뒤에 오는 텍스트 인스턴스는 매크로 호출을 나타냅니다. 소스 파일의 *식별자* 인스턴스 뒤에 오는 실제 인수는 매크로 정의의 해당 형식 매개 변수와 일치 합니다. 문자열 화 (), charizing () 또는 토큰 붙여넣기 () 연산자가 아닌 *토큰 문자열* 의 각 형식 매개 변수 `#` `#@` `##` 는 그 다음에 연산자가 오지 않고 `##` 해당 실제 인수로 대체 됩니다. 실제 인수의 모든 매크로는 지시문이 형식 매개 변수를 대체하기 전에 확장됩니다. 연산자는 [전처리기 연산자](../preprocessor/preprocessor-operators.md)에 설명 되어 있습니다.

인수가 있는 매크로의 다음 예는 **#define** 구문의 두 번째 형태를 보여 줍니다.

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

파생 효과가 있는 인수를 사용하면 매크로가 예기치 않은 결과를 생성하기도 합니다. 지정 된 형식 매개 변수는 *토큰 문자열* 에 두 번 이상 나타날 수 있습니다. 해당 형식 매개 변수가 파생 효과가 있는 식으로 대체되는 경우 해당 식은 그 파생 효과로 인해 두 번 이상 계산됩니다. [토큰 붙여넣기 연산자 (# #)](../preprocessor/token-pasting-operator-hash-hash.md)아래의 예제를 참조 하십시오.

`#undef` 지시문으로 인해 식별자의 전처리기 정의가 무시될 수 있습니다. 자세한 내용은 [#undef 지시문을](../preprocessor/hash-undef-directive-c-cpp.md) 참조 하십시오.

정의 되는 매크로 이름이 *토큰 문자열* 에서 발생 하는 경우 (다른 매크로 확장의 결과로도) 확장 되지 않습니다.

같은 이름을 가진 매크로에 대 한 두 번째 **#define** 는 두 번째 토큰 시퀀스가 첫 번째와 동일 하지 않으면 경고를 생성 합니다.

**Microsoft 전용**

Microsoft C/C++에서는 새 정의가 원래 정의와 구문적으로 동일할 경우 매크로를 재정의할 수 있습니다. 즉, 두 개의 정의에서 매개 변수 이름은 각기 다를 수 있습니다. 이 동작은 두 정의를 어휘 적으로 동일 하 게 해야 하는 ANSI C와는 다릅니다.

예를 들어, 다음 두 매크로는 매개 변수 이름만 제외하면 모두 동일합니다. ANSI C에서는 이러한 재정의를 허용 하지 않지만 Microsoft C/c + +는 오류 없이 컴파일합니다.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

한편 다음 동일하지 않은 두 매크로는 Microsoft C/C++에서 경고를 생성합니다.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**Microsoft 전용 종료**

이 예에서는 **#define** 지시문을 보여 줍니다.

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

첫 번째 명령문은 `WIDTH` 식별자를 정수 상수 80으로 정의하고, `LENGTH`를 `WIDTH` 더하기 정수 상수 10으로 정의합니다. `LENGTH`가 나타날 때마다 (`WIDTH + 10`)으로 바뀝니다. 또한, `WIDTH + 10`이 발생할 때마다 (`80 + 10`) 식으로 바뀝니다. `WIDTH + 10`을 묶는 괄호는 다음과 같은 문에서 해석을 제어하기 때문에 중요합니다.

```C
var = LENGTH * 20;
```

전처리 단계 후 문은 다음과 같아집니다.

```C
var = ( 80 + 10 ) * 20;
```

결과 값이 1800으로 계산됩니다. 괄호가 없을 경우 결과는 다음과 같습니다.

```C
var = 80 + 10 * 20;
```

280로 평가 됩니다.

**Microsoft 전용**

[/D](../build/reference/d-preprocessor-definitions.md) 컴파일러 옵션을 사용 하 여 매크로 및 상수를 정의 하는 것은 파일의 시작 부분에서 **#define** 전처리 지시문을 사용 하는 것과 동일한 효과를 가집니다. /D 옵션을 사용하여 최대 30 매크로로 정의할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[전처리기 지시문](../preprocessor/preprocessor-directives.md)

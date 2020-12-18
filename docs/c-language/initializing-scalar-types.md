---
description: '자세한 정보: 스칼라 형식 초기화'
title: 스칼라 형식 초기화
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: a9294f04f39e6984a2068c5c8f79e48641834236
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181828"
---
# <a name="initializing-scalar-types"></a>스칼라 형식 초기화

스칼라 형식을 초기화할 때 *`assignment-expression`* 값이 변수에 할당됩니다. 할당에 대한 변환 규칙이 적용됩니다. (변환 규칙에 대한 자세한 내용은 [형식 변환](../c-language/type-conversions-c.md)을 참조하세요.)

## <a name="syntax"></a>구문

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`init-declarator-list`* <sub>opt</sub> **`;`**

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`storage-class-specifier`* *`declaration-specifiers`* <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-specifier`* *`declaration-specifiers`* <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-qualifier`* *`declaration-specifiers`* <sub>opt</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declarator`* **`=`** *`initializer`*  /\* 스칼라 초기화의 경우 \*/

*`initializer`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assignment-expression`*

다음 규칙에 따라 모든 형식의 변수를 초기화할 수 있습니다.

- 파일 범위 수준에서 선언된 변수를 초기화할 수 있습니다. 외부 수준에서 변수를 명시적으로 초기화하지 않는 경우 해당 변수는 기본적으로 0으로 초기화됩니다.

- 상수 식을 사용하여 **`static`** *`storage-class-specifier`* 로 선언된 전역 변수를 초기화할 수 있습니다. **`static`** 으로 선언될 변수는 프로그램 실행이 시작될 때 초기화됩니다. 전역 **`static`** 변수를 명시적으로 초기화하지 않는 경우 해당 변수는 기본적으로 0으로 초기화되고 포인터 형식을 갖는 모든 멤버에 null 포인터가 할당됩니다.

- **`auto`** 또는 **`register`** 스토리지 클래스 지정자로 선언된 변수는 해당 변수가 선언된 블록에 실행 제어가 전달될 때마다 초기화됩니다. **`auto`** 또는 **`register`** 변수의 선언에서 이니셜라이저를 생략하는 경우 변수의 초기 값이 정의되지 않습니다. 자동 및 레지스터 값의 경우 이니셜라이저는 상수가 되는 것으로 제한되지 않습니다. 따라서 이니셜라이저는 함수가 호출되어도 이전에 정의된 값을 포함하는 모든 식일 수 있습니다.

- 외부 변수 선언 및 모든 **`static`** 변수에 대한 초기 값은 외부 또는 내부인지에 상관없이 상수 식이어야 합니다. 자세한 내용은 [상수 식](../c-language/c-constant-expressions.md)을 참조하세요. 외부 선언 또는 정적 변수의 주소는 상수이므로 이러한 주소를 사용하면 내부적으로 선언된 **`static`** 포인터 변수를 초기화할 수 있습니다. 그러나 **`auto`** 변수의 주소는 블록의 각 실행에 대해 서로 다를 수 있으며 정적 이니셜라이저로 사용될 수 없습니다. 상수 또는 변수 값을 사용하여 **`auto`** 및 **`register`** 변수를 초기화할 수 있습니다.

- 식별자 선언에 블록 범위가 있으며 식별자에 외부 링크가 있는 경우 선언이 초기화를 가질 수 없습니다.

## <a name="examples"></a>예

다음 예제에서는 초기화를 보여 줍니다.

```C
int x = 10;
```

정수 변수 `x`는 상수 식 `10`으로 초기화됩니다.

```C
register int *px = 0;
```

`px` 포인터는 0으로 초기화되어 "null" 포인터를 생성합니다.

```C
const int c = (3 * 1024);
```

이 예제에서는 상수 식 `(3 * 1024)`를 사용하여 `c`를 **`const`** 키워드 때문에 수정될 수 없는 상수 값으로 초기화합니다.

```C
int *b = &x;
```

이 문은 다른 변수 `b`의 주소와 함께 `x` 포인터를 초기화합니다.

```C
int *const a = &z;
```

`a` 포인터는 `z`라는 변수의 주소와 함께 초기화됩니다. 그러나 이 포인터는 **`const`** 로 지정되므로 `a` 변수는 초기화만 할 수 있고 수정은 할 수 없습니다. 항상 동일한 위치를 가리킵니다.

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

전역 변수 `GLOBAL`은 외부 수준에서 선언되므로 전역 수명을 가집니다. 지역 변수 `LOCAL`은 **`auto`** 스토리지 클래스를 가지며 선언된 함수를 실행하는 동안에만 주소를 가집니다. 따라서 **`static`** 포인터 변수 `lp`를 `LOCAL`의 주소로 초기화할 수 없습니다. `GLOBAL`은 주소가 항상 동일하므로 **`static`** 포인터 변수 `gp`는 해당 주소로 초기화될 수 있습니다. 마찬가지로 `*rp`는 지역 변수이며 비상수 이니셜라이저를 가질 수 있으므로 `rp`는 초기화될 수 있습니다. 블록을 입력할 때마다 `LOCAL`에 새 주소가 지정되며 이 주소는 `rp`에 할당됩니다.

## <a name="see-also"></a>참조

[초기화](../c-language/initialization.md)

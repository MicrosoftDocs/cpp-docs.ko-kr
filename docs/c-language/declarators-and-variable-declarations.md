---
description: '자세한 정보: 선언자 및 변수 선언'
title: 선언자 및 변수 선언
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 920c44e3345c6143489815de55ea81470e46d279
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306419"
---
# <a name="declarators-and-variable-declarations"></a>선언자 및 변수 선언

이 단원의 나머지 부분에서는 이 목록에 요약된 변수 형식 선언의 형태와 의미를 설명합니다. 나머지 단원에서는 다음을 선언하는 방법을 중점적으로 설명합니다.

|변수 형식|설명|
|----------------------|-----------------|
|[단순 변수](../c-language/simple-variable-declarations.md)|정수 계열 또는 부동 소수점 형식의 단일 값 변수|
|[배열](../c-language/array-declarations.md)|형식이 같은 요소의 컬렉션으로 구성된 변수|
|[포인터](../c-language/pointer-declarations.md)|다른 변수를 가리키고 값 대신 가변 위치(주소 형태)를 포함하는 변수|
|[열거형 변수](../c-language/c-enumeration-declarations.md)|명명된 정수 상수 집합의 값 하나를 보유하는 정수 계열 형식의 단순 변수|
|[구조체](../c-language/structure-declarations.md)|다양한 형식을 가질 수 있는 값의 컬렉션으로 구성된 변수|
|[공용 구조체](../c-language/union-declarations.md)|같은 스토리지 공간을 차지하는 서로 다른 형식의 여러 값으로 구성된 변수|

선언자는 프로그램에 정의될 이름을 지정하는 선언부입니다. <strong>\*</strong>(포인터) 및 Microsoft 호출 규칙 키워드와 같은 한정자를 포함할 수 있습니다.

**Microsoft 전용**

다음 선언자에서

```C
__declspec(thread) char *var;
```

**`char`** 은 형식 지정자이고 `__declspec(thread)` 및 `*`는 한정자이며 `var`은 식별자의 이름입니다.

**Microsoft 전용 종료**

값의 배열, 값에 대한 포인터 및 지정된 형식의 값을 반환하는 함수를 선언하는 데 선언자를 사용합니다. 선언자는 이 단원의 뒷부분에 설명되어 있는 배열 및 포인터 선언에 나타납니다.

## <a name="syntax"></a>구문

*declarator*:<br/>
&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *declarator*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> *선언자* 를 참조하는 구문은 [C 언어 구문 요약](../c-language/c-language-syntax-summary.md) 또는 [선언 개요](../c-language/overview-of-declarations.md)에서 *선언* 에 대한 구문을 참조하세요.

선언자가 수정되지 않은 식별자로 구성되면 선언되는 항목에 기본 형식이 있습니다. 식별자 왼쪽에 별표(<strong>\*</strong>)가 나타나는 경우 형식은 포인터 형식으로 수정됩니다. 식별자 뒤에 대괄호( **[ ]** )가 올 경우 형식은 배열 형식으로 수정됩니다. 식별자 뒤에 괄호가 올 경우 형식은 함수 형식으로 수정됩니다. 선언 내에서 우선 순위를 해석하는 방법에 대한 자세한 내용은 [더 복잡한 선언자 해석](../c-language/interpreting-more-complex-declarators.md)을 참조하세요.

각 선언자는 하나 이상의 식별자를 선언합니다. 선언이 완전하려면 선언자에 형식 지정자가 포함되어야 합니다. 형식 지정자는 배열 형식의 요소 형식, 포인터 형식으로 처리되는 개체의 형식 또는 함수의 반환 형식을 제공합니다.

[배열](../c-language/array-declarations.md) 및 [포인터](../c-language/pointer-declarations.md) 선언에 대해서는 이 단원의 뒷부분에 자세히 설명되어 있습니다. 다음 예제에서는 몇 가지 간단한 형태의 선언자를 보여 줍니다.

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Microsoft 전용**

Microsoft C 컴파일러는 산술, 구조체 또는 공용 구조체 형식을 수정할 수 있는 선언자의 수를 제한하지 않습니다. 이 수는 사용 가능한 메모리에 의해서만 제한됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[선언 및 형식](../c-language/declarations-and-types.md)

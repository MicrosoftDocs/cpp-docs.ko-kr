---
description: '자세한 정보: 포인터 선언'
title: 포인터 선언
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 3c1670d1dd86e7df7f164e357ff99f3ed31e7339
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195920"
---
# <a name="pointer-declarations"></a>포인터 선언

*포인터 선언* 은 포인터 변수의 이름을 지정하고 변수가 가리키는 개체의 형식을 지정합니다. 포인터로 선언된 변수는 메모리 주소를 갖습니다.

## <a name="syntax"></a>구문

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*type-specifier* 는 개체의 형식을 제공합니다. 개체 형식은 기본, 구조체 또는 공용 구조체 형식일 수 있습니다. 포인터 변수는 함수, 배열 및 다른 포인터를 가리킬 수도 있습니다. 더 복잡한 포인터 형식의 선언 및 해석에 대한 자세한 내용은 [더 복잡한 선언자 해석](../c-language/interpreting-more-complex-declarators.md)을 참조하세요.

*type-specifier* 를 **`void`** 로 만들면 포인터가 참조할 형식 지정이 지연됩니다. 그러한 항목이 " **`void`** 에 대한 포인터"로 참조되고 `void *`로 작성됩니다. *void* 에 대한 포인터로 선언된 변수를 사용하여 모든 형식의 개체를 가리킬 수 있습니다. 그러나 포인터나 포인터가 가리키는 개체에 대해 작업을 수행하려면 대개 포인터가 가리키는 형식이 각 작업에 대해 명시적으로 지정되어야 합니다. ( **`char`** <strong>\*</strong> 형식 및 **`void`** <strong>\*</strong> 형식의 변수는 형식 캐스팅 없이 대입과 호환됩니다.) 형식 캐스팅을 사용하여 이러한 변환을 수행할 수 있습니다. 자세한 내용은 [형식 캐스팅 변환](../c-language/type-cast-conversions.md)을 참조하세요.

*type-qualifier* 는 **`const`** 또는 **`volatile`** 이거나 둘 다일 수 있습니다. 이 형식 한정자는 각각 프로그램 자체에서 포인터를 수정할 수 없거나( **`const`** ), 프로그램 제어를 벗어나 일부 프로세스에서 포인터를 올바르게 수정할 수 있도록( **`volatile`** ) 지정합니다. ( **`const`** 및 **`volatile`** 에 대한 자세한 내용은 [형식 한정자](../c-language/type-qualifiers.md)를 참조하세요.)

*declarator* 는 변수 이름을 지정하며 형식 한정자를 포함할 수 있습니다. 예를 들어, *declarator* 가 배열을 나타낼 경우 포인터 형식이 배열에 대한 포인터로 수정됩니다.

구조체, 공용 구조체 또는 열거형 형식을 정의하기 전에 구조체, 공용 구조체 또는 열거형 형식에 대한 포인터를 선언할 수 있습니다. 아래의 예제와 같이 구조체 또는 공용 구조체 태그를 사용하여 포인터를 선언합니다. 컴파일러가 구조체나 공용 구조체의 크기를 몰라도 포인터 변수의 공간을 할당할 수 있으므로 이러한 선언이 허용됩니다.

## <a name="examples"></a>예

다음 예제에서는 포인터 선언을 보여 줍니다.

```
char *message; /* Declares a pointer variable named message */
```

*message* 포인터는 형식이 **`char`** 인 변수를 가리킵니다.

```
int *pointers[10];  /* Declares an array of pointers */
```

*pointers* 배열에 10개의 요소가 있고 각 요소는 형식이 **`int`** 인 변수의 포인터입니다.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

*pointer* 변수는 요소가 10개인 배열을 가리킵니다. 이 배열의 각 요소는 **`int`** 형식입니다.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

*x* 포인터를 수정하여 다른 **`int`** 값을 가리킬 수 있지만 포인터가 가리키는 값은 수정할 수 없습니다.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

이 선언의 *y* 변수는 **`int`** 값에 대한 상수 포인터로 선언됩니다. 포인터가 가리키는 값은 수정할 수 있지만 포인터 자체는 항상 같은 위치, 즉 *fixed_object* 주소를 가리켜야 합니다. 마찬가지로 *z* 는 상수 포인터지만 프로그램으로 값을 수정할 수 없는 **`int`** 를 가리키도록 선언되기도 합니다. 추가 지정자 **`volatile`** 은 *z* 로 가리킨 **const int** 값을 프로그램으로 수정할 수 없더라도 프로그램과 동시에 실행 중인 프로세스에서 올바르게 수정할 수 있음을 나타냅니다. *w* 선언은 가리킨 값을 프로그램이 변경할 수 없으며 프로그램이 포인터를 수정할 수 없도록 지정합니다.

```
struct list *next, *previous; /* Uses the tag for list */
```

이 예제에서는 구조체 형식 *list* 를 가리키는 두 개의 포인터 변수 *next* 와 *previous* 를 선언합니다. *list* 형식 정의와 선언의 표시 유형이 같을 경우 이 선언이 *list* 구조체 형식의 정의 앞에 나타날 수 있습니다(다음 예제 참조).

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

*line* 변수에 이름이 *list* 인 구조체 형식이 있습니다. *list* 구조체 형식에는 세 가지 멤버가 있습니다. 첫째 멤버는 **`char`** 값에 대한 포인터이고 둘째 멤버는 **`int`** 값이며 셋째 멤버는 다른 *list* 구조체에 대한 포인터입니다.

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

*record* 변수에는 *id* 구조체 형식이 있습니다. *pname* 은 이름이 *name* 인 다른 구조체 형식에 대한 포인터로 선언됩니다. *name* 형식이 정의되기 전에 이 선언이 나타날 수 있습니다.

## <a name="see-also"></a>참조

[선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)

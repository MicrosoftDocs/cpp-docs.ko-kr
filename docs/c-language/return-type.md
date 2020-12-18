---
description: '자세한 정보: 반환 형식'
title: 반환 형식
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 5f4c3c59dd5d89a3c9083eb177bb72e4049ab454
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293029"
---
# <a name="return-type"></a>반환 형식

함수의 반환 형식은 함수에 의해 반환된 값의 크기와 형식을 설정하며, 아래 구문에 나타난 type-specifier에 대응됩니다.

## <a name="syntax"></a>구문

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* 는 Microsoft 전용임 \*/

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int8`**  /\* Microsoft 전용 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int16`**  /\* Microsoft 전용 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int32`**  /\* Microsoft 전용 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int64`**  /\* Microsoft 전용 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-specifier* 는 모든 기본, 구조체 또는 공용 구조체 형식을 지정할 수 있습니다. *type-specifier* 를 포함하지 않는 경우 반환 형식은 **`int`** 로 간주됩니다.

함수 정의에 지정된 반환 형식은 프로그램의 다른 곳에서 선언된 함수의 반환 형식과 일치해야 합니다. 함수는 식을 포함하는 **`return`** 문이 실행될 때 값을 반환합니다. 식이 계산되고 반환 값 형식으로 변환되고(필요한 경우) 함수가 호출된 지점으로 돌아갑니다. 함수가 반환 형식 **`void`** 로 선언되는 경우 식이 포함된 Return 문은 경고를 발생시키고 식은 계산되지 않습니다.

다음 예제에서는 함수 반환 값을 보여 줍니다.

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

이 예제에서는 **`typedef`** 선언으로 `STUDENT` 형식을 정의하고 `sortstu` 함수가 `STUDENT` 반환 형식을 가지도록 정의합니다. 함수는 해당 구조체 인수 둘 중 하나를 선택하고 반환합니다. 함수에 대한 후속 호출에서 컴파일러는 인수 형식이 `STUDENT`인지 확인합니다.

> [!NOTE]
> 전체 구조체가 아니라 포인터를 구조체에 전달하면 효율성을 향상시킬 수 있습니다.

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

이 예제에서는 문자 배열에 대한 포인터를 반환하는 함수를 정의합니다. 함수는 두 문자 배열(문자열)을 인수로 사용하고 두 문자열 중 짧은 문자열에 대한 포인터를 반환합니다. 배열에 대한 포인터는 배열 요소의 처음을 가리키고 해당 형식을 갖고 있으므로 함수의 반환 형식은 **`char`** 형식에 대한 포인터입니다.

인수 및 반환 값에 대한 올바른 형식 검사를 사용할 수 있도록 프로토타입을 권장하지만, 이를 호출하기 전에 **`int`** 반환 형식의 함수를 선언할 필요가 없습니다.

## <a name="see-also"></a>참조

[C 함수 정의](../c-language/c-function-definitions.md)

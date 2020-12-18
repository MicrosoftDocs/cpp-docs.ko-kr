---
description: '자세한 정보: 공용 구조체 선언'
title: 공용 구조체 선언
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: c544a4d92f452415fdd03ccef51d49f69e2b5dae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258826"
---
# <a name="union-declarations"></a>공용 구조체 선언

"공용 구조체 선언"은 변수 값의 집합을 지정하고 공용 구조체 이름을 지정하는 태그를 선택적으로 지정합니다. 변수 값을 공용 구조체의 "멤버"라고 하며 변수 값은 다른 형식이 될 수 있습니다. 공용 구조체는 다른 언어의 "가변 레코드"와 비슷합니다.

## <a name="syntax"></a>구문

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union* *identifier*<sub>opt</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union* *identifier*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`union`**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

공용 구조체 내용은 다음과 같이 정의됩니다.

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list*  **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator-list*  **,**  *struct-declarator*

**`union`** 형식의 변수는 해당 형식으로 정의된 값 중 하나를 저장합니다. 구조체 및 공용 구조체 선언에 같은 규칙이 적용됩니다. 공용 구조체에 비트 필드를 포함할 수도 있습니다.

공용 구조체 멤버는 불완전한 형식, **`void`** 형식 또는 함수 형식을 가질 수 없습니다. 따라서 멤버는 공용 구조체의 인스턴스가 될 수 없지만 선언할 공용 구조체 형식의 포인터가 될 수는 있습니다.

공용 구조체 형식 선언은 템플릿만 가능합니다. 변수를 선언할 때까지는 메모리가 예약되지 않습니다.

> [!NOTE]
> 두 형식의 공용 구조체가 선언되고 값이 한 개 저장되지만 다른 형식으로 공용 구조체에 액세스하는 경우 결과를 신뢰할 수 없습니다. 예를 들어, **`float`** 및 **`int`** 의 공용 구조체가 선언됩니다. **`float`** 값이 저장되지만 나중에 **`int`** 로 값에 액세스합니다. 그러면 **`float`** 값의 내부 스토리지에 따라 값이 결정됩니다. 정수 값은 신뢰할 수 없습니다.

## <a name="examples"></a>예

다음은 공용 구조체의 예제입니다.

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

이 예제에서는 `sign` 형식으로 공용 구조체 변수를 정의하며 멤버가 2개 있고 이름이 `number`인 변수를 선언합니다. `svar` 멤버는 부호 있는 정수이고 `uvar` 멤버는 부호 없는 정수입니다. 이 선언을 사용하면 `number`의 현재 값을 부호 있는 값이나 부호 없는 값으로 저장할 수 있습니다. 이 공용 구조체 형식과 연결된 태그는 `sign`입니다.

```C
union               /* Defines a two-dimensional */
{                   /*  array named screen */
    struct
    {
      unsigned int icon : 8;
      unsigned color : 4;
    } window1;
    int screenval;
} screen[25][80];
```

`screen` 배열에 2,000개의 요소가 있습니다. 배열의 각 요소는 멤버 2개(`window1` 및 `screenval`)가 있는 개별 공용 구조체입니다. `window1` 멤버는 비트 필드 멤버 2개(`icon` 및 `color`)가 있는 구조체입니다. `screenval` 멤버는 **`int`** 입니다. 지정된 시간에 각 공용 구조체 요소는 `screenval`로 표현되는 **`int`** 또는 `window1`로 표현되는 구조체를 포함합니다.

**Microsoft 전용**

중첩된 공용 구조체가 다른 구조체나 공용 구조체의 멤버일 경우 익명으로 선언할 수 있습니다. 다음은 이름 없는 공용 구조체의 예제입니다.

```C
struct str
{
    int a, b;
    union            / * Unnamed union */
    {
      char c[4];
      long l;
      float f;
   };
   char c_array[10];
} my_str;
.
.
.
my_str.l == 0L;  /* A reference to a field in the my_str union */
```

특정 시간에 공용 구조체에 포함된 데이터의 형식을 제공하는 필드가 포함된 구조체 안에 공용 구조체가 종종 중첩됩니다. 다음은 이런 공용 구조체 선언의 예제입니다.

```C
struct x
{
    int type_tag;
    union
    {
      int x;
      float y;
    }
}
```

공용 구조체 참조에 대한 자세한 내용은 [구조체 및 공용 구조체 멤버](../c-language/structure-and-union-members.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)

---
title: 일반 선택(C11)
description: Microsoft Visual C 컴파일러에서 사용되는 C11 _Generic 키워드에 대해 설명합니다.
ms.date: 12/9/2020
helpviewer_keywords:
- _Generic keyword [C]
ms.openlocfilehash: de0e840c19186219d53800b9d008d7695b807bc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97348897"
---
# <a name="generic-selection-c11"></a>일반 선택(C11)

**`_Generic`** 키워드를 사용하여 컴파일 시간에 인수의 형식을 기반으로 식을 선택하는 코드를 작성합니다. 이는 인수 형식이 평가할 식을 선택한다는 점을 제외하고 인수 형식이 호출할 함수를 선택하는 C++의 오버로드와 비슷합니다.

예를 들어 식 `_Generic(42, int: "integer", char: "character", default: "unknown");`은 `42`의 형식을 평가하고 목록에서 일치하는 형식 `int`를 검색합니다. 이 형식을 찾아 `"integer"`를 반환합니다.

## <a name="syntax"></a>구문

*`generic-selection`*:\
&nbsp;&nbsp;&nbsp;&nbsp;**`_Generic`** **(** *`assignment-expression`, `assoc-list`* **)**

*`assoc-list`*:\
&nbsp;&nbsp;&nbsp;&nbsp;*`association`*\
&nbsp;&nbsp;&nbsp;&nbsp;*`assoc-list`, `association`*

*`association`*:\
&nbsp;&nbsp;&nbsp;&nbsp;*`type-name`* : *`assignment-expression`*\
&nbsp;&nbsp;&nbsp;&nbsp;**`default`** : *`assignment-expression`*

첫 번째 *`assignment-expression`* 을 제어 식이라고 합니다. 제어 식의 형식은 컴파일 시간에 결정되고 *`assoc-list`* 와 비교되어 평가 및 반환할 식을 찾습니다. 제어 식은 평가되지 않습니다. 예를 들어 `_Generic(intFunc(), int: "integer", default: "error");`은 런타임에 `intFunc()`를 호출하지 않습니다. 

제어 식의 형식이 결정되면 `const`, `volatile` 및 `restrict`은 *`assoc-list`* 와 비교하기 전에 제거됩니다.

`assoc-list`에서 선택되지 않은 항목은 평가되지 않습니다.

## <a name="constraints"></a>제약 조건

- *`assoc-list`* 는 동일한 형식을 두 번 이상 지정할 수 없습니다.
- *`assoc-list`* 는 열거형과 해당 열거형의 기본 형식 같이 서로 호환되는 형식을 지정할 수 없습니다.
- 일반 선택에 기본값이 없는 경우 제어 식에는 일반 연결 목록에 호환되는 형식 이름이 하나만 있어야 합니다.

## <a name="example"></a>예제

**`_Generic`** 을 사용하는 한 가지 방법은 매크로입니다. <tgmath.h> 헤더 파일은 **_Generic** 을 사용하여 인수의 형식에 따라 올바른 수학 함수를 호출합니다. 예를 들어 `cos()`에 대한 매크로는 `cosf()`에 float를 사용하는 호출을 매핑하고, complex double를 사용하는 호출은 `ccos()`에 매핑합니다.

다음 예제에서는 전달되는 인수의 형식을 식별하는 매크로를 작성하는 방법을 보여 줍니다. *`assoc-list`* 에 제어 식과 일치하는 항목이 없는 경우 `"unknown"`을 반환합니다.

```C
// Compile with /std:c11

#include <stdio.h>

/* Get a type name string for the argument x */
#define TYPE_NAME(X) _Generic((X), \
      int: "int", \
      char: "char", \
      double: "double", \
      default: "unknown")

int main()
{
    printf("Type name: %s\n", TYPE_NAME(42.42));

    // The following would result in a compile error because 
    // 42.4 is a double, doesn't match anything in the list, 
    // and there is no default.
    // _Generic(42.4, int: "integer", char: "character"));
}

/* Output:
Type name: double
*/

```

## <a name="see-also"></a>참조

[`/std`(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)\
[형식-제네릭 수학](../c-runtime-library/tgmath.md)
---
description: '자세한 정보: 외부 수준 선언에 대한 스토리지 클래스 지정자'
title: 외부 수준 선언에 대한 스토리지 클래스 지정자
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: a048ebcf6eea87c77cba23ed50ab117d014c95e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296851"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>외부 수준 선언에 대한 스토리지 클래스 지정자

외부 변수는 파일 범위의 변수이며, 함수 외부에서 정의되고 잠재적으로 많은 함수에서 사용될 수 있습니다. 함수는 외부 수준에서만 정의될 수 있으므로 중첩될 수 없습니다. 기본적으로 이름이 같은 외부 변수와 함수에 대한 모든 참조는 같은 개체에 대한 참조이며, 이는 외부 링크를 갖고 있다는 의미입니다. ( **`static`** 키워드를 사용하여 이 동작을 재정의할 수 있습니다.)

외부 수준의 변수 선언은 변수의 정의(정의 선언)이거나 다른 곳에서 정의된 변수에 대한 참조(참조 선언)입니다.

변수의 초기화(암시적 또는 명시적)도 수행하는 외부 변수 선언은 변수의 정의 선언입니다. 외부 수준의 정의는 다음과 같은 형태일 수 있습니다.

- **`static`** 스토리지 클래스 지정자를 사용하여 선언하는 변수. [초기화](../c-language/initialization.md)에 설명된 대로 **`static`** 변수를 상수 식으로 명시적으로 초기화할 수 있습니다. 이니셜라이저를 생략할 경우 변수는 기본적으로 0으로 초기화됩니다. 예를 들어 다음 두 문은 모두 변수 `k`의 정의로 간주됩니다.

    ```C
    static int k = 16;
    static int k;
    ```

- 외부 수준에서 명시적으로 초기화하는 변수. 예를 들어 `int j = 3;`은 변수 `j`의 정의입니다.

외부 수준(즉, 모든 함수의 외부)의 변수 선언에서 **`static`** 또는 **`extern`** 스토리지 클래스 지정자를 사용할 수도 있고 스토리지 클래스 지정자를 완전히 생략할 수도 있습니다. 외부 수준에서는 **`auto`** 및 **`register`** *`storage-class-specifier`* 터미널을 사용할 수 없습니다.

변수가 외부 수준에서 정의되면 변환 단위의 나머지 부분 전체에서 표시됩니다. 변수는 동일한 소스 파일에서 해당 변수의 선언 이전에 표시되지 않습니다. 또한 변수는 아래에 설명된 대로 참조 선언에서 표시되도록 지정하지 않는 한 프로그램의 다른 소스 파일에서도 표시되지 않습니다.

**`static`** 과 관련된 규칙은 다음과 같습니다.

- **`static`** 키워드 없이 모든 블록 외부에서 선언된 변수는 항상 프로그램 전체에서 그 값을 유지합니다. 특정 변환 단위에 대한 변수의 액세스를 제한하려면 **`static`** 키워드를 사용해야 합니다. 이렇게 하면 변수에 내부 링크가 제공됩니다. 변수를 전체 프로그램에 전역으로 지정하려면 명시적 스토리지 클래스를 생략하거나 **`extern`** 키워드를 사용합니다(다음 목록에 있는 규칙 참조). 이렇게 하면 변수에 외부 링크가 제공됩니다. 내부 및 외부 링크는 [링크](../c-language/linkage.md)에도 설명되어 있습니다.

- 외부 수준의 변수는 프로그램 내에서 한 번만 정의할 수 있습니다. 다른 변환 단위에서 같은 이름과 **`static`** 스토리지 클래스 지정자를 사용하여 또 다른 변수를 정의할 수 있습니다. 각 **`static`** 정의는 자체 변환 단위에서만 표시되므로 충돌이 발생하지 않습니다. 이는 단일 변환 단위의 함수 중에서 공유되어야 하지만 다른 변환 단위에 표시되지 않아야 하는 식별자 이름을 숨기는 데 유용합니다.

- **`static`** 스토리지 클래스 지정자는 함수에도 적용될 수 있습니다. 함수를 **`static`** 으로 선언하는 경우 함수 이름은 함수가 선언된 파일 외부에서 표시되지 않습니다.

**`extern`** 사용에 대한 규칙은 다음과 같습니다.

- **`extern`** 스토리지 클래스 지정자는 다른 곳에 정의된 변수에 대한 참조를 선언합니다. **`extern`** 선언을 사용하여 다른 소스 파일의 정의가 표시되도록 하거나 동일한 소스 파일에서 변수가 변수 선언 이전에 표시되도록 할 수 있습니다. 외부 수준에서 변수에 대한 참조를 선언하면 선언된 참조가 발생하는 변환 단위의 나머지 부분 전체에서 변수가 표시됩니다.

- **`extern`** 참조가 유효하려면 참조하는 변수가 외부 수준에서 한 번만 정의되어야 합니다. 이 정의( **`extern`** 스토리지 클래스를 사용하지 않음)는 프로그램을 구성하는 어떠한 변환 단위에도 포함될 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 외부 선언을 보여 줍니다.

```C
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

이 예제의 두 소스 파일에는 `i`의 외부 선언이 세 개 포함되어 있습니다. 다음 선언만 "정의 선언"입니다.

```C
int i = 3;
```

이 선언은 전역 변수 `i`를 정의하고 초기 값 3으로 초기화합니다. **`extern`** 을 사용한 첫 번째 소스 파일 맨 위에 있는 `i`의 "참조" 선언은 이 전역 변수가 해당 파일에서 정의 선언 이전에 표시되도록 합니다. 두 번째 소스 파일에 있는 `i`의 참조 선언도 이 변수가 해당 소스 파일에서 표시되도록 합니다. 변수의 정의 인스턴스가 변환 단위에서 제공되지 않는 경우 컴파일러는 다음과 같은

```C
extern int x;
```

참조 선언이 있고 다음과 같은

```C
int x = 0;
```

정의 선언이 프로그램의 다른 변환 단위에서 나타난다고 가정합니다.

`main`, `next` 및 `other` 함수 모두 `i`를 증가시키고 인쇄하는 동일한 작업을 수행합니다. 값 4, 5, 6이 인쇄됩니다.

`i` 변수가 초기화되지 않은 경우 자동으로 0으로 설정됩니다. 이 경우에는 값 1, 2, 3이 인쇄됩니다. 변수 초기화에 대한 자세한 내용은 [초기화](../c-language/initialization.md)를 참조하세요.

## <a name="see-also"></a>참조

[C 스토리지 클래스](../c-language/c-storage-classes.md)

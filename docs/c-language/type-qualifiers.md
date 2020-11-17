---
title: 형식 한정자
description: Microsoft Visual C 컴파일러에서 사용되는 C 언어의 형식 한정자를 설명합니다.
ms.date: 11/6/2020
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: dd36aeb5d142eebbd6e4a339fe6c18925a6fd45a
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381612"
---
# <a name="type-qualifiers"></a>형식 한정자

형식 한정자는 두 속성 중 하나를 식별자에 제공합니다. **`const`** 형식 한정자는 개체를 수정할 수 없는 것으로 선언합니다. **`volatile`** 형식 한정자가 선언하는 항목의 값은 해당 항목이 나타나는 프로그램의 제어를 벗어난 요소(예: 동시에 실행되는 스레드)가 올바르게 변경할 수 있습니다.

**`const`** , **`restrict`** , **`volatile`** 형식 한정자는 선언에서 한 번만 나타날 수 있습니다. 형식 한정자는 모든 형식 지정자와 함께 나타날 수 있지만, 여러 항목 선언에서 첫 번째 쉼표 뒤에는 나타날 수 없습니다. 예를 들어 다음 선언은 올바릅니다.

```c
typedef volatile int VI;
const int ci;
```

다음 선언은 올바르지 않습니다.

```c
typedef int *i, volatile *vi;
float f, const cf;
```

형식 한정자는 식에서 l-value로 식별자에 액세스하는 경우에만 관련이 있습니다. l-value와 식에 대한 자세한 내용은 [L-Value 및 R-Value 식](../c-language/l-value-and-r-value-expressions.md)을 참조하세요.

## <a name="syntax"></a>구문

*`type-qualifier`*:\
&emsp;**`const`**\
&emsp;**`restrict`**\
&emsp;**`volatile`**

## <a name="const-and-volatile"></a>`const` 및 `volatile`

다음은 올바른 **`const`** 및 **`volatile`** 선언입니다.

```c
int const *p_ci;      // Pointer to constant int
int const (*p_ci);   // Pointer to constant int
int *const cp_i;     // Constant pointer to int
int (*const cp_i);   // Constant pointer to int
int volatile vint;     // Volatile integer
```

배열 형식의 지정에 형식 한정자가 포함된 경우 배열 형식이 아니라 요소가 한정됩니다. 함수 형식의 지정에 한정자가 포함된 경우에는 동작이 정의되어 있지 않습니다. **`volatile`** 및 **`const`** 는 값의 범위 또는 개체의 산술 속성에 영향을 미치지 않습니다.

- **`const`** 키워드를 사용하여 모든 기본 또는 집계 형식을 수정하거나 모든 형식의 개체에 대한 포인터 또는 **`typedef`** 를 수정할 수 있습니다. 항목이 **`const`** 형식 한정자만 사용하여 선언되는 경우 형식은 **const int** 로 간주됩니다. **`const`** 변수는 초기화되거나 스토리지의 읽기 전용 영역에 배치될 수 있습니다. **`const`** 키워드를 사용하여 포인터를 **`const`** 로 선언하면 함수가 어떤 식으로든 포인터를 변경하지 못하게 되므로 유용합니다.

- 컴파일러는 프로그램의 어떠한 지점에서도 **`volatile`** 변수의 값을 사용하거나 수정하는 알 수 없는 프로세스에 의해 해당 변수가 액세스될 수 있다고 가정합니다. 명령줄에 지정된 최적화와 관계없이 아무 영향이 없는 것처럼 보이는 경우에도 **`volatile`** 변수에 대한 각 할당 또는 참조를 위한 코드를 생성해야 합니다.

**`volatile`** 만 사용되는 경우에는 **`int`** 가 가정됩니다. **`volatile`** 형식 지정자를 사용하여 특별한 메모리 위치에 대한 안정적인 액세스를 제공할 수 있습니다. 신호 처리기, 동시에 실행되는 프로그램 또는 메모리 매핑된 I/O 제어 레지스터와 같은 특수 하드웨어가 액세스하거나 변경할 수 있는 데이터 개체와 함께 **`volatile`** 을 사용합니다. 변수의 수명 동안 변수를 **`volatile`** 로 선언하거나 단일 참조를 **`volatile`** 로 캐스팅할 수 있습니다.

- 항목이 **`const`** 이면서 **`volatile`** 일 수도 있습니다. 이 경우 항목은 자체 프로그램에서 올바르게 수정될 수 없지만 비동기 프로세스에서 수정될 수 있습니다.
 
## `restrict`

C99에 도입된 **`restrict`** 형식 한정자는 포인터 선언에 적용할 수 있습니다. 이 형식 한정자는 포인터가 가리키는 것이 아닌 포인터를 한정합니다.

**`restrict`** 는 현재 범위에 있는 다른 포인터가 동일한 메모리 위치를 참조하지 않는 컴파일러에 대한 최적화 힌트입니다. 즉, 포인터 또는 포인터에서 파생된 값(예: 포인터 + 1)만 포인터의 수명 동안 개체에 액세스하는 데 사용됩니다. 이렇게 하면 컴파일러가 더 최적화된 코드를 생성할 수 있습니다. C++에는 이와 동등한 메커니즘인 [`__restrict`](../cpp/extension-restrict.md)가 있습니다.

**`restrict`** 는 사용자와 컴파일러 간의 계약임을 명심하세요. **`restrict`** 로 표시된 포인터에 별칭을 지정하면 결과가 정의되지 않습니다.

다음은 **`restrict`** 를 사용하는 예제입니다.

```c
void test(int* restrict first, int* restrict second, int* val)
{
    *first += *val;
    *second += *val;
}

int main()
{
    int i = 1, j = 2, k = 3;
    test(&i, &j, &k);

    return 0;
}

// Marking union members restrict tells the compiler that
// only z.x or z.y will be accessed in any scope, which allows
// the compiler to optimize access to the members.
union z 
{
    int* restrict x;
    double* restrict y;
};
```

## <a name="see-also"></a>참조

[`/std`(언어 표준 버전 지정)](../build/reference/std-specify-language-standard-version.md)\
[선언 및 형식](../c-language/declarations-and-types.md)

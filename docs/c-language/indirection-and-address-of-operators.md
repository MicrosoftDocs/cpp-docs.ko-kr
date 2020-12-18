---
description: '자세한 정보: 연산자 주소 및 간접 참조'
title: 연산자 주소 및 간접 참조
ms.date: 02/16/2018
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
ms.openlocfilehash: bd05d9eee4a453d9d99198a1a8481fcebcf103dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137595"
---
# <a name="indirection-and-address-of-operators"></a>연산자 주소 및 간접 참조

단항 간접 참조 연산자( __&#42;__ )는 포인터를 통해 값에 간접적으로 액세스합니다. 피연산자는 포인터 형식이어야 합니다. 연산 결과는 피연산자가 가리키는 주소에 있는 값입니다. 결과의 형식은 피연산자가 표시하는 형식과 동일합니다.

간접 참조 연산자의 결과는 피연산자가 *형식에 대한 포인터* 형식인 경우 *형식* 입니다. 피연산자가 함수를 가리키는 경우 결과는 함수 지정자입니다. 개체를 가리키는 경우 결과는 개체를 지정하는 Ivalue입니다.

포인터 값이 유효하지 않으면, 간접 참조 연산자의 결과는 정의되지 않습니다. 다음은 포인터 값을 무효화하는 가장 일반적인 조건 중 일부입니다.

- 포인터가 null 포인터입니다.

- 포인터는 참조 시에 수명이 종료된 개체(예: 범위를 벗어나거나 할당이 취소된 개체)의 주소를 지정합니다.

- 포인터가 가리키는 개체의 형식에 대해 부적절하게 정렬된 주소를 지정합니다.

- 포인터가 실행 중인 프로그램에서 사용되지 않는 주소를 지정합니다.

단항 주소 연산자( **&** )는 해당 피연산자의 주소를 제공합니다. 피연산자는 __레지스터__ 로 선언되지 않고 비트 필드가 아닌 개체를 지정하는 lvalue이거나, 단항 __&#42;__ 연산자 또는 배열 역참조( __&#91;&#93;__ ) 연산자 또는 함수 지정자여야 합니다. 형식의 결과는 *형식* 의 피연산자에 대한 형식 *형식에 대한 포인터* 입니다.

피연산자가 단항 __&#42;__ 연산자의 결과이면, 연산자가 평가되지 않고 결과는 둘 다 생략된 것과 같습니다. 결과는 lvalue가 아니며 연산자에 대한 제약 조건이 여전히 적용됩니다. 피연산자가 __&#91;&#93;__ 연산자의 결과인 경우, __&__ 연산자도 __&#91;&#93;__ 연산자에 의해 함축된 단항 __&#42;__ 는 평가되지 않습니다. 결과는 __&__ 연산자를 제거하고 __&#91;&#93;__ 연산자를 __+__ 연산자로 변경하는 것과 동일한 효과가 있습니다. 그렇지 않은 경우 결과는 피연산자가 지정한 개체 또는 함수에 대한 포인터입니다.

## <a name="examples"></a>예

다음 예에서는 이러한 일반적인 선언을 사용합니다.

```C
int *pa, x;
int a[20];
double d;
```

이 명령문은 주소 연산자( **&** )를 사용하여 `a` 배열의 여섯 번째 요소의 주소를 가져옵니다. 결과는 포인터 변수 `pa`에 저장됩니다.

```C
pa = &a[5];
```

이 예제에서는 간접 참조 연산자( __&#42;__ )를 사용하여 `pa`에 저장된 주소의 **`int`** 값에 액세스합니다. 값이 정수 변수 `x`에 할당됩니다.

```C
x = *pa;
```

이 예는 간접 참조 연산자를 `x`의 주소에 적용한 결과가 `x`와 동일하다는 것을 나타냅니다.

```C
assert( x == *&x );
```

이 예는 함수에 대한 포인터를 선언하는 동일한 방법을 보여줍니다.

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

함수 `roundup`이 선언되면 `roundup`에 대한 두 개의 포인터가 선언되고 초기화됩니다. 첫 번째 포인터, `proundup`은 해당 함수의 이름만을 사용하여 초기화되지만 두 번째 포인터, `pround`는 초기화 시 주소 연산자를 사용합니다. 초기화는 동일합니다.

## <a name="see-also"></a>참조

[간접 참조 연산자: &#42;](../cpp/indirection-operator-star.md)<br/>
[주소 연산자: &](../cpp/address-of-operator-amp.md)

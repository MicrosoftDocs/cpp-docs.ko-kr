---
description: '자세한 정보: 아래 첨자 연산자 []'
title: 첨자 연산자 []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: e11e94bdf516d830020c4844be2a4c3bfc4a8774
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221204"
---
# <a name="subscript-operator-"></a>첨자 연산자 []

## <a name="syntax"></a>구문

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>설명

후 위 식 (기본 식이 될 수도 있음) 다음에 첨자 연산자 **[]** 를 지정 하면 배열 인덱싱이 지정 됩니다.

C + +/CLI의 관리 되는 배열에 대 한 자세한 내용은 [배열](../extensions/arrays-cpp-component-extensions.md)을 참조 하세요.

일반적으로 *후 위 식* 으로 표시 되는 값은 배열 식별자와 같은 포인터 값 이며 *expression* 은 정수 계열 값 (열거형 형식 포함)입니다. 그러나 구문적 요구 사항은 식 중 하나가 포인터 형식이고 다른 하나는 정수 계열 형식이어야 한다는 것 밖에 없습니다. 따라서 정수 계열 값은 *후 위 식* 위치에 있을 수 있으며 포인터 값은 *식* 또는 첨자 위치의 대괄호 안에 있을 수 있습니다. 다음과 같은 코드 조각을 생각해 봅시다.

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

위의 예제에서 `nArray[2]` 식은 `2[nArray]`와 동일합니다. 그 이유는 아래 첨자 식의 결과가에서 제공 되기 때문입니다 `e1[e2]` .

`*((e2) + (e1))`

식으로 생성 되는 주소는 *e1* 주소에서 *e2* 바이트가 아닙니다. 대신 주소는 *e2* 배열에서 다음 개체를 생성 하도록 크기를 조정 합니다. 예를 들어:

```cpp
double aDbl[2];
```

및의 주소 `aDb[0]` 는 `aDb[1]` 8 바이트 떨어져 있습니다. 즉, 형식의 개체 크기입니다 **`double`** . 개체 형식에 따른 이러한 크기 조정은 c + + 언어에 의해 자동으로 수행 되며 더하기 [연산자](../cpp/additive-operators-plus-and.md) 에서 정의 되며 포인터 형식의 피연산자에 대 한 더하기 및 빼기가 설명 됩니다.

첨자 식에는 다음과 같이 여러 첨자가 있을 수도 있습니다.

*expression1* **[** *식 2* **] [** *expression3* **]** ...

첨자 식은 왼쪽에서 오른쪽으로 연결합니다. 맨 왼쪽 첨자 식인 *expression1* **[** *expression2* **]** 이 먼저 계산됩니다. *expression1* 및 *expression2* 를 추가한 결과인 주소는 포인터 식을 형성합니다. 그런 다음 이 포인터 식에 *expression3* 이 추가되어 새 포인터 식을 형성하고 마지막 첨자 식이 추가될 때까지 계속됩니다. <strong>\*</strong>마지막 포인터 값이 배열 형식의 주소를 지정 하지 않는 한 간접 참조 연산자 ()는 마지막 첨자 식이 계산 된 후에 적용 됩니다.

여러 첨자가 포함된 식은 다차원 배열의 요소를 참조합니다. 다차원 배열은 요소가 배열인 배열입니다. 예를 들어 3차원 배열의 첫 번째 요소는 2차원 배열입니다. 다음 예제에서는 간단한 2차원 문자 배열을 선언 및 초기화합니다.

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>양수 및 음수 아래 첨자

배열의 첫 번째 요소는 요소 0입니다. C + + 배열의 범위는 *배열*[0]에서 *배열*[*크기* -1] 사이입니다. 하지만 C++는 양수 및 음수 첨자를 지원합니다. 음수 첨자는 배열 경계 내에 속해야 하며, 그렇지 않으면 결과를 예측할 수 없습니다. 다음 코드에서는 양수 및 음수 배열 첨자를 보여줍니다.

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

마지막 줄의 음수 첨자는 **`int`** 메모리에서 배열의 원점 보다 낮은 주소 256 위치를 가리키기 때문에 런타임 오류가 발생할 수 있습니다. 포인터는 `midArray` 의 중간으로 초기화 되므로 `intArray` 양수 및 음수 배열 인덱스를 모두 사용할 수 있습니다 (위험). 배열 첨자 오류는 컴파일 시간 오류를 발생시키지 않지만 예측할 수 없는 결과를 생성합니다.

첨자 연산자는 가환적입니다. 따라서 식 *배열*[*index*]와 *index*[*array*]는 첨자 연산자가 오버 로드 되지 않는 한 ( [오버 로드 된 연산자](../cpp/operator-overloading.md)참조) 동일한 것으로 보장 됩니다. 첫 번째 형태가 가장 일반적인 코딩 방법이지만, 둘 다 작동합니다.

## <a name="see-also"></a>참고 항목

[후 위 식](../cpp/postfix-expressions.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[배열](../cpp/arrays-cpp.md)<br/>
[1 차원 배열](../c-language/one-dimensional-arrays.md)<br/>
[다차원 배열](../c-language/multidimensional-arrays-c.md)<br/>

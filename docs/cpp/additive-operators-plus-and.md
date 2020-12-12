---
description: '자세히 알아보기: 덧셈 연산자: + 및-'
title: '가감 연산자: + 및 -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: f87a8682b6f282668c168262cd28230745cb4402
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288375"
---
# <a name="additive-operators--and--"></a>가감 연산자: + 및 -

## <a name="syntax"></a>구문

```
expression + expression
expression - expression
```

## <a name="remarks"></a>설명

가감 연산자는 다음과 같습니다.

- 더하기 ( **+** )

- 빼기 ( **-** )

이 이항 연산자는 왼쪽에서 오른쪽으로 연결됩니다.

가감 연산자는 산술 또는 포인터 형식의 피연산자를 사용합니다. 더하기 () 연산자의 결과는 **+** 피연산자의 합계입니다. 빼기 () 연산자의 결과는 **-** 피연산자 간의 차이입니다. 피연산자 중 하나 이상이 포인터인 경우 함수가 아닌 개체에 대한 포인터여야 합니다. 피연산자가 둘 다 포인터인 경우 둘 다 동일한 배열의 개체에 대한 포인터가 아니면 결과는 의미가 없습니다.

가감 연산자는 *산술*, *정수 계열* 및 *스칼라* 형식의 피연산자를 사용 합니다. 이러한 형식은 다음 표에 정의되어 있습니다.

### <a name="types-used-with-additive-operators"></a>가감 연산자와 함께 사용되는 형식

|유형|의미|
|----------|-------------|
|*산술*|정수 계열 및 부동 형식을 전체적으로 "산술" 형식이라고 합니다.|
|*비정*|모든 크기(long, short)의 char 및 int 형식과 열거형은 "정수 계열" 형식입니다.|
|*스칼라(scalar)*|스칼라 피연산자는 산술 또는 포인터 형식의 피연산자입니다.|

이러한 연산자의 올바른 조합은 다음과 같습니다.

*산술*  +  *산술*

*스칼라*  +  *정수 계열*

*정수 계열*  +  *스칼라*

*산술*  -  *산술*

*스칼라*  -  *스칼라*

더하기와 빼기는 동등한 연산이 아닙니다.

두 피연산자가 모두 산술 형식이 면 [표준 변환](standard-conversions.md) 에서 설명 하는 변환이 피연산자에 적용 되며 결과는 변환 된 형식입니다.

## <a name="example"></a>예제

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>포인터 더하기

더하기 연산에서 피연산자 중 하나가 개체 배열에 대한 포인터인 경우 다른 피연산자는 정수 계열 형식이어야 합니다. 결과는 원래 포인터와 형식이 같으며 다른 배열 요소를 가리키는 포인터입니다. 다음 코드 조각에서는 이 개념을 보여 줍니다.

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

정수 계열 값 1이 `pIntArray`에 추가되지만 이는 "주소에 1을 추가"하라는 의미가 아니라 "배열의 다음 개체(2바이트 또는 `sizeof( int )`만큼 떨어져 있음)를 가리키도록 포인터를 조정"하라는 의미합니다.

> [!NOTE]
> `pIntArray = pIntArray + 1` 형태의 코드는 C++ 프로그램에서 거의 발견되지 않습니다. 증분을 수행하려면 `pIntArray++` 또는 `pIntArray += 1` 형태를 사용하는 것이 좋습니다.

## <a name="pointer-subtraction"></a>포인터 빼기

두 피연산자가 모두 포인터인 경우 빼기의 결과는 피연산자 간 배열 요소의 차이입니다. 빼기 식은 형식의 부호 있는 정수 결과 `ptrdiff_t` (표준 포함 파일에 정의 됨)를 생성 \<stddef.h> 합니다.

피연산자 중 하나가 두 번째 피연산자라면 정수 계열 형식이 될 수 있습니다. 빼기 결과는 원래 포인터와 동일한 형식입니다. 빼기 값은 (*n*  -  *i*) 번째 배열 요소에 대 한 포인터입니다. 여기서 *n* 은 원래 포인터가 가리키는 요소이 고 *i* 는 두 번째 피연산자의 정수 계열 값입니다.

## <a name="see-also"></a>참고 항목

[이항 연산자가 있는 식](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 가감 연산자](../c-language/c-additive-operators.md)

---
description: '자세한 정보: 왼쪽 시프트 및 오른쪽 시프트 연산자 ( &gt; &gt; 및 &lt; &lt; )'
title: 왼쪽 시프트 및 오른쪽 시프트 연산자 ( &gt; &gt; 및 &lt; &lt; )
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: e13333d178fdfbb44631b9a2aced9ed2a48ad871
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321020"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>왼쪽 시프트 및 오른쪽 시프트 연산자 ( &gt; &gt; 및 &lt; &lt; )

비트 시프트 연산자는 시프트 식의 비트를 오른쪽으로 이동 하는 오른쪽 시프트 연산자 ( **&gt;&gt;** )와  **&lt;&lt;** *시프트 식* 의 비트를 왼쪽으로 이동 하는 왼쪽 시프트 연산자 ()입니다. <sup>1</sup>

## <a name="syntax"></a>Syntax

> *시프트 식* `<<` *가산 식*\
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>설명

> [!IMPORTANT]
> 다음 설명 및 예제는 x86 및 x64 아키텍처에 대해 Windows에서 유효 합니다. 왼쪽 시프트 및 오른쪽 시프트 연산자의 구현은 Windows에서 ARM 장치에 크게 차이가 있습니다. 자세한 내용은 [HELLO ARM](https://devblogs.microsoft.com/cppblog/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c/) 블로그 게시물의 "시프트 연산자" 섹션을 참조 하세요.

## <a name="left-shifts"></a>왼쪽 시프트

왼쪽 시프트 연산자를 통해 *시프트 식* 의 비트가 왼쪽으로 이동 하 여 *가산 식* 으로 지정 된 위치 수 만큼 이동 합니다. 시프트 연산으로 비워진 비트 위치는 0으로 채워집니다. 왼쪽 시프트는 논리 시프트입니다(부호 비트를 포함해 끝에서 벗어나 이동한 비트는 무시됨). 비트 시프트의 종류에 대 한 자세한 내용은 [비트 시프트](https://en.wikipedia.org/wiki/Bitwise_shift)를 참조 하세요.

다음 예제에서는 부호 없는 숫자를 사용하는 왼쪽 시프트 연산을 보여 줍니다. 예제에서는 값을 비트 집합으로 나타내어 비트에서 어떤 일이 발생하는지 보여 줍니다. 자세한 내용은 [bitset 클래스](../standard-library/bitset-class.md)를 참조 하세요.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

부호 비트가 영향을 받도록 부호 있는 숫자를 왼쪽 시프트하면 결과가 정의되지 않습니다. 다음 예제에서는 1 비트가 부호 비트 위치로 왼쪽 이동 될 때 발생 하는 상황을 보여 줍니다.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>오른쪽 시프트

오른쪽 시프트 연산자를 통해 *시프트 식* 의 비트 패턴이 *덧셈 식* 으로 지정 된 위치 수 만큼 오른쪽으로 이동 합니다. 부호 없는 숫자의 경우 시프트 연산으로 비워진 비트 위치는 0으로 채워집니다. 부호 있는 숫자의 경우 부호 비트는 비워진 비트 위치를 채우는 데 사용됩니다. 즉, 숫자가 양수이면 0이 사용되고 숫자가 음수이면 1이 사용됩니다.

> [!IMPORTANT]
> 부호 있는 음수의 오른쪽 시프트 결과는 구현에 따라 다릅니다. Microsoft c + + 컴파일러는 부호 비트를 사용 하 여 비워진 비트 위치를 채우지만 다른 구현 에서도 그렇게 할 수 있는 것은 아닙니다.

이 예제에서는 부호 없는 숫자를 사용하는 오른쪽 시프트 연산을 보여 줍니다.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

다음 예제에서는 부호 있는 양수를 사용하는 오른쪽 시프트 연산을 보여 줍니다.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

다음 예제에서는 부호 있는 음수를 사용하는 오른쪽 시프트 연산을 보여 줍니다.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>시프트 및 확장

시프트 연산자 양쪽에 있는 식은 정수 계열 형식이어야 합니다. 정수 계열 확장은 [표준 변환](standard-conversions.md)에 설명 된 규칙에 따라 수행 됩니다. 결과의 형식은 승격 된 *시프트 식* 의 형식과 같습니다.

다음 예제에서 형식의 변수는 **`char`** 로 승격 됩니다 **`int`** .

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>추가 정보

*가감* 식이 음수 이거나 *가감 식* 이 (승격 된) *시프트 식* 의 비트 수보다 크거나 같은 경우 시프트 연산의 결과가 정의 되지 않습니다. *가감 식이* 0 이면 시프트 연산이 수행 되지 않습니다.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>각주

<sup>1</sup> c + + 11 iso 사양 (INCITS/ISO/IEC 14882-2011 [2012]), 섹션 5.8.2 및 5.8.3의 시프트 연산자에 대 한 설명은 다음과 같습니다.

`E1 << E2`의 값은 `E1` 왼쪽 이동된 `E2` 비트 위치입니다. 비워진 비트는 0으로 채워집니다. `E1`에 부호 없는 형식이 있는 경우 결과 값은 **E1 x 2**<sup>**E2**</sup>이 고, 결과 형식에서 표현할 수 있는 최대값 보다 1이 넘는 모듈로 줄어듭니다. 그렇지 않고 `E1` 에 부호 있는 형식과 음수가 아닌 값이 있고 **E1 × 2**<sup>**E2**</sup> 를 결과 형식의 해당 하는 부호 없는 형식으로 표현할 수 있는 경우 결과 형식으로 변환 된 값은 결과 값입니다. 그렇지 않으면 동작이 정의 되지 않습니다.

`E1 >> E2`의 값은 `E1` 오른쪽 이동된 `E2` 비트 위치입니다. `E1`에 부호 없는 형식이 있거나이 `E1` 부호 있는 형식이 고 음수가 아닌 값을 포함 하는 경우 결과 값은 **E1/2**<sup>**E2**</sup>의 몫의 정수 부분입니다. `E1`이 부호 있는 형식이고 음수인 경우 결과 값은 구현 시 정의됩니다.

## <a name="see-also"></a>참고 항목

[이항 연산자가 있는 식](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 기본 제공 연산자, 우선 순위 및 결합성](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

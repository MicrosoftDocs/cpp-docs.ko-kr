---
description: '자세히 알아보기: break 문 (c + +)'
title: break 문 (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 13efaf55307f7f1d7decaf7cd0039c84b3141fc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229576"
---
# <a name="break-statement-c"></a>break 문 (C++)

**`break`** 문이 표시 되는 가장 가까운 바깥쪽 루프 또는 조건문의 실행을 종료 합니다. 제어는 종료된 문 뒤의 문이 있는 경우 전달됩니다.

## <a name="syntax"></a>구문

```
break;
```

## <a name="remarks"></a>설명

**`break`** 문은 조건문과 [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)및 [](../cpp/switch-statement-cpp.md) [while](../cpp/while-statement-cpp.md) loop 문을 사용 하 여 사용 됩니다.

문에서 문은 **`switch`** **`break`** 프로그램이 문 외부의 다음 문을 실행 하도록 합니다 **`switch`** . 문이 없으면 **`break`** 절을 포함 하 여 일치 하는 **`case`** 레이블의 끝에 있는 모든 문이 **`switch`** **`default`** 실행 됩니다.

루프에서 **`break`** 문은 가장 가까운 바깥쪽 **`do`** , 또는 문의 실행을 종료 **`for`** **`while`** 합니다. 종료된 문 뒤에 문이 있는 경우 제어가 해당 문으로 전달됩니다.

중첩 된 문 내에서 **`break`** 문은 **`do`** **`for`** **`switch`** 바로이를 둘러싼,, 또는 **`while`** 문만 종료 합니다. **`return`** 또는 문을 사용 하 여 **`goto`** 보다 깊게 중첩 된 구조에서 컨트롤을 전송할 수 있습니다.

## <a name="example"></a>예제

다음 코드에서는 루프에서 문을 사용 하는 방법을 보여 줍니다 **`break`** **`for`** .

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

다음 코드에서는 **`break`** **`while`** 루프와 루프에서를 사용 하는 방법을 보여 줍니다 **`do`** .

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

다음 코드에서는 switch 문에서를 사용 하는 방법을 보여 줍니다 **`break`** . 각 사례를 **`break`** 개별적으로 처리 하려는 경우에는 항상를 사용 해야 합니다 .을 사용 하지 않는 경우 **`break`** 코드 실행은 다음 사례로 이동 합니다.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>참고 항목

[점프 문](../cpp/jump-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[continue 문](../cpp/continue-statement-cpp.md)

---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4868'
title: 컴파일러 경고 C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: 66b6673dc1981351aa25a7ce6c0b9bc30bdf82c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315012"
---
# <a name="compiler-warning-level-4-c4868"></a>컴파일러 경고 (수준 4) C4868

> '_file_(*line_number*) ' 컴파일러는 중괄호로 묶인 이니셜라이저 목록에서 왼쪽에서 오른쪽으로 계산 순서를 적용할 수 없습니다.

중괄호로 묶인 이니셜라이저 목록의 요소는 왼쪽에서 오른쪽 순서로 계산 됩니다. 컴파일러가이 순서를 보장할 수 없는 두 가지 경우가 있습니다. 첫 번째는 일부 요소가 값으로 전달 되는 개체인 경우입니다. 두 번째는를 사용 하 여 컴파일하는 경우 `/clr` 와 일부 요소는 개체의 필드 이거나 배열 요소인 경우입니다. 컴파일러가 왼쪽에서 오른쪽으로 실행 하는 것을 보장할 수 없는 경우 경고 C4868를 내보냅니다.

이 경고는 Visual Studio 2015 업데이트 2에 대해 수행 된 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. Visual Studio 2015 업데이트 2 이전에 컴파일된 코드는 이제 C4868을 생성할 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. `/Wall`을 사용 하 여이 경고를 활성화 합니다.

이 경고를 해결 하려면 먼저 요소를 계산할 때 순서에 종속적인 부작용이 발생할 수 있는 경우와 같이 이니셜라이저 목록 요소를 왼쪽에서 오른쪽으로 계산 해야 하는지 여부를 고려해 야 합니다. 대부분의 경우 요소를 평가 하는 순서는 관찰 가능한 효과를 갖지 않습니다.

계산 순서를 왼쪽에서 오른쪽으로 해야 하는 경우에는 대신 참조로 요소를 전달할 수 있는지를 고려 **`const`** 하세요. 이와 같이 변경 하면 다음 코드 샘플에서 경고가 제거 됩니다.

## <a name="example"></a>예제

이 샘플에서는 C4868를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```

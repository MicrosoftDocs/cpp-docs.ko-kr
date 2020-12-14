---
description: '자세한 정보: 컴파일러 오류 C2672'
title: 컴파일러 오류 C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 2de901eaa416f3ee675c7b09c342de74dc7207fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282083"
---
# <a name="compiler-error-c2672"></a>컴파일러 오류 C2672

> '*function*': 일치 하는 오버 로드 된 함수를 찾을 수 없습니다.

컴파일러가 지정 된 함수와 일치 하는 오버 로드 된 함수를 찾을 수 없습니다. 일치 하는 매개 변수를 사용 하는 함수가 없거나, 일치 하는 함수가 컨텍스트에서 필요한 액세스 가능성을가지고 있지 않습니다.

특정 표준 라이브러리 컨테이너 또는 알고리즘에서 사용 하는 경우 형식은 액세스 가능한 멤버나 컨테이너 또는 알고리즘의 요구 사항을 충족 하는 friend 함수를 제공 해야 합니다. 예를 들어 반복기 형식은에서 파생 되어야 `std::iterator<>` 합니다. 컨테이너 요소 형식에 대해 비교 작업 또는 다른 연산자를 사용 하려면 형식이 왼쪽 피연산자와 오른쪽 피연산자로 모두 고려 되어야 합니다. 형식을 오른쪽 피연산자로 사용 하려면 연산자의 구현이 형식의 멤버가 아닌 함수로 구현 되어야 합니다.

## <a name="example"></a>예제

Visual Studio 2017 이전 버전의 컴파일러는 일부 템플릿 컨텍스트의 정규화 된 이름에 대 한 액세스 검사를 수행 하지 않았습니다. 이는 이름에 액세스할 수 없기 때문에 대체에 실패할 것으로 예상되는 경우 예상되는 SFINAE 동작을 방해할 수 있습니다. 따라서 컴파일러가 연산자의 잘못된 오버로드를 잘못 호출하기 때문에 잠재적으로 런타임에 크래시나 예기치 않은 동작이 발생했을 수 있습니다. Visual Studio 2017에서는 컴파일러 오류가 발생합니다.

이 예제는 Visual Studio 2015에서 컴파일되지만 Visual Studio 2017에서 오류를 발생 시킵니다. 이 문제를 해결 하려면 템플릿 매개 변수 멤버를 평가할 때 액세스할 수 있도록 설정 합니다.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

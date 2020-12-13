---
description: '자세히 알아보기: c + +의 constexpr 람다 식'
title: c + +의 constexpr 람다 식
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 4ff4b3acf4289a74f8b7320620601e0e2284d356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333940"
---
# <a name="constexpr-lambda-expressions-in-c"></a>c + +의 constexpr 람다 식

**Visual Studio 2017 버전 15.3 이상** ( [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)과 함께 사용 가능): **`constexpr`** 상수 식 내에서 캡처 또는 도입 하는 각 데이터 멤버의 초기화가 허용 되는 경우 람다 식을 상수 식에 사용 하거나 사용할 수 있습니다.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

람다는 **`constexpr`** 결과가 함수의 요구 사항을 충족 하는 경우 암시적입니다 **`constexpr`** .

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

람다가 암시적 또는 명시적으로 인 경우이를 **`constexpr`** 함수 포인터로 변환 하면 결과 함수도 **`constexpr`** 다음과 같이 표시 됩니다.

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C + + 표준 라이브러리의 함수 개체](../standard-library/function-objects-in-the-stl.md)<br/>
[함수 호출](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)

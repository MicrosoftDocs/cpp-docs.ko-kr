---
title: c + +의 람다 식 constexpr | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e01f41aaf8b761020f57625e7cbf06f8fba2659
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418902"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr c + +의 람다 식
**Visual Studio 2017 버전 15.3 이상** (사용할 수 있는 [/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 람다 식으로 선언할 수 있습니다 `constexpr` contant 식에서 사용할 때 각 데이터 멤버의 초기화 한다는 캡처하거나 소개 상수 식 내에 허용 됩니다.  

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
람다는 암시적으로 `constexpr` 결과의 요구 사항을 만족 하는 경우는 `constexpr` 함수:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
람다가 암시적 또는 명시적으로 경우 `constexpr`를 함수 포인터로 변환 하 고, 결과 함수는 또한 `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>참고 항목  
 [C++ 언어 참조](../cpp/cpp-language-reference.md)   
 [C + + 표준 라이브러리에 함수 개체](../standard-library/function-objects-in-the-stl.md)   
 [함수 호출](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)
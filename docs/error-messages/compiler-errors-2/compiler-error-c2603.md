---
description: '자세한 정보: 컴파일러 오류 C2603'
title: 컴파일러 오류 C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e28ea581c4c1417972cddc0ce558bd518acb8889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208790"
---
# <a name="compiler-error-c2603"></a>컴파일러 오류 C2603

> '*function*': 생성자/소멸자가 있는 블록 범위 정적 개체가 함수에 너무 많습니다.

Visual Studio 2015 이전의 Microsoft c + + 컴파일러 또는 [/zc: threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) 컴파일러 옵션이 지정 된 경우 외부에서 볼 수 있는 인라인 함수에서 사용할 수 있는 정적 개체 수는 31 개로 제한 됩니다.

이 문제를 해결 하려면 최신 버전의 Microsoft c + + 컴파일러 도구 집합을 채택 하거나 가능한 경우/Zc: threadSafeInit-컴파일러 옵션을 제거 하는 것이 좋습니다. 가능 하지 않은 경우 정적 개체를 결합 하는 것이 좋습니다. 개체가 동일한 형식이 면 해당 형식의 단일 정적 배열을 사용 하 고 필요에 따라 개별 멤버를 참조 하는 것이 좋습니다.

## <a name="example"></a>예제

다음 코드는 C2603을 생성 하 고이를 해결 하는 한 가지 방법을 보여 줍니다.

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```

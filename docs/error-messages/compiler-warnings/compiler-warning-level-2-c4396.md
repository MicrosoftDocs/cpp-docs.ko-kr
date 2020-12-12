---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4396'
title: 컴파일러 경고(수준 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: ab8743c748044456fa1826c805f8d652d76c403d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173521"
---
# <a name="compiler-warning-level-2-c4396"></a>컴파일러 경고(수준 2) C4396

"name": friend 선언이 함수 템플릿의 특수화를 참조하는 경우 인라인 지정자를 사용할 수 없습니다.

함수 템플릿의 특수화에서 [인라인](../../cpp/inline-functions-cpp.md) 지정자를 지정할 수 없습니다. 컴파일러가 C4396 경고를 실행하고 인라인 지정자를 무시합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **`inline`** **`__inline`** **`__forceinline`** Friend 함수 선언에서, 또는 지정자를 제거 합니다.

## <a name="example"></a>예제

다음 코드 예제에서는 지정자를 사용 하는 잘못 된 friend 함수 선언을 보여 줍니다 **`inline`** .

```cpp
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```

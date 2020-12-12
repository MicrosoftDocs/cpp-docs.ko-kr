---
description: '자세한 정보: 컴파일러 오류 C3241'
title: 컴파일러 오류 C3241
ms.date: 11/04/2016
f1_keywords:
- C3241
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
ms.openlocfilehash: c940599ccee67338c6a088793970b7a255d83ff2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307342"
---
# <a name="compiler-error-c3241"></a>컴파일러 오류 C3241

' method ':이 메서드는 ' interface '에 의해 정의 되지 않았습니다.

함수를 명시적으로 재정의 하는 경우 함수 시그니처는 재정의 하는 함수에 대 한 선언과 정확히 일치 해야 합니다.

다음 샘플에서는 C3241를 생성 합니다.

```cpp
// C3241.cpp
#pragma warning(disable:4199)

__interface IX12A {
   void mf();
};

__interface IX12B {
   void mf(int);
};

class CX12 : public IX12A, public IX12B { // C3241
   void IX12A::mf(int);
};
```

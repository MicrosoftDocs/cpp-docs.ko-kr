---
description: '자세한 정보: 컴파일러 오류 C2674'
title: 컴파일러 오류 C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: c88a32eaeeda28b8ffb8daa0411a71fd773ffa2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282044"
---
# <a name="compiler-error-c2674"></a>컴파일러 오류 C2674

이 컨텍스트에서는 제네릭 선언을 사용할 수 없습니다.

제네릭이 잘못 선언 되었습니다. 자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2674를 생성 합니다.

```cpp
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```

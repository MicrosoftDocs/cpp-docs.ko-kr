---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4570'
title: 컴파일러 경고(수준 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: aa776654b77f8d548f197ac2dc35bd4474e92068
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257773"
---
# <a name="compiler-warning-level-3-c4570"></a>컴파일러 경고(수준 3) C4570

' type ':가 abstract로 명시적으로 선언 되지 않았지만 추상 함수를 포함 합니다.

[추상](../../extensions/abstract-cpp-component-extensions.md) 함수를 포함 하는 형식은 abstract로 표시 되어야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4570를 생성 합니다.

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```

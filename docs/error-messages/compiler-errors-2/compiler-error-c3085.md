---
description: '자세한 정보: 컴파일러 오류 C3085'
title: 컴파일러 오류 C3085
ms.date: 11/04/2016
f1_keywords:
- C3085
helpviewer_keywords:
- C3085
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
ms.openlocfilehash: e4525a0862f4d32a7fd5ca924934b6679b2a7a6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116394"
---
# <a name="compiler-error-c3085"></a>컴파일러 오류 C3085

'constructor': 생성자는 'keyword'일 수 없습니다.

생성자가 잘못 선언되었습니다. 자세한 내용은 [Override Specifiers](../../extensions/override-specifiers-cpp-component-extensions.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3085를 생성합니다.

```cpp
// C3085.cpp
// compile with: /c /clr
ref struct S {
   S() abstract;   // C3085
   S(S%) abstract;   // C3085
};

ref struct T {
   T() sealed {}   // C3085
   T(T%) sealed {}   // C3085
};
```

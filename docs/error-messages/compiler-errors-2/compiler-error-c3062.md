---
description: '자세한 정보: 컴파일러 오류 C3062'
title: 컴파일러 오류 C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: b57d03f3ef09e1d01741866d99dfff87aa5aa28d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281745"
---
# <a name="compiler-error-c3062"></a>컴파일러 오류 C3062

' enum ': 내부 형식이 ' t r u e ' 이므로 열거자에 값이 필요 합니다.

열거형의 기본 형식을 지정할 수 있습니다. 그러나 일부 형식에서는 각 열거자에 값을 할당 해야 합니다.

열거형에 대 한 자세한 내용은 [enum 클래스](../../extensions/enum-class-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3062를 생성 합니다.

```cpp
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```

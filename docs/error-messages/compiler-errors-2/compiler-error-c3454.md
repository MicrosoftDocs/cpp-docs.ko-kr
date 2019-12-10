---
title: 컴파일러 오류 C3454
ms.date: 11/04/2016
f1_keywords:
- C3454
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
ms.openlocfilehash: 1909dc772413c16d39271dc839a0ec0db206da03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756684"
---
# <a name="compiler-error-c3454"></a>컴파일러 오류 C3454

[attribute]는 클래스 선언에 사용할 수 없습니다.

클래스는 특성이 되도록 정의되어야 합니다.

자세한 내용은 [attribute](../../windows/attributes/attribute.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3454를 생성합니다.

```cpp
// C3454.cpp
// compile with: /clr /c
using namespace System;

[attribute]   // C3454
ref class Attr1;

[attribute]   // OK
ref class Attr2 {};
```

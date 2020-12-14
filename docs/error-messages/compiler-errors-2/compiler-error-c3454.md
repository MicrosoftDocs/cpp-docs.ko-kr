---
description: '자세한 정보: 컴파일러 오류 C3454'
title: 컴파일러 오류 C3454
ms.date: 11/04/2016
f1_keywords:
- C3454
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
ms.openlocfilehash: 3d7905600a5d9502315689f9d25bd6d39dd80763
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315935"
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

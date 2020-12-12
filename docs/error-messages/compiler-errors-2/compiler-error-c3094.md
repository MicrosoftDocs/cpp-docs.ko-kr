---
description: '자세한 정보: 컴파일러 오류 C3094'
title: 컴파일러 오류 C3094
ms.date: 11/04/2016
f1_keywords:
- C3094
helpviewer_keywords:
- C3094
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
ms.openlocfilehash: 0ca6beeaf8976aab3847b7384c74f6dfef5a2f5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116342"
---
# <a name="compiler-error-c3094"></a>컴파일러 오류 C3094

'attribute': 익명으로 사용할 수 없습니다.

특성의 범위를 올바르게 지정하지 않았습니다.  자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3094를 생성합니다.

```cpp
// C3094.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
public ref class AAttribute : Attribute {};

[A];   // C3094

// OK
[A]
ref class x{};
```

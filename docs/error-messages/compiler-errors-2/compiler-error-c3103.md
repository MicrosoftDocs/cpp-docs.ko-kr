---
description: '자세한 정보: 컴파일러 오류 C3103'
title: 컴파일러 오류 C3103
ms.date: 11/04/2016
f1_keywords:
- C3103
helpviewer_keywords:
- C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
ms.openlocfilehash: a1cd6b2116e277b21eec291633ccb8b84196a615
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116121"
---
# <a name="compiler-error-c3103"></a>컴파일러 오류 C3103

' argument ': 명명 된 인수가 반복 되었습니다.

특성은 명명 된 인수를 반복할 수 없습니다.

자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3103를 생성 합니다.

```cpp
// C3103.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   int m_t;
};

[Attr(m_t = 10, m_t = 1)]   // C3103
// try the following line instead
// [Attr(m_t = 10)]
ref class A {};
```

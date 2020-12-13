---
description: '자세한 정보: 컴파일러 오류 C3749'
title: 컴파일러 오류 C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 247f98214a3f2ec8a496f1da11633f53916328f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340179"
---
# <a name="compiler-error-c3749"></a>컴파일러 오류 C3749

' attribute ': 사용자 지정 특성은 함수 내에서 사용할 수 없습니다.

사용자 지정 특성은 함수 내에서 사용할 수 없습니다. 사용자 지정 특성에 대 한 자세한 내용은 항목 [특성](../../windows/attributes/attribute.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3749를 생성 합니다.

```cpp
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```

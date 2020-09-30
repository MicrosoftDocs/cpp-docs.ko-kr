---
title: 컴파일러 오류 C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 0d49eae823eb64f97e7276d432e161b3de21d725
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510077"
---
# <a name="compiler-error-c3734"></a>컴파일러 오류 C3734

'class': 관리되는 클래스 또는 WinRT 클래스에는 coclass를 사용할 수 없습니다.

[Coclass](../../windows/attributes/coclass.md) 특성은 관리 되는 클래스 또는 WinRT 클래스와 함께 사용할 수 없습니다.

다음 샘플에서는 C3734를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```

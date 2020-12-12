---
description: '자세한 정보: 컴파일러 오류 C3455'
title: 컴파일러 오류 C3455
ms.date: 11/04/2016
f1_keywords:
- C3455
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
ms.openlocfilehash: ae450f385111fd6fa6f7f5655d04f01f893b8fd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113638"
---
# <a name="compiler-error-c3455"></a>컴파일러 오류 C3455

'attribute': 해당 인수와 일치하는 특성 생성자가 없습니다.

잘못된 값이 특성을 선언하는 데 사용되었습니다.  자세한 내용은 [attribute](../../windows/attributes/attribute.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3455를 생성합니다.

```cpp
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```

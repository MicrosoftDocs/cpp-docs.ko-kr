---
title: 컴파일러 오류 C3131
ms.date: 11/04/2016
f1_keywords:
- C3131
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
ms.openlocfilehash: e19442e3c218ade2fc9f9b1c18bf44ade8188035
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501427"
---
# <a name="compiler-error-c3131"></a>컴파일러 오류 C3131

프로젝트에는 ' name ' 속성이 있는 ' module ' 특성이 있어야 합니다.

[Module](../../windows/attributes/module-cpp.md) 특성에는 name 매개 변수가 있어야 합니다.

다음 샘플에서는 C3131를 생성 합니다.

```cpp
// C3131.cpp
[emitidl];
[module];   // C3131
// try the following line instead
// [module (name="MyLib")];

[public]
typedef long int LongInt;
```

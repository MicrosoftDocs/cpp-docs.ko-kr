---
description: '자세한 정보: 컴파일러 오류 C2777'
title: 컴파일러 오류 C2777
ms.date: 11/04/2016
f1_keywords:
- C2777
helpviewer_keywords:
- C2777
ms.assetid: 5fe158c0-2a65-488a-aca2-61d4a8b32d43
ms.openlocfilehash: 301dadd8a62826455c0cdd7b7d9d8d9d3832d666
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298125"
---
# <a name="compiler-error-c2777"></a>컴파일러 오류 C2777

속성 당 ' put ' 메서드를 하나만 지정할 수 있습니다.

[속성](../../cpp/property-cpp.md) declspec 한정자에 속성이 둘 이상 `put` 있습니다.

다음 샘플에서는 C2777를 생성 합니다.

```cpp
// C2777.cpp
struct A {
   __declspec(property(put=PutProp,put=PutPropToo))   // C2777
   // try the following line instead
   // __declspec(property(put=PutProp))
      int prop;
   int PutProp(void);
   int PutPropToo(void);
};
```

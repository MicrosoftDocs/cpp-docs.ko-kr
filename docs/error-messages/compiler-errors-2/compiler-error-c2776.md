---
description: '자세한 정보: 컴파일러 오류 C2776'
title: 컴파일러 오류 C2776
ms.date: 11/04/2016
f1_keywords:
- C2776
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
ms.openlocfilehash: 75e0121c61fd55aa89e6ffcc6e1ed00137fcaaca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298138"
---
# <a name="compiler-error-c2776"></a>컴파일러 오류 C2776

속성 당 ' get ' 메서드를 하나만 지정할 수 있습니다.

`get` [속성](../../cpp/property-cpp.md) 확장 특성에는 함수를 하나만 지정할 수 있습니다. 이 오류 `get` 는 여러 함수를 지정 하는 경우에 발생 합니다.

다음 샘플에서는 C2776를 생성 합니다.

```cpp
// C2776.cpp
struct A {
   __declspec(property(get=GetProp,get=GetPropToo))
   // try the following line instead
   // __declspec(property(get=GetProp))
      int prop;   // C2776
   int GetProp(void);
   int GetPropToo(void);
};
```

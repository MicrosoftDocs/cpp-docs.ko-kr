---
description: '자세한 정보: 컴파일러 오류 C2640'
title: 컴파일러 오류 C2640
ms.date: 11/04/2016
f1_keywords:
- C2640
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
ms.openlocfilehash: e1bbcc2e0db1b12cb4b72f8346c1d5a55532d6da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160898"
---
# <a name="compiler-error-c2640"></a>컴파일러 오류 C2640

' identifier ': 참조에 사용할 __based 한정자가 잘못 되었습니다.

**`__based`** 한정자는 포인터에만 사용할 수 있습니다.

다음 샘플에서는 C2640를 생성 합니다.

```cpp
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```

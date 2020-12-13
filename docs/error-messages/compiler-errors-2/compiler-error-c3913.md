---
description: '자세한 정보: 컴파일러 오류 C3913'
title: 컴파일러 오류 C3913
ms.date: 11/04/2016
f1_keywords:
- C3913
helpviewer_keywords:
- C3913
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
ms.openlocfilehash: 92db9f0c198d07453968c1d01a63ee33e2998594
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144081"
---
# <a name="compiler-error-c3913"></a>컴파일러 오류 C3913

기본 속성은 인덱싱되어 야 합니다.

기본 속성이 잘못 정의 되었습니다.

자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C3913를 생성 합니다.

```cpp
// C3913.cpp
// compile with: /clr /c
ref struct X {
   property int default {   // C3913
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```

---
title: 컴파일러 오류 C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: faf87334f1a98661078341a4d7dc11280802a376
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220212"
---
# <a name="compiler-error-c2793"></a>컴파일러 오류 C2793

' token ': ':: ', 식별자 또는 ' operator ' 키워드 뒤에 예기치 않은 토큰이 필요 합니다.

따를 수 있는 토큰은 `__super::` 식별자 또는 키워드 **`operator`** 입니다.

다음 샘플에서는 C2793를 생성 합니다.

```cpp
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```

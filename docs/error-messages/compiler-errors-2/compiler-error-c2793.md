---
description: '자세한 정보: 컴파일러 오류 C2793'
title: 컴파일러 오류 C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: 26d38427f8d5b502df7d8a6ff4351dd00a3155eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297748"
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

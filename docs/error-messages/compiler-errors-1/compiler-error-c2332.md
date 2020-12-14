---
description: '자세한 정보: 컴파일러 오류 C2332'
title: 컴파일러 오류 C2332
ms.date: 11/04/2016
f1_keywords:
- C2332
helpviewer_keywords:
- C2332
ms.assetid: fb05cd68-e271-4bea-9fb7-ef4edb0a26ac
ms.openlocfilehash: 9733e588c3f24d61da154d7cb14a5eeecc30e2c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234919"
---
# <a name="compiler-error-c2332"></a>컴파일러 오류 C2332

' typedef ': 태그 이름이 없습니다.

컴파일러가 불완전 한 형식 정의를 발견 했습니다.

다음 샘플에서는 C2332를 생성 합니다.

```cpp
// C2332.cpp
// compile with: /c
struct S {
   int i;
};

typedef struct * pS;   // C2332
typedef struct S* pS;   // OK

int get_S_i(pS p) {
   return p->i;
}
```

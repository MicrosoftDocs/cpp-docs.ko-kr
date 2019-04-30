---
title: 컴파일러 오류 C2104
ms.date: 11/04/2016
f1_keywords:
- C2104
helpviewer_keywords:
- C2104
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
ms.openlocfilehash: 086952b9f2b2b84851565bd2b4dafefa15808079
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338664"
---
# <a name="compiler-error-c2104"></a>컴파일러 오류 C2104

비트 필드의 '&'가 무시됩니다.

비트 필드의 주소를 가져올 수 없습니다.

다음 샘플에서는 C2104 오류가 생성 됩니다.

```
// C2104.cpp
struct X {
   int sb : 1;
};

int main() {
   X x;
   &x.sb;   // C2104
   x.sb;   // OK
}
```
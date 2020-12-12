---
description: '자세한 정보: 컴파일러 오류 C2104'
title: 컴파일러 오류 C2104
ms.date: 11/04/2016
f1_keywords:
- C2104
helpviewer_keywords:
- C2104
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
ms.openlocfilehash: 407bb77c3c1fe19410a68a1dc48baf562dc6c5b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170245"
---
# <a name="compiler-error-c2104"></a>컴파일러 오류 C2104

비트 필드의 ' & '이 (가) 무시 되었습니다.

비트 필드의 주소를 가져올 수 없습니다.

다음 샘플에서는 C2104를 생성 합니다.

```cpp
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

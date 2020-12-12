---
description: '자세히 알아보기: 자동 (함수 범위) 변수'
title: 자동 (함수 범위) 변수
ms.date: 04/22/2019
helpviewer_keywords:
- automatic variables
- variables, automatic
- functions [C++], scope
- scope, declared within functions
ms.assetid: 6e1a14c2-1fb0-4937-8628-8d963cc35ed4
ms.openlocfilehash: 666a59ce6ebb9e8d011216f87ca45b49eabbc766
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323014"
---
# <a name="automatic-function-scope-variables"></a>자동 (함수 범위) 변수

함수 내에서 선언 된 변수는 해당 함수의 범위 내 에서만 사용할 수 있습니다.

```cpp
// LNK2019_AV.cpp
// compile with: /c
void test(void);

static int lnktest3 = 3;
int lnktest4 = 4;

int main() {
   static int lnktest1 = 1;
   int lnktest2 = 2;
   test();
}
```

그런 다음

```cpp
// LNK2019_AV_2.cpp
// compile with: LNK2019_AV.cpp
// LNK2019 expected
extern int lnktest1;
extern int lnktest2;
extern int lnktest3;
extern int lnktest4;

void test(void) {
   int i = 0;
   i = lnktest1;
   i = lnktest2;
   i = lnktest3;
   i = lnktest4;   // OK
}
```

## <a name="see-also"></a>참고 항목

[링커 도구 오류 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)

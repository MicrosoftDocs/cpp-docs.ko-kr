---
description: '자세한 정보: 컴파일러 오류 C2362'
title: 컴파일러 오류 C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 9043b6e82fd45923e7108d6a6f8934416eaaa328
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210922"
---
# <a name="compiler-error-c2362"></a>컴파일러 오류 C2362

> ' goto *label*'에서 '*identifier*' 초기화를 건너뜁니다.

[/Za](../../build/reference/za-ze-disable-language-extensions.md)를 사용 하 여 컴파일한 경우 레이블로 이동 하면 식별자가 초기화 되지 않습니다.

선언이 입력 되지 않은 블록에 포함 되어 있거나 변수가 이미 초기화 된 경우 이니셜라이저를 사용 하 여 선언을 건너뛸 수 있습니다.

다음 샘플에서는 C2362를 생성 합니다.

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

해결 방법:

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```

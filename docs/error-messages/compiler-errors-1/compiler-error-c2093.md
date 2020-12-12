---
description: '자세한 정보: 컴파일러 오류 C2093'
title: 컴파일러 오류 C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d08c2e29415363fc64309a89691ec0852ca5fa88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251858"
---
# <a name="compiler-error-c2093"></a>컴파일러 오류 C2093

' variable1 ': ' variable2 ' 자동 변수의 주소를 사용 하 여 초기화할 수 없습니다.

[/Za](../../build/reference/za-ze-disable-language-extensions.md)를 사용 하 여 컴파일하는 경우 프로그램에서 자동 변수의 주소를 이니셜라이저로 사용 하려고 시도 했습니다.

다음 샘플에서는 C2093를 생성 합니다.

```c
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```

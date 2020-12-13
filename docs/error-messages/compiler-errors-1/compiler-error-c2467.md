---
description: '자세한 정보: 컴파일러 오류 C2467'
title: 컴파일러 오류 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: fd5227e451208d848d631550da33999a4ebae8dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333821"
---
# <a name="compiler-error-c2467"></a>컴파일러 오류 C2467

익명의 ' 사용자 정의 형식 ' 선언이 잘못 되었습니다.

중첩 된 사용자 정의 형식이 선언 되었습니다. 이 오류는[/za](../../build/reference/za-ze-disable-language-extensions.md)(ANSI compatibility option)를 사용 하는 C 소스 코드를 컴파일하는 경우에 발생 합니다.

다음 샘플에서는 C2467를 생성 합니다.

```c
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```

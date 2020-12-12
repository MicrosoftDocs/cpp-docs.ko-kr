---
description: '자세한 정보: 컴파일러 오류 C2689'
title: 컴파일러 오류 C2689
ms.date: 11/04/2016
f1_keywords:
- C2689
helpviewer_keywords:
- C2689
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
ms.openlocfilehash: 532db26a3c0da3191c9b15215d470618e561e76a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326716"
---
# <a name="compiler-error-c2689"></a>컴파일러 오류 C2689

' function ': friend 함수는 지역 클래스 내에 정의할 수 없습니다.

로컬 클래스에서 friend 함수를 선언 하 고 정의할 수는 없습니다.

다음 샘플에서는 C2689를 생성 합니다.

```cpp
// C2689.cpp
// compile with: /c
void g() {
   void f2();
   class X {
      friend void f2(){}   // C2689
      friend void f2();   // OK
   };
}
```

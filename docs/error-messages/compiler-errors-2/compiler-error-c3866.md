---
description: '자세한 정보: 컴파일러 오류 C3866'
title: 컴파일러 오류 C3866
ms.date: 11/04/2016
f1_keywords:
- C3866
helpviewer_keywords:
- C3866
ms.assetid: 685870af-2440-4cdf-a6cb-284a5b96ef9d
ms.openlocfilehash: fceb8ed41a3cbfc287f4c1115cd0502ce8506925
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222868"
---
# <a name="compiler-error-c3866"></a>컴파일러 오류 C3866

함수 호출에 인수 목록이 없습니다.

비정적 멤버 함수 내에서 소멸자 또는 종료자 호출에 인수 목록이 없습니다.

다음 샘플에서는 C3866를 생성 합니다.

```cpp
// C3866.cpp
// compile with: /c
class C {
   ~C();
   void f() {
      this->~C;   // C3866
      this->~C();   // OK
   }
};
```

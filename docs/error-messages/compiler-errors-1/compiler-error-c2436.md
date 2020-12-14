---
description: '자세한 정보: 컴파일러 오류 C2436'
title: 컴파일러 오류 C2436
ms.date: 11/04/2016
f1_keywords:
- C2436
helpviewer_keywords:
- C2436
ms.assetid: ca4cc813-bc1d-4c0a-9a2c-3a5fe673d084
ms.openlocfilehash: 3858146d48006c1129f6dca1992e229603b70a79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189914"
---
# <a name="compiler-error-c2436"></a>컴파일러 오류 C2436

' identifier ': 생성자 이니셜라이저 목록에 멤버 함수 또는 중첩 클래스가 있습니다.

생성자 이니셜라이저 목록의 멤버 함수 또는 로컬 클래스를 초기화할 수 없습니다.

다음 샘플에서는 C2436를 생성 합니다.

```cpp
// C2436.cpp
struct S{
   int f();
   struct Inner{
      int i;
   };
   S():f(10), Inner(0){}   // C2436
};
```

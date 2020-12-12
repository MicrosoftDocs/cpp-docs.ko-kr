---
description: '자세한 정보: 컴파일러 오류 C2634'
title: 컴파일러 오류 C2634
ms.date: 11/04/2016
f1_keywords:
- C2634
helpviewer_keywords:
- C2634
ms.assetid: 58c8f2db-ac95-4a81-9355-ef3cfb0ba7b3
ms.openlocfilehash: 5e8aee2ce27fc56f1204d925147f48352bd24a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123411"
---
# <a name="compiler-error-c2634"></a>컴파일러 오류 C2634

' &class:: member ': 참조 멤버에 대 한 포인터가 잘못 되었습니다.

참조 멤버에 대 한 포인터가 선언 됩니다.

다음 샘플에서는 C2634를 생성 합니다.

```cpp
// C2634.cpp
int mem;
struct S {
   S() : rf(mem) { }
   int &rf;
};
int (S::*pdm) = &S::rf;   // C2634
```

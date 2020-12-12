---
description: '자세한 정보: 컴파일러 오류 C2365'
title: 컴파일러 오류 C2365
ms.date: 11/04/2016
f1_keywords:
- C2365
helpviewer_keywords:
- C2365
ms.assetid: 35839b0b-4055-4b79-8957-b3a0871bdd02
ms.openlocfilehash: e8968e7cc56355c213e88d2e4aeecfb1044e4550
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210935"
---
# <a name="compiler-error-c2365"></a>컴파일러 오류 C2365

'class member': 재정의: 이전 정의는 'class member'입니다.

클래스 멤버를 다시 정의하려고 했습니다.

다음 샘플에서는 C2365를 생성합니다.

```cpp
// C2365.cpp
// compile with: /c
class C1 {
   int CFunc();
   char *CFunc;   // C2365, already exists as a member function

   int CMem;
   char *CMem();   // C2365, already exists as a data member
};
```

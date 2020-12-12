---
description: '자세한 정보: 컴파일러 오류 C2809'
title: 컴파일러 오류 C2809
ms.date: 11/04/2016
f1_keywords:
- C2809
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
ms.openlocfilehash: 75333b2742e1860eede12727e465479b4869e00c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320602"
---
# <a name="compiler-error-c2809"></a>컴파일러 오류 C2809

' operator operator '에 정식 매개 변수가 없습니다.

연산자에 필수 매개 변수가 부족 합니다.

다음 샘플에서는 C2809를 생성 합니다.

```cpp
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```

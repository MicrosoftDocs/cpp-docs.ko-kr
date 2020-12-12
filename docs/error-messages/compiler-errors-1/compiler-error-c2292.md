---
description: '자세한 정보: 컴파일러 오류 C2292'
title: 컴파일러 오류 C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: fb3630edc1aa3fc3aeb1b90d3ab79b17c775fa61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268251"
---
# <a name="compiler-error-c2292"></a>컴파일러 오류 C2292

' identifier ': 모범 사례 상속 표현입니다. ' representation1 '가 선언 되었지만 ' representation2 '가 필요 합니다.

[/Vmb](../../build/reference/vmb-vmg-representation-method.md) 를 사용 하 여 다음 코드를 컴파일하면 ("모범 사례 항상" 표현) C2292가 발생 합니다.

```cpp
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```

---
description: '자세한 정보: 컴파일러 오류 C2159'
title: 컴파일러 오류 C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: 045515ba964832de8821e048eac58b0ec507d830
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181217"
---
# <a name="compiler-error-c2159"></a>컴파일러 오류 C2159

스토리지 클래스를 두 개 이상 지정했습니다.

선언에 스토리지 클래스가 둘 이상 포함되어 있습니다.

다음 샘플에서는 C2159를 생성합니다.

```cpp
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```

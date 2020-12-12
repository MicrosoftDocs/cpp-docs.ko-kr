---
description: '자세한 정보: 컴파일러 오류 C2479'
title: 컴파일러 오류 C2479
ms.date: 11/04/2016
f1_keywords:
- C2479
helpviewer_keywords:
- C2479
ms.assetid: c74c7869-e65b-4ca1-b6fa-eb39fed4458a
ms.openlocfilehash: 7193112ee546b7314075b105cb88c68fce71a256
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123944"
---
# <a name="compiler-error-c2479"></a>컴파일러 오류 C2479

' identifier ': ' allocate () '는 정적 범위의 데이터 항목에만 유효 합니다.

`__declspec( allocate())`구문은 정적 데이터에만 사용할 수 있습니다.

다음 샘플에서는 C2479를 생성 합니다.

```cpp
// C2479.cpp
// compile with: /c
#pragma section("mycode", read)
static __declspec(allocate("mycode")) void DoNothing() {}   // C2479
__declspec(allocate("mycode"))  int i = 0;   // OK
```

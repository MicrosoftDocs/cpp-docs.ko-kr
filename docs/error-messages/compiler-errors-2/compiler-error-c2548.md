---
title: 컴파일러 오류 C2548 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2548
dev_langs:
- C++
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4fd5087613466ecb483ad4ec28018c9321453ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050513"
---
# <a name="compiler-error-c2548"></a>컴파일러 오류 C2548

'class::member': 매개 변수 매개 변수에 대 한 기본 매개 변수 누락

기본 매개 변수 목록에 매개 변수가 없습니다. 매개 변수 목록에서 아무 곳 이나 기본 매개 변수를 제공 하는 경우 모든 후속 매개 변수에 대 한 기본 매개 변수를 정의 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2548 오류가 생성 됩니다.

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```
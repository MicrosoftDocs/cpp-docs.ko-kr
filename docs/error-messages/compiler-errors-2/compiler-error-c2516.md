---
title: 컴파일러 오류 C2516
ms.date: 11/04/2016
f1_keywords:
- C2516
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
ms.openlocfilehash: 2114ad048c2061b81f223c86536f23737bdf43fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540064"
---
# <a name="compiler-error-c2516"></a>컴파일러 오류 C2516

'name': 올바른 기본 클래스가 아닙니다.

클래스에서 정의 된 형식 이름에서 파생 됩니다는 `typedef` 문입니다.

다음 샘플에서는 C2516 오류가 생성 됩니다.

```
// C2516.cpp
typedef unsigned long ulong;
class C : public ulong {}; // C2516
```
---
title: 컴파일러 오류 C2846
ms.date: 11/04/2016
f1_keywords:
- C2846
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
ms.openlocfilehash: 4e1e88e538008cff03349a35e193b7bcd471b950
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256752"
---
# <a name="compiler-error-c2846"></a>컴파일러 오류 C2846

'constructor': 인터페이스는 생성자를 사용할 수 없습니다.

시각적 개체 C++ [인터페이스](../../cpp/interface.md) 생성자를 사용할 수 없습니다.

다음 샘플에서는 C2846 오류가 생성 됩니다.

```
// C2846.cpp
// compile with: /c
__interface C {
   C();   // C2846 constructor not allowed in an interface
};
```
---
description: '자세한 정보: 컴파일러 오류 C2256'
title: 컴파일러 오류 C2256
ms.date: 11/04/2016
f1_keywords:
- C2256
helpviewer_keywords:
- C2256
ms.assetid: 171fa2bc-8c72-49cd-afe5-d723b7acd3c5
ms.openlocfilehash: a0dfc7601a09a47c24128ca5f999780d9fdf3e48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134760"
---
# <a name="compiler-error-c2256"></a>컴파일러 오류 C2256

' function '에서 friend 지정자를 잘못 사용 하였습니다.

소멸자 또는 생성자를 [friend](../../cpp/friend-cpp.md)로 지정할 수 없습니다.

다음 샘플에서는 C2256를 생성 합니다.

```cpp
// C2256.cpp
// compile with: /c
class C {
public:
   friend ~C();   // C2256
   ~C();   // OK
};
```

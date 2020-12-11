---
description: '자세한 정보: 컴파일러 오류 C2648'
title: 컴파일러 오류 C2648
ms.date: 11/04/2016
f1_keywords:
- C2648
helpviewer_keywords:
- C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
ms.openlocfilehash: e8e417fa54e0c198cb6adba78932232c6c33b437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160768"
---
# <a name="compiler-error-c2648"></a>컴파일러 오류 C2648

' identifier ': 멤버를 기본 매개 변수로 사용 하려면 정적 멤버가 필요 합니다.

비정적 멤버가 기본 매개 변수로 사용 됩니다.

다음 샘플에서는 C2648를 생성 합니다.

```cpp
// C2648.cpp
// compile with: /c
class C {
public:
   int i;
   static int j;
   void func1( int i = i );  // C2648  i is not static
   void func2( int i = j );  // OK
};
```

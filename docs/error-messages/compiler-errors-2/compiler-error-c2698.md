---
description: '자세한 정보: 컴파일러 오류 C2698'
title: 컴파일러 오류 C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: a787c43e7a885734f4c6a2d76aa16d51e19615c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326632"
---
# <a name="compiler-error-c2698"></a>컴파일러 오류 C2698

' 선언 1 '에 대 한 using 선언은 ' 선언 2 '에 대 한 기존 using 선언과 함께 사용할 수 없습니다.

데이터 멤버에 대 한 [using 선언이](../../cpp/using-declaration.md) 있으면 함수는 오버 로드 될 수 있으므로 동일한 이름을 사용 하는 동일한 범위에 있는 using 선언은 허용 되지 않습니다.

다음 샘플에서는 C2698를 생성 합니다.

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```

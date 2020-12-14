---
description: '자세한 정보: 컴파일러 오류 C3226'
title: 컴파일러 오류 C3226
ms.date: 11/04/2016
f1_keywords:
- C3226
helpviewer_keywords:
- C3226
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
ms.openlocfilehash: f6c050f4e4c41e9ed5574c56fcc8067759cc172b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304196"
---
# <a name="compiler-error-c3226"></a>컴파일러 오류 C3226

제네릭 선언 내부에서는 템플릿을 선언할 수 없습니다.

제네릭 클래스 내부에서는 제네릭 선언을 사용합니다.

다음 샘플에서는 C3226을 생성합니다.

```cpp
// C3226.cpp
// compile with: /clr
generic <class T>
ref class C {
   template <class T1>   // C3226
   ref struct S1 {};
};
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3226b.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   generic <class T1>
   ref struct S1 {};
};
```

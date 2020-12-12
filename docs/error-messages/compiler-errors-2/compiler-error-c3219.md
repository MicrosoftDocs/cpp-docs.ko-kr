---
description: '자세한 정보: 컴파일러 오류 C3219'
title: 컴파일러 오류 C3219
ms.date: 11/04/2016
f1_keywords:
- C3219
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
ms.openlocfilehash: 0210d8c65972a6adc7d5c2dbe51088f3c3766106
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267744"
---
# <a name="compiler-error-c3219"></a>컴파일러 오류 C3219

'param': 제네릭 매개 변수는 여러 개의 비인터페이스('class')에 의해 제약을 받을 수 없습니다.

제네릭 매개 변수를 둘 이상의 관리되는 클래스로 제한할 수 없습니다.

다음 샘플에서는 C3219를 생성합니다.

```cpp
// C3219.cpp
// compile with: /clr
ref class A {};
ref class B {};

generic <class T>
where T : A, B
ref class E {};   // C3219
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3219b.cpp
// compile with: /clr /c
ref class A {};

interface struct C {};

generic <class T>
where T : A
ref class E {};
```

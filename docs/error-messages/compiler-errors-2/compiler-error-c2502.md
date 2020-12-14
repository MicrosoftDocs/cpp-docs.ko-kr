---
description: '자세한 정보: 컴파일러 오류 C2502'
title: 컴파일러 오류 C2502
ms.date: 11/04/2016
f1_keywords:
- C2502
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
ms.openlocfilehash: 6ee501a5fa3601ef5e4b97d4be5a8e59463ce797
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275934"
---
# <a name="compiler-error-c2502"></a>컴파일러 오류 C2502

' identifier ': 기본 클래스에 액세스 한정자가 너무 많습니다.

기본 클래스에 액세스 한정자가 둘 이상 있습니다. 하나의 액세스 한정자 ( **`public`** , **`private`** 또는)만 **`protected`** 허용 됩니다.

다음 샘플에서는 C2502를 생성 합니다.

```cpp
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```

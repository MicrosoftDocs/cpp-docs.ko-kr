---
description: '자세한 정보: 컴파일러 오류 C3210'
title: 컴파일러 오류 C3210
ms.date: 11/04/2016
f1_keywords:
- C3210
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
ms.openlocfilehash: 5349a7ea8677a8a55511f514e74251375a262fb7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173911"
---
# <a name="compiler-error-c3210"></a>컴파일러 오류 C3210

' type ': 액세스 선언은 기본 클래스 멤버에만 적용할 수 있습니다.

[Using 선언이](../../cpp/using-declaration.md) 잘못 지정 되었습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3210를 생성 합니다.

```cpp
// C3210.cpp
// compile with: /c
struct A {
protected:
   int i;
};

struct B {
   using A::i;   // C3210
};

struct C : public A {
   using A::i;   // OK
};
```

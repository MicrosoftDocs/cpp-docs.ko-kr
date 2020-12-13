---
description: '자세한 정보: 컴파일러 오류 C3657'
title: 컴파일러 오류 C3657
ms.date: 11/04/2016
f1_keywords:
- C3657
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
ms.openlocfilehash: 6e5cf5dd0b3739acdd703e5ef11d3eb553fa9e90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134422"
---
# <a name="compiler-error-c3657"></a>컴파일러 오류 C3657

소멸자는 명시적으로 재정의 하거나 명시적으로 재정의할 수 없습니다.

소멸자 또는 종료자는 명시적으로 재정의할 수 없습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3657를 생성 합니다.

```cpp
// C3657.cpp
// compile with: /clr
public ref struct I {
   virtual ~I() { }
   virtual void a();
};

public ref struct D : I {
   virtual ~D() = I::~I {}   // C3657
   virtual void a() = I::a {}   // OK
};
```

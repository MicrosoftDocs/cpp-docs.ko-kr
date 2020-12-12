---
description: '자세한 정보: 컴파일러 오류 C3252'
title: 컴파일러 오류 C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: 59b5a0073d3dc8147b2e89d637fd98ba7339f6b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194308"
---
# <a name="compiler-error-c3252"></a>컴파일러 오류 C3252

'method': 관리되는 형식 또는 WinRT 형식에서 가상 메서드의 접근성을 줄일 수 없습니다.

기본 클래스에서 가상 메서드를 구현하거나 인터페이스에서 메서드를 구현하는 클래스는 해당 메서드에 대한 액세스를 줄일 수 없습니다.

인터페이스의 모든 메서드는 공용입니다.

다음 샘플에서는 C3252 오류가 발생하는 경우 및 이를 해결 방법을 보여 줍니다.

```cpp
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```

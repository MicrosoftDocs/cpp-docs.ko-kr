---
description: '자세한 정보: 컴파일러 오류 C2890'
title: 컴파일러 오류 C2890
ms.date: 11/04/2016
f1_keywords:
- C2890
helpviewer_keywords:
- C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
ms.openlocfilehash: 4df022147b9e8b199fa2aea45c3af88525375690
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337444"
---
# <a name="compiler-error-c2890"></a>컴파일러 오류 C2890

' class ': ref 클래스에는 비 인터페이스 기본 클래스를 하나만 사용할 수 있습니다.

참조 클래스에는 기본 클래스를 하나만 사용할 수 있습니다.

다음 샘플에서는 C2890를 생성 합니다.

```cpp
// C2890.cpp
// compile with: /clr /c
ref class A {};
ref class B {};
ref class C : public A, public B {};   // C2890
ref class D : public A {};   // OK
```

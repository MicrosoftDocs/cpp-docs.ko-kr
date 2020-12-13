---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4265'
title: 컴파일러 경고(수준 3) C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: f7ad04d59b9896ce91f4a135f205664885af8f68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344174"
---
# <a name="compiler-warning-level-3-c4265"></a>컴파일러 경고(수준 3) C4265

' class ': 클래스에 가상 함수가 있지만 소멸자가 가상이 아닙니다.

클래스에 가상 함수는 있지만 비가상 소멸자가 있으면 클래스를 기본 클래스 포인터를 통해 소멸 시킬 때 형식의 개체가 제대로 제거 되지 않을 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4265를 생성 합니다.

```cpp
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```

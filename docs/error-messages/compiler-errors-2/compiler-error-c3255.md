---
description: '자세한 정보: 컴파일러 오류 C3255'
title: 컴파일러 오류 C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 576b2c9126173f72470a6e741dd64d8a356c9224
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194204"
---
# <a name="compiler-error-c3255"></a>컴파일러 오류 C3255

' value type ':이 값 형식 개체를 네이티브 힙에 동적으로 할당할 수 없습니다.

관리 되는 멤버를 포함 하는 값 형식 ( [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)참조)의 인스턴스는 스택에서 만들 수 있지만 힙에서는 만들 수 없습니다.

다음 샘플에서는 C3255를 생성 합니다.

```cpp
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```

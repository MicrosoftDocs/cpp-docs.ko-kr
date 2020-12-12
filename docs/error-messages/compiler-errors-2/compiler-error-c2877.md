---
description: '자세한 정보: 컴파일러 오류 C2877'
title: 컴파일러 오류 C2877
ms.date: 11/04/2016
f1_keywords:
- C2877
helpviewer_keywords:
- C2877
ms.assetid: 0b54837e-fcae-4d90-9658-623250435e24
ms.openlocfilehash: fd5a122cfed34c59e4a597bb6371a026a90c2ebb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320488"
---
# <a name="compiler-error-c2877"></a>컴파일러 오류 C2877

' symbol '은 ' class '에서 액세스할 수 없습니다.

기본 클래스에서 파생 된 모든 멤버는 파생 클래스에서 액세스할 수 있어야 합니다.

다음 샘플에서는 C2877를 생성 합니다.

```cpp
// C2877.cpp
// compile with: /c
class A {
private:
   int a;
};

class B : public A {
   using A::a;   // C2877
};
```

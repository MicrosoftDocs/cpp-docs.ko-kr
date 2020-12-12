---
description: '자세한 정보: 컴파일러 오류 C2929'
title: 컴파일러 오류 C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: b110615a05a416b6bba7256c7f59f734179677a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320389"
---
# <a name="compiler-error-c2929"></a>컴파일러 오류 C2929

'identifier': 명시적 인스턴스화. 템플릿-클래스 멤버의 인스턴스화를 명시적으로 강제하고 억제할 수 없습니다.

인스턴스화되지 않도록 하는 동시에 식별자를 명시적으로 인스턴스화할 수 없습니다.

다음 샘플에서는 C2929를 생성합니다.

```cpp
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```

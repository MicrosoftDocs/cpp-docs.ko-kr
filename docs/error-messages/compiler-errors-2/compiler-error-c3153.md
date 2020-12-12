---
description: '자세한 정보: 컴파일러 오류 C3153'
title: 컴파일러 오류 C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 93b028e08963a8d124defe660966a75595c57771
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322048"
---
# <a name="compiler-error-c3153"></a>컴파일러 오류 C3153

' interface ': 인터페이스의 인스턴스를 만들 수 없습니다.

인터페이스를 인스턴스화할 수 없습니다. 인터페이스의 멤버를 사용 하려면 인터페이스에서 클래스를 파생 시키고 인터페이스 멤버를 구현한 다음 멤버를 사용 합니다.

다음 샘플에서는 C3153를 생성 합니다.

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```

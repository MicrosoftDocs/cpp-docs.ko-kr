---
description: '자세한 정보: 컴파일러 오류 C3628'
title: 컴파일러 오류 C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: ed0c434a40e6c513580e37b5fb2fc9f44b1dc5dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144406"
---
# <a name="compiler-error-c3628"></a>컴파일러 오류 C3628

' base class ': 관리 되는 또는 WinRTclasses는 공용 상속만 지원 합니다.

관리 되는 또는 WinRT 클래스를 [전용](../../cpp/private-cpp.md) 또는 [보호 된](../../cpp/protected-cpp.md) 기본 클래스로 사용 하려고 했습니다. 관리 되는 또는 WinRT 클래스는 [공용](../../cpp/public-cpp.md) 액세스를 사용 하는 기본 클래스로만 사용할 수 있습니다.

다음 샘플에서는 C3628을 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```

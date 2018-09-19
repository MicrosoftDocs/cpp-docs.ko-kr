---
title: 컴파일러 오류 C3628 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a65dc33c5381b063c3adb01072e930075108649
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037374"
---
# <a name="compiler-error-c3628"></a>컴파일러 오류 C3628

'base class': 관리 또는 WinRTclasses 공용 상속만 지원

관리 되는 또는 WinRT 사용 하려고 했습니다 클래스는 [사설](../../cpp/private-cpp.md) 또는 [보호](../../cpp/protected-cpp.md) 기본 클래스입니다. 관리 되는 또는 WinRT 클래스는 기본 클래스로 사용할 수 있습니다 [공용](../../cpp/public-cpp.md) 액세스 합니다.

다음 샘플에서는 C3628을 생성하고 해결 방법을 보여 줍니다.

```
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

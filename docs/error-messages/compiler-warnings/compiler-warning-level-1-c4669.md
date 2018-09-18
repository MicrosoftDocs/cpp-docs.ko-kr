---
title: 컴파일러 경고 (수준 1) C4669 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4669
dev_langs:
- C++
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f96bcf40b1fbc989daceabc810d019d1bb9aa98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060861"
---
# <a name="compiler-warning-level-1-c4669"></a>컴파일러 경고(수준 1) C4669

'cast': 안전하지 않은 변환입니다. 'class'는 WinRT 또는 관리되는 형식 개체입니다.

캐스트는 Windows 런타임 또는 관리되는 형식을 포함합니다. 컴파일러는 포인터 간에 비트 복사를 수행하여 캐스트를 완료하지만 다른 검사는 제공하지 않습니다. 이 경고를 해결하려면 관리되는 멤버 또는 Windows 런타임 형식을 포함하는 클래스를 캐스팅하지 마세요.

다음 샘플에서는 C4669 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```
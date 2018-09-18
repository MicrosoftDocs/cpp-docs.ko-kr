---
title: 컴파일러 오류 C2886 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2886
dev_langs:
- C++
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 271ee8341cb5faa033d3fb5ec3238f36975c3531
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023581"
---
# <a name="compiler-error-c2886"></a>컴파일러 오류 C2886

'class::identifier': 멤버 using 선언에서 기호를 사용할 수 없습니다

`using` 선언 네임 스페이스 이름과 같은 기호를 사용 합니다. `using` 선언이 기본 클래스 멤버를 선언 합니다.

다음 샘플에서는 C2886 오류가 생성 됩니다.

```
// C2886.cpp
// compile with: /c
namespace Z {
    int i;
}

class B {
protected:
    int i;
};

class D : public B {
    // Error: Z is a namespace
    using Z::i;   // C2886

    // OK: B is a base class
    using B::i;
};
```
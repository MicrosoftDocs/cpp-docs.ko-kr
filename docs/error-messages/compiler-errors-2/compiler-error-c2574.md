---
title: 컴파일러 오류 C2574 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2574
dev_langs:
- C++
helpviewer_keywords:
- C2574
ms.assetid: 3e1c5c18-ee8b-4dbb-bfc0-d3b8991af71b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51874eed00c66832cbae11490147eca50c2d5071
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058396"
---
# <a name="compiler-error-c2574"></a>컴파일러 오류 C2574

'소멸자': 정적으로 선언할 수 없습니다.

생성자 나 소멸자를 선언할 수 있습니다 `static`합니다.

다음 샘플에서는 C2574를 생성합니다.

```
// C2574.cpp
// compile with: /c
class A {
   virtual static ~A();   // C2574
   //  try the following line instead
   // virtual ~A();
};
```
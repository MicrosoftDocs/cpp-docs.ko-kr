---
title: 컴파일러 오류 C3065 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3065
dev_langs:
- C++
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35867da62dad9e399e4b4672f84478e4ea9688a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104937"
---
# <a name="compiler-error-c3065"></a>컴파일러 오류 C3065

클래스 범위가 아닌 범위에서는 속성을 선언할 수 없습니다.

[property](../../cpp/property-cpp.md) __declspec 한정자가 클래스 외부에서 사용되었습니다.  속성은 클래스 내부에서만 선언할 수 있습니다.

다음 샘플에서는 C3065를 생성합니다.

```
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```
---
title: 컴파일러 오류 C3230 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f74e17b1dec3aba78a38d993da81995d00c93784
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065604"
---
# <a name="compiler-error-c3230"></a>컴파일러 오류 C3230

'function': 'template'에 대한 템플릿 형식 인수는 제네릭 형식 매개 변수를 포함할 수 없습니다. 'param'

템플릿은 컴파일 시간에 인스턴스화되는데 제네릭은 런타임에 인스턴스화됩니다. 따라서 제네릭 형식이 마지막으로 알려졌을 때 템플릿을 런타임에 인스턴스화할 수 없으므로 템플릿을 호출할 수 있는 제네릭 코드를 생성할 수 없습니다.

다음 샘플에서는 C3230을 생성합니다.

```
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```
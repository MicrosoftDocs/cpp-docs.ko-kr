---
title: 컴파일러 오류 C2394 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2394
dev_langs:
- C++
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfb1db7ab7cb1b44ff61d4cf6d5a22d5365da4b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051687"
---
# <a name="compiler-error-c2394"></a>컴파일러 오류 C2394

'your_type:: operator'op' ": CLR 또는 WinRToperator 유효 하지 않습니다. 하나 이상의 매개 변수가 'T^', 'T^%', 'T^&' 형식이어야 합니다(여기서 T = 'your_type').

Windows 런타임 또는 관리되는 형식의 연산자는 형식이 연산자 반환 값의 형식과 동일한 매개 변수를 하나 이상 사용할 수 없습니다.

다음 샘플에서는 C2394 오류가 발생하는 경우를 보여 줍니다.

```
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```
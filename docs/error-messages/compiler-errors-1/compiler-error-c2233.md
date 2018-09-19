---
title: 컴파일러 오류 C2233 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2233
dev_langs:
- C++
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 224e32735cb1cc4ad9e02c78f07e9efb9f5627bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083342"
---
# <a name="compiler-error-c2233"></a>컴파일러 오류 C2233

'identifier': 크기가 0 인 배열이 포함 된 개체의 배열을 올바르지 않습니다.

배열의 각 개체에 요소를 하나 이상 있어야 합니다.

다음 샘플에서는 C2233 오류가 생성 됩니다.

```
// C2233.cpp
// compile with: /c
class A {
   char somearray[1];
};

class B {
   char zeroarray[];
};

A array[100];   // OK
B array2[100];   // C2233
```
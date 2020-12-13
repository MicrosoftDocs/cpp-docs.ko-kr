---
description: '자세한 정보: 컴파일러 오류 C2233'
title: 컴파일러 오류 C2233
ms.date: 11/04/2016
f1_keywords:
- C2233
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
ms.openlocfilehash: d111a20fa9cac5a41566f63f6e3eef0c14ef544c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338770"
---
# <a name="compiler-error-c2233"></a>컴파일러 오류 C2233

' identifier ': 크기가 0 인 배열을 포함 하는 개체의 배열이 잘못 되었습니다.

배열의 각 개체는 하나 이상의 요소를 포함 해야 합니다.

다음 샘플에서는 C2233를 생성 합니다.

```cpp
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

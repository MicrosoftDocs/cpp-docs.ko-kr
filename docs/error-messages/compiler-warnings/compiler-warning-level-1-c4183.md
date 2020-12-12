---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4183'
title: 컴파일러 경고 (수준 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 1e9753637d0ee52ef40ce875e4e2d66fbdaab9db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266678"
---
# <a name="compiler-warning-level-1-c4183"></a>컴파일러 경고 (수준 1) C4183

' identifier ': 반환 형식이 없습니다. ' i n t '를 반환 하는 멤버 함수로 간주 됩니다.

클래스 또는 구조체의 멤버 함수에 대 한 인라인 정의에 반환 형식이 없습니다. 이 멤버 함수는의 기본 반환 형식으로 간주 됩니다 **`int`** .

다음 샘플에서는 C4183를 생성 합니다.

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```

---
description: '자세한 정보: 컴파일러 오류 C2738'
title: 컴파일러 오류 C2738
ms.date: 11/04/2016
f1_keywords:
- C2738
helpviewer_keywords:
- C2738
ms.assetid: 896b4640-1ee0-4cd8-9910-de3efa30006a
ms.openlocfilehash: 80d56a4491cf6205313b4da66cb695b956cb60a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123099"
---
# <a name="compiler-error-c2738"></a>컴파일러 오류 C2738

' 선언 ': 모호 하거나 ' type '의 멤버가 아닙니다.

함수가 잘못 선언 되었습니다.

다음 샘플에서는 C2738를 생성 합니다.

```cpp
// C2738.cpp
struct A {
   template <class T> operator T*();
   // template <class T> operator T();
};

template <>
A::operator int() {   // C2738

// try the following line instead
// A::operator int*() {

// or use the commented member declaration

   return 0;
}
```

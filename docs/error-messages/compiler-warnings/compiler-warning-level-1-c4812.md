---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4812'
title: 컴파일러 경고(수준 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 3476086d067b98a62ec9d96647a77c109c9a263b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332191"
---
# <a name="compiler-warning-level-1-c4812"></a>컴파일러 경고(수준 1) C4812

사용되지 않는 선언 스타일입니다. 대신 'new_syntax'를 사용하세요.

현재 릴리스의 Visual C++에서는 명시적 생성자 특수화가 지원되지만 이후 릴리스에서는 지원되지 않을 수 있습니다.

다음 샘플에서는 C4812를 생성합니다.

```cpp
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```

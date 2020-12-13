---
description: '자세한 정보: 컴파일러 오류 C2754'
title: 컴파일러 오류 C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: 68840f85d7a7f9be18246dfa4f3176a76f0fb9ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336225"
---
# <a name="compiler-error-c2754"></a>컴파일러 오류 C2754

' 특수화 ': 부분 특수화에는 종속 형식이 아닌 템플릿 매개 변수를 사용할 수 없습니다.

종속 형식이 아닌 템플릿 매개 변수를 포함 하는 템플릿 클래스를 부분적으로 특수화 하려고 했습니다. 이것은 허용되지 않습니다.

다음 샘플에서는 C2754를 생성 합니다.

```cpp
// C2754.cpp
// compile with: /c

template<class T, T t>
struct A {};

template<class T, int N>
struct B {};

template<class T> struct A<T,5> {};   // C2754
template<> struct A<int,5> {};   // OK
template<class T> struct B<T,5> {};   // OK
```

---
description: '자세한 정보: 컴파일러 오류 C2912'
title: 컴파일러 오류 C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: 405c4acb5da6aa83e4b5d45e2297f1259a0d932e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270526"
---
# <a name="compiler-error-c2912"></a>컴파일러 오류 C2912

명시적 특수화 'declaration'이 함수 템플릿의 특수화가 아닙니다.

비템플릿 함수를 특수화할 수 없습니다.

다음 샘플에서는 C2912 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

이 오류는 Visual Studio .NET 2003에서 수행된 컴파일러 규칙 작업의 결과로 발생합니다. 모든 명시적 특수화의 경우 기본 템플릿의 매개 변수와 일치하도록 명시적 특수화의 매개 변수를 선택해야 합니다.

```cpp
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```

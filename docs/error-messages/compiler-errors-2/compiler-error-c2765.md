---
description: '자세한 정보: 컴파일러 오류 C2765'
title: 컴파일러 오류 C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 496f28645dddc0ac426716cc80ee0d6760042ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239547"
---
# <a name="compiler-error-c2765"></a>컴파일러 오류 C2765

' function ': 함수 템플릿의 명시적 특수화에는 기본 인수를 사용할 수 없습니다.

함수 템플릿의 명시적 특수화에는 기본 인수를 사용할 수 없습니다. 자세한 내용은 [함수 템플릿의 명시적 특수화](../../cpp/explicit-specialization-of-function-templates.md)를 참조 하세요.

다음 샘플에서는 C2765를 생성 합니다.

```cpp
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```

---
description: '자세한 정보: 함수 템플릿의 명시적 특수화'
title: 함수 템플릿의 명시적 특수화
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: c77ebce3383ba2051ac010c39a7dd0eb37b8111a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181503"
---
# <a name="explicit-specialization-of-function-templates"></a>함수 템플릿의 명시적 특수화

함수 템플릿을 사용하면 특정 형식에 대한 함수 템플릿의 명시적 특수화(재정의)를 제공하여 해당 형식에 대한 특별한 동작을 정의할 수 있습니다. 예를 들어:

```cpp
template<> void MySwap(double a, double b);
```

이 선언을 사용 하면 변수에 대해 다른 함수를 정의할 수 있습니다 **`double`** . 템플릿이 아닌 함수와 마찬가지로 표준 형식 변환 (예: 형식의 변수를 **`float`** 로 승격 **`double`** )이 적용 됩니다.

## <a name="example"></a>예제

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>참고 항목

[함수 템플릿](../cpp/function-templates.md)

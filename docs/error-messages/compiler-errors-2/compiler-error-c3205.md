---
description: '자세한 정보: 컴파일러 오류 C3205'
title: 컴파일러 오류 C3205
ms.date: 11/04/2016
f1_keywords:
- C3205
helpviewer_keywords:
- C3205
ms.assetid: 802d306e-5ff3-4491-8a22-c5f1c072d005
ms.openlocfilehash: bc85a414ee4ef1602f911833928b8f8dc7f49476
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164343"
---
# <a name="compiler-error-c3205"></a>컴파일러 오류 C3205

템플릿 매개 변수 'parameter'의 인수 목록이 없습니다.

[템플릿](../../cpp/templates-cpp.md) 매개 변수가 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3205를 생성합니다.

```cpp
// C3205.cpp
template<template<class> class T> struct A {
   typedef T unparameterized_type;   // C3205
   // try the following line instead
   // typedef T<int> unparameterized_type;
};

template <class T>
struct B {
   typedef int value_type;
};

int main() {
   A<B> x;
}
```

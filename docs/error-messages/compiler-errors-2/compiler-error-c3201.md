---
description: '자세한 정보: 컴파일러 오류 C3201'
title: 컴파일러 오류 C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 3cd6e037cd9dbb0638040e2f3eca61dab1dabb46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330650"
---
# <a name="compiler-error-c3201"></a>컴파일러 오류 C3201

클래스 템플릿 'template'에 대한 템플릿 매개 변수 목록이 템플릿 매개 변수 'template'에 대한 템플릿 매개 변수 목록과 일치하지 않습니다.

템플릿 매개 변수를 사용하지 않는 클래스 템플릿에 클래스 템플릿을 인수로 전달했거나 기본 템플릿 인수에 대해 일치하지 않는 개수의 템플릿 인수를 전달했습니다.

```cpp
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```

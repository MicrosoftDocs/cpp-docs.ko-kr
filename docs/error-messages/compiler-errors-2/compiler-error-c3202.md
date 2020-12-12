---
description: '자세한 정보: 컴파일러 오류 C3202'
title: 컴파일러 오류 C3202
ms.date: 11/04/2016
f1_keywords:
- C3202
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
ms.openlocfilehash: d3f090128a5290521aa64f9d834c200783bc2011
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291872"
---
# <a name="compiler-error-c3202"></a>컴파일러 오류 C3202

'arg name' : 템플릿 매개 변수 'parameter'에 대한 기본 인수가 잘못되었습니다. 클래스 템플릿이 필요합니다.

템플릿 매개 변수에 대해 잘못된 기본 인수를 전달했습니다.

다음 샘플에서는 C3202를 생성합니다.

```cpp
// C3202.cpp
template<typename T>
class X
{
};

class Z
{
};

template<template<typename U> class T1 = Z, typename T2> // C3202
class Y
{
};
```

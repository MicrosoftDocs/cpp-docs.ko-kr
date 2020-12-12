---
description: '자세한 정보: 컴파일러 오류 C3208'
title: 컴파일러 오류 C3208
ms.date: 11/04/2016
f1_keywords:
- C3208
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
ms.openlocfilehash: bd76a209fa3736449e8816473d0dee12daa93a61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173950"
---
# <a name="compiler-error-c3208"></a>컴파일러 오류 C3208

'function': 클래스 템플릿 'class'에 대한 템플릿 매개 변수 목록이 template 템플릿 매개 변수 'parameter'에 대한 템플릿 매개 변수 목록과 일치하지 않습니다.

template 템플릿 매개 변수의 템플릿 매개 변수 개수가 제공된 클래스 템플릿과 다릅니다.

다음 샘플에서는 C3208을 생성합니다.

```cpp
// C3208.cpp
template <template <class T> class TT >
int f();

template <class T1, class T2>
struct S;

template <class T1>
struct R;

int i = f<S>();   // C3208
// try the following line instead
// int i = f<R>();
```

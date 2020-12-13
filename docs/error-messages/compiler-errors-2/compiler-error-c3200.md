---
description: '자세한 정보: 컴파일러 오류 C3200'
title: 컴파일러 오류 C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: c693878628ff0bd9dddcb2f100ca652910b0fb89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330663"
---
# <a name="compiler-error-c3200"></a>컴파일러 오류 C3200

' template ': 템플릿 매개 변수 ' parameter '의 템플릿 인수가 잘못 되었습니다. 클래스 템플릿이 필요 합니다.

잘못 된 인수를 클래스 템플릿에 전달 했습니다. 클래스 템플릿에는 매개 변수로 템플릿이 필요 합니다. 다음 예제에서를 호출 하면 `Y<int, int> aY` C3200이 생성 됩니다. 첫 번째 매개 변수는와 같은 템플릿 이어야 `Y<X, int> aY` 합니다.

```cpp
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```

---
description: '자세한 정보: 컴파일러 오류 C2752'
title: 컴파일러 오류 C2752
ms.date: 11/04/2016
f1_keywords:
- C2752
helpviewer_keywords:
- C2752
ms.assetid: ae42b3ec-84a9-4e9d-8d59-3d208132d0b2
ms.openlocfilehash: 5a508ca9c286392bc05dd30602e138880882f813
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174431"
---
# <a name="compiler-error-c2752"></a>컴파일러 오류 C2752

' template ': 두 개 이상의 부분 특수화가 템플릿 인수 목록과 일치 합니다.

인스턴스화가 모호 합니다.

다음 샘플에서는 C2752를 생성 합니다.

```cpp
// C2752.cpp
template<class T, class U>
struct A {};

template<class T, class U>
struct A<T*, U> {};

template<class T, class U>
struct A<T,U*> {};

// try the following line instead
// template<class T, class U> struct A<T*,U*> {};

int main() {
   A<char*,int*> a;   // C2752 an instantiation

   // OK
   A<char*,int> a1;
   A<char,int*> a2;
   A<char,int> a3;
}
```

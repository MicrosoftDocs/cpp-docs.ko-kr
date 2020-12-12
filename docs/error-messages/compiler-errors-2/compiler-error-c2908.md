---
description: '자세한 정보: 컴파일러 오류 C2908'
title: 컴파일러 오류 C2908
ms.date: 11/04/2016
f1_keywords:
- C2908
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
ms.openlocfilehash: 086bc8d20f40f8dabb1aff1e30b45a73de8ab16a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270656"
---
# <a name="compiler-error-c2908"></a>컴파일러 오류 C2908

명시적 특수화 ' template '이 이미 인스턴스화 되었습니다.

기본 템플릿의 특수화는 명시적 특수화 이전에 발생 합니다.

다음 샘플에서는 C2908를 생성 합니다.

```cpp
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```

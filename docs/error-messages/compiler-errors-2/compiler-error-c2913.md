---
description: '자세한 정보: 컴파일러 오류 C2913'
title: 컴파일러 오류 C2913
ms.date: 11/04/2016
f1_keywords:
- C2913
helpviewer_keywords:
- C2913
ms.assetid: c6cf6090-02e8-49a5-913f-5bc6f864b769
ms.openlocfilehash: eba6a782c8ec9abe5c13e643d077c81d25d4bf2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270487"
---
# <a name="compiler-error-c2913"></a>컴파일러 오류 C2913

명시적 특수화 ' 선언 '은 클래스 템플릿의 특수화가 아닙니다.

템플릿이 아닌 클래스를 특수화할 수 없습니다.

다음 샘플에서는 C2913를 생성 합니다.

```cpp
// C2913.cpp
// compile with: /c
class X{};
template <class T> class Y{};

template<> class X<int> {};   // C2913
template<> class Y<int> {};
```

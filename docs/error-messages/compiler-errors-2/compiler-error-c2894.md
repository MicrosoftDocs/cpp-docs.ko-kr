---
description: '자세한 정보: 컴파일러 오류 C2894'
title: 컴파일러 오류 C2894
ms.date: 11/04/2016
f1_keywords:
- C2894
helpviewer_keywords:
- C2894
ms.assetid: 4e250579-2b59-4993-a6f4-49273e7ecf06
ms.openlocfilehash: dcb5f04cd7cd1ad9d2e6f0d645cabd512ed91c42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270922"
---
# <a name="compiler-error-c2894"></a>컴파일러 오류 C2894

템플릿에 ' C ' 링크가 있도록 선언할 수 없습니다.

이 오류는 블록 내에 정의 된 템플릿에 의해 발생할 수 있습니다 `extern "C"` .

다음 샘플에서는 C2894를 생성 합니다.

```cpp
// C2894.cpp
extern "C" {
   template<class T> class stack {};   // C2894 fail

   template<class T> void f(const T &aT) {}   // C2894
}
```

다음 샘플에서는 C2894를 생성 합니다.

```cpp
// C2894b.cpp
// compile with: /c
extern "C" template<class T> void f(const T &aT) {}   // C2894

template<class T> void f2(const T &aT) {}   // OK
```

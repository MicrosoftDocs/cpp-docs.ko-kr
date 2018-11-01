---
title: 컴파일러 오류 C2995
ms.date: 11/04/2016
f1_keywords:
- C2995
helpviewer_keywords:
- C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
ms.openlocfilehash: 56bd012457fe17cec7d46095ba7c98658d030b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557505"
---
# <a name="compiler-error-c2995"></a>컴파일러 오류 C2995

'function': 함수 템플릿이 이미 정의되었습니다.

템플릿 클래스의 각 멤버 함수에 대한 정의가 하나뿐인지 확인합니다.

다음 샘플에서는 C2995를 생성합니다.

```
// C2995.cpp
// compile with: /c
template <class T>
void Test(T x){}

template <class T> void Test(T x){}   // C2995
template <class T> void Test2(T x){}   // OK
```
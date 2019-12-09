---
title: 컴파일러 오류 C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: af30ccc4a71c51d042d6f7807a648a1eef066a70
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742667"
---
# <a name="compiler-error-c2970"></a>컴파일러 오류 C2970

' class ': 템플릿 매개 변수 ' param ': ' arg ': 내부 링크가 있는 개체를 포함 하는 식을 비 형식 인수로 사용할 수 없습니다.

정적 변수의 이름이 나 주소를 템플릿 인수로 사용할 수 없습니다. 템플릿 클래스에는 컴파일 시간에 계산할 수 있는 const 값이 필요 합니다.

다음 샘플에서는 C2970를 생성 합니다.

```cpp
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```

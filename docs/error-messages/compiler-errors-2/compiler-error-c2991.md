---
description: '자세한 정보: 컴파일러 오류 C2991'
title: 컴파일러 오류 C2991
ms.date: 11/04/2016
f1_keywords:
- C2991
helpviewer_keywords:
- C2991
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
ms.openlocfilehash: 9f42d96a15869b656abfff21a921ec340aa6ce1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338597"
---
# <a name="compiler-error-c2991"></a>컴파일러 오류 C2991

형식 매개 변수 'parameter' 재정의

`parameter`의 두 가지 제네릭 또는 템플릿 정의 간에 형식 충돌이 발생했습니다. 여러 제네릭 또는 템플릿 매개 변수를 정의할 때는 동일한 형식을 사용해야 합니다.

다음 샘플에서는 C2991을 생성합니다.

```cpp
// C2991.cpp
// compile with: /c
template<class T, class T> struct TC {};   // C2991
// try the following line instead
// template<class T, class T2> struct TC {};
```

C2991은 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2991b.cpp
// compile with: /clr /c
generic<class T,class T> ref struct GC {};   // C2991
// try the following line instead
// generic<class T,class T2> ref struct GC {};
```

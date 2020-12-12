---
description: '자세한 정보: 컴파일러 오류 C2935'
title: 컴파일러 오류 C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 853c1e51444454ffdbd09e8387d47eb9770d7fa7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320307"
---
# <a name="compiler-error-c2935"></a>컴파일러 오류 C2935

'class': type-class-id가 전역 함수로 재정의되었습니다.

제네릭 또는 템플릿 클래스를 전역 함수로 사용할 수 없습니다.

중괄호가 짝이 맞지 않는 경우 이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2935를 생성합니다.

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

제네릭을 사용할 때도 C2935가 발생할 수 있습니다.

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```

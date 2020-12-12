---
description: '자세한 정보: 컴파일러 오류 C3236'
title: 컴파일러 오류 C3236
ms.date: 11/04/2016
f1_keywords:
- C3236
helpviewer_keywords:
- C3236
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
ms.openlocfilehash: ed9a8e630a3c385bc3f7586c4f9db1e06259a3c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307511"
---
# <a name="compiler-error-c3236"></a>컴파일러 오류 C3236

제네릭을 명시적으로 인스턴스화할 수 없습니다.

컴파일러는 제네릭 클래스의 명시적 인스턴스화를 허용하지 않습니다.

다음 샘플에서는 C3236을 생성합니다.

```cpp
// C3236.cpp
// compile with: /clr
generic<class T>
public ref class X {};

generic ref class X<int>;   // C3236
```

다음 샘플에는 가능한 해결 방법을 보여 줍니다.

```cpp
// C3236b.cpp
// compile with: /clr /c
generic<class T>
public ref class X {};
```

---
title: 컴파일러 오류 C3857
ms.date: 11/04/2016
f1_keywords:
- C3857
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
ms.openlocfilehash: 2fe4973c3452e86449aec56c1f7cb40d5ea4a2cb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754812"
---
# <a name="compiler-error-c3857"></a>컴파일러 오류 C3857

' type ': 여러 형식 매개 변수 목록을 사용할 수 없습니다.

동일한 형식에 대해 둘 이상의 템플릿이나 제네릭를 지정 했지만이는 허용 되지 않습니다.

다음 샘플에서는 C3857를 생성 합니다.

```cpp
// C3857.cpp
template <class T, class TT>
template <class T2>    // C3857
struct B {};
```

가능한 해결 방법:

```cpp
// C3857b.cpp
// compile with: /c
template <class T, class TT, class T2>
struct B {};
```

제네릭을 사용 하는 경우에도 C3857이 발생할 수 있습니다.

```cpp
// C3857c.cpp
// compile with: /clr
generic <typename T>
generic <typename U>
ref class GC;   // C3857
```

가능한 해결 방법:

```cpp
// C3857d.cpp
// compile with: /clr /c
generic <typename U>
ref class GC;
```

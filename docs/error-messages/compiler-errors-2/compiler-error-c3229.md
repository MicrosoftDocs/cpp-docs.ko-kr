---
description: '자세한 정보: 컴파일러 오류 C3229'
title: 컴파일러 오류 C3229
ms.date: 11/04/2016
f1_keywords:
- C3229
helpviewer_keywords:
- C3229
ms.assetid: f2d90923-aa8b-444f-ab10-1f37dbb864e1
ms.openlocfilehash: 17d50d0bcc60357e024505499e002589525c5cba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304118"
---
# <a name="compiler-error-c3229"></a>컴파일러 오류 C3229

'type': 제네릭 형식 매개 변수에 대한 간접 참조는 허용되지 않습니다.

`*`, `^`또는 `&`와 제네릭 매개 변수를 사용할 수 없습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C3229를 생성합니다.

```cpp
// C3229.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   T^ t;   // C3229
};

// OK
generic <class T>
ref class D {
   T u;
};
```

다음 샘플에서는 C3229를 생성합니다.

```cpp
// C3229_b.cpp
// compile with: /clr /c
generic <class T>   // OK
ref class Utils {
   static void sort(T elems[], size_t size);   // C3229
   static void sort2(T elems, size_t size);   // OK
};
```

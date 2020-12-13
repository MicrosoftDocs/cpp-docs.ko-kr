---
description: '자세한 정보: 컴파일러 오류 C2179'
title: 컴파일러 오류 C2179
ms.date: 11/04/2016
f1_keywords:
- C2179
helpviewer_keywords:
- C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
ms.openlocfilehash: 17ddc839161f36efc668bb52504e2434ec82f995
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335226"
---
# <a name="compiler-error-c2179"></a>컴파일러 오류 C2179

' type ': 특성 인수는 형식 매개 변수를 사용할 수 없습니다.

제네릭 형식 매개 변수는 런타임에 확인 됩니다. 그러나 특성 매개 변수는 컴파일 타임에 확인 해야 합니다. 따라서 제네릭 형식 매개 변수를 특성에 대 한 인수로 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2179를 생성 합니다.

```cpp
// C2179.cpp
// compile with: /clr
using namespace System;

public ref struct Attr : Attribute {
   Attr(Type ^ a) {
      x = a;
   }

   Type ^ x;
};

ref struct G {};

generic<typename T>
public ref class Z {
public:
   Type ^ d;
   [Attr(T::typeid)]   // C2179
   // try the following line instead
   // [Attr(G::typeid)]
   T t;
};
```

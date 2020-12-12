---
description: '자세한 정보: 컴파일러 오류 C2903'
title: 컴파일러 오류 C2903
ms.date: 11/04/2016
f1_keywords:
- C2903
helpviewer_keywords:
- C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
ms.openlocfilehash: 0013be28857ac8e138a78cb7a4e3502cdc04536b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270734"
---
# <a name="compiler-error-c2903"></a>컴파일러 오류 C2903

'identifier': 기호가 클래스 템플릿 또는 함수 템플릿이 아닙니다.

코드에서 템플릿이 아닌 항목에 대해 명시적 인스턴스화를 시도합니다.

다음 샘플에서는 C2903을 생성합니다.

```cpp
// C2903.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template Y y;   // C2903
   N::X<N::Y> y;   // OK
}
```

제네릭을 사용할 때도 C2903이 발생할 수 있습니다.

```cpp
// C2903b.cpp
// compile with: /clr /c
namespace N {
   class Y {};
   generic<class T> ref class Z {};
}

void f() {
   N::generic Y y;   // C2903
   N:: generic Z<int>^ z;   // OK
}
```

---
description: '자세한 정보: 컴파일러 오류 C2931'
title: 컴파일러 오류 C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: a4d659a0529fa80affc6749d150b9a567d015d90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320333"
---
# <a name="compiler-error-c2931"></a>컴파일러 오류 C2931

'class': type-class-id가 'identifier'의 멤버 함수로 다시 정의되었습니다.

제네릭 또는 템플릿 클래스를 다른 클래스의 멤버 함수로 사용할 수 없습니다.

중괄호가 짝이 맞지 않는 경우 이 오류가 발생할 수 있습니다.

다음 샘플에서는 C2931을 생성합니다.

```cpp
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

C2931은 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```

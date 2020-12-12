---
description: '자세한 정보: 컴파일러 오류 C3804'
title: 컴파일러 오류 C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: b033acefd9a583b1659755f63fdbd3781fc95ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291508"
---
# <a name="compiler-error-c3804"></a>컴파일러 오류 C3804

' property_accessor ': 속성에 대 한 접근자 메서드는 모두 static 이거나 모두 static이 아니어야 합니다.

Trivial이 아닌 속성을 정의 하는 경우 접근자 함수는 정적 또는 인스턴스일 수 있지만 둘 다 사용할 수는 없습니다.

자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3804를 생성 합니다.

```cpp
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```

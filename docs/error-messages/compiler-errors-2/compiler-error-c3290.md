---
description: '자세한 정보: 컴파일러 오류 C3290'
title: 컴파일러 오류 C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: 68c0e79c233f7fbd416f6bdbe42cc555c04731fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337427"
---
# <a name="compiler-error-c3290"></a>컴파일러 오류 C3290

'type': trivial 속성은 참조 형식일 수 없습니다.

속성이 잘못 선언되었습니다. trivial 속성을 선언하면 컴파일러가 속성에서 업데이트할 변수를 만들며, 클래스에 추적 참조 변수를 사용할 수 없습니다.

자세한 내용은 [속성](../../extensions/property-cpp-component-extensions.md) 및 [추적 참조 연산자](../../extensions/tracking-reference-operator-cpp-component-extensions.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3290을 생성합니다.

```cpp
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```

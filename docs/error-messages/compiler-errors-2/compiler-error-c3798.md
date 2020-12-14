---
description: '자세한 정보: 컴파일러 오류 C3798'
title: 컴파일러 오류 C3798
ms.date: 11/04/2016
f1_keywords:
- C3798
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
ms.openlocfilehash: 394fe0f420c25fbabab44204e1793dc7dd5e9058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244838"
---
# <a name="compiler-error-c3798"></a>컴파일러 오류 C3798

' 지정자 ': 속성 선언에는 재정의 지정자를 사용할 수 없습니다. 대신 속성 get/set 메서드에 배치 해야 합니다.

속성이 잘못 선언되었습니다. 자세한 내용은 다음을 참조하세요.

- [property](../../extensions/property-cpp-component-extensions.md)

- [abstract](../../extensions/abstract-cpp-component-extensions.md)

- [sealed](../../extensions/sealed-cpp-component-extensions.md)

## <a name="example"></a>예제

다음 샘플에서는 C3798를 생성 합니다.

```cpp
// C3798.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_1 abstract;   // C3798
   property int Prop_2 sealed;   // C3798

   // OK
   property int Prop_3 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }

   property int Prop_4 {
      virtual int get() sealed;
      virtual void set(int i) sealed;
   }
};
```

---
description: '자세한 정보: 컴파일러 경고 C4485'
title: 컴파일러 경고 C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 85ce885aa299adf68b12d46f0a74af5aa55319f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180710"
---
# <a name="compiler-warning-c4485"></a>컴파일러 경고 C4485

' override_function ': 기본 ref 클래스 메서드 ' base_class_function '과 (와) 일치 하지만 ' new ' 또는 ' override '로 표시 되어 있지 않습니다. ' new ' (및 ' virtual ')를 가정 합니다.

접근자는 키워드를 사용 하거나 사용 하지 않고 **`virtual`** 기본 클래스 접근자 함수를 재정의 하지만 `override` 또는 지정자는 **`new`** 재정의 함수 시그니처의 일부가 아닙니다. **`new`** 또는 `override` 지정자를 추가 하 여이 경고를 해결 합니다.

자세한 내용은 [override](../../extensions/override-cpp-component-extensions.md) 및 [new (vtable의 새 슬롯)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) 를 참조 하세요.

C4485는 항상 오류로 실행 됩니다. C4485를 표시 하지 않으려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4485를 생성 합니다.

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```

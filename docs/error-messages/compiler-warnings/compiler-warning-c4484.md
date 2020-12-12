---
description: '자세한 정보: 컴파일러 경고 C4484'
title: 컴파일러 경고 C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 43228cabc8dfd728ea104f6c3b57d863ec9e5e5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180736"
---
# <a name="compiler-warning-c4484"></a>컴파일러 경고 C4484

' override_function ': 기본 ref 클래스 메서드 ' base_class_function '과 (와) 일치 하지만 ' virtual ', ' new ' 또는 ' override '로 표시 되어 있지 않습니다. ' new ' (및 ' virtual ' 아님)를 가정 합니다.

**/Clr** 을 사용 하 여 컴파일하는 경우 컴파일러는 기본 클래스 함수를 암시적으로 재정의 하지 않습니다. 즉, 함수가 vtable에서 새 슬롯을 가져옵니다. 이 문제를 해결 하려면 함수가 재정의 인지 여부를 명시적으로 지정 합니다.

자세한 내용은 다음을 참조하세요.

- [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new(vtable의 new 슬롯)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484는 항상 오류로 실행 됩니다. C4484를 표시 하지 않으려면 [warning](../../preprocessor/warning.md) pragma를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4484를 생성 합니다.

```cpp
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```

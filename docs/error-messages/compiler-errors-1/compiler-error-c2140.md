---
description: '자세한 정보: 컴파일러 오류 C2140'
title: 컴파일러 오류 C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: b9292019ce9a17c8f1dabca87f61f27b21494a82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124152"
---
# <a name="compiler-error-c2140"></a>컴파일러 오류 C2140

' type ': 제네릭 형식 매개 변수에 종속 된 형식은 컴파일러 내장 형식 특성 ' 특성 '에 대 한 인수로 사용할 수 없습니다.

형식 특성에 잘못 된 형식 지정 자가 전달 되었습니다.

자세한 내용은 [형식 특성에 대한 컴파일러 지원](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2140를 생성 합니다.

```cpp
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```

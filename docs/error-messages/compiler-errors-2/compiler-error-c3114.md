---
description: '자세한 정보: 컴파일러 오류 C3114'
title: 컴파일러 오류 C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 18d14ae01c0ae101ff0b66d837edd0699312af9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115952"
---
# <a name="compiler-error-c3114"></a>컴파일러 오류 C3114

' argument ': 명명 된 특성 인수가 잘못 되었습니다.

특성 클래스 데이터 멤버가 유효한 명명 된 인수가 되려면, 또는로 표시 되지 않아야 합니다 **`static`** **`const`** **`literal`** . 속성이 인 경우 속성은이 아니어야 하며 **`static`** get 및 set 접근자가 있어야 합니다.

자세한 내용은 [속성](../../extensions/property-cpp-component-extensions.md) 및 [사용자 정의 특성](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3114를 생성 합니다.

```cpp
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```

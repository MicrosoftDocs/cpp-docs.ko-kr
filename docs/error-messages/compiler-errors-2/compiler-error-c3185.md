---
description: '자세한 정보: 컴파일러 오류 C3185 오류가 발생'
title: 컴파일러 오류 C3185 오류가 발생
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 7dbcf11aa7c88d883aeccc8325832849f8b7a238
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242017"
---
# <a name="compiler-error-c3185"></a>컴파일러 오류 C3185 오류가 발생

'typeid' : 관리되는 형식 또는 WinRT 형식 'type'에 사용되었습니다. 대신 'operator'를 사용하세요.

관리 되는 형식 또는 WinRT 형식에는 [typeid](../../cpp/typeid-operator.md) 연산자를 적용할 수 없습니다. 대신 [typeid](../../extensions/typeid-cpp-component-extensions.md) 를 사용 하십시오.

다음 샘플에서는 C3185 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```

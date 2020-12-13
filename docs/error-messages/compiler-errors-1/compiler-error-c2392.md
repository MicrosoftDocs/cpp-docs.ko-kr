---
description: '자세한 정보: 컴파일러 오류 C2392'
title: 컴파일러 오류 C2392
ms.date: 11/04/2016
f1_keywords:
- C2392
helpviewer_keywords:
- C2392
ms.assetid: 98ced473-6383-46ed-b79c-21857d65dcb2
ms.openlocfilehash: 0a367ed1416b28bb27fc5d79d4a474de219e48e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337566"
---
# <a name="compiler-error-c2392"></a>컴파일러 오류 C2392

' method1 ': 공변 (covariant) 반환 형식은 관리 되는 또는 WinRTtypes에서 지원 되지 않습니다. 그렇지 않으면 ' method2 '이 재정의 됩니다.

공변 (Covariant) 반환 형식은 Windows 런타임 멤버 함수 또는 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 옵션을 사용 하 여 컴파일할 때 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2392 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2392.cpp
// compile with: /clr
public ref struct B {
public:
   int i;
};

public ref struct D: public B{};

public ref struct B1 {
public:
   virtual B^ mf() {
      B^ pB = gcnew B;
      pB->i = 11;
      return pB;
   }
};

public ref struct D1: public B1 {
public:
   virtual D^ mf() override {  // C2392
   // try the following line instead
   // virtual B^ mf() override {
   // return type D^ is covariant with B^, not allowed with CLR types
      D^ pD = gcnew D;
      pD->i = 12;
      return pD;
   }
};

int main() {
   B1^ pB1 = gcnew D1;
   B^ pB = pB1->mf();
   D^ pD = dynamic_cast<D^>(pB);
}
```

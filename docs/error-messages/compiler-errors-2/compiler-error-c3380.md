---
description: '자세한 정보: 컴파일러 오류 C3380'
title: 컴파일러 오류 C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: bb633d75d08fdbb902f086b3a4cd6a8a6db1fc69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334985"
---
# <a name="compiler-error-c3380"></a>컴파일러 오류 C3380

'class': 어셈블리 액세스 지정자가 잘못되었습니다. 'public' 또는 'private'만 사용할 수 있습니다.

관리되는 클래스 또는 구조체에 적용하는 경우 [public](../../cpp/public-cpp.md) 및 [private](../../cpp/private-cpp.md) 키워드는 클래스가 어셈블리 메타데이터를 통해 노출되는지 여부를 나타냅니다. `public` 또는 `private` 만 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)로 컴파일된 프로그램의 클래스에 적용할 수 있습니다.

`ref` `value` [/Clr](../../build/reference/clr-common-language-runtime-compilation.md)과 함께 사용 될 경우 및 키워드는 클래스가 관리 됨을 나타내고, 클래스 [및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조 하세요.

다음 샘플에서는 C3380을 생성합니다.

```cpp
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```

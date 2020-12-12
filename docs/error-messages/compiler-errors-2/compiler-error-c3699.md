---
description: '자세한 정보: 컴파일러 오류 C3699'
title: 컴파일러 오류 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: 670b5c41aad9afcece8d8cd292727ad64925a4ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228718"
---
# <a name="compiler-error-c3699"></a>컴파일러 오류 C3699

' operator ': ' type ' 형식에 대해이 간접 참조를 사용할 수 없습니다.

에서 허용 되지 않는 간접 참조를 사용 하려고 `type` 한 경우

## <a name="examples"></a>예제

다음 샘플에서는 C3699를 생성 합니다.

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

Trivial 속성에는 참조 형식을 사용할 수 없습니다. 자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md) 를 참조하세요. 다음 샘플에서는 C3699를 생성 합니다.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

"포인터에 대 한 포인터" 구문에 해당 하는 것은 추적 참조에 대 한 핸들입니다. 다음 샘플에서는 C3699를 생성 합니다.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```

---
description: '자세한 정보: 컴파일러 오류 C2725'
title: 컴파일러 오류 C2725
ms.date: 11/04/2016
f1_keywords:
- C2725
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
ms.openlocfilehash: 92594737bf06095ffb230cac6bb6d233fc6f9307
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155490"
---
# <a name="compiler-error-c2725"></a>컴파일러 오류 C2725

'exception': 관리되는 또는 WinRT 개체를 값이나 참조로 throw 또는 catch할 수 없습니다.

관리되는 또는 WinRT 예외의 형식이 올바르지 않습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C2725를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

다음 샘플에서는 C2725를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```

---
description: '자세한 정보: 방법: 네이티브 형식에서 값 형식에 대 한 참조 유지'
title: '방법: 값 형식에 대한 참조를 네이티브 형식에 저장'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- value type reference in native type
- reference to value type in native type
ms.assetid: 1eabf8be-7d4f-4339-9027-48d5c4244483
ms.openlocfilehash: 4f012b2590b6085e965f3cd1420dbcba4347c84d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134890"
---
# <a name="how-to-hold-reference-to-value-type-in-native-type"></a>방법: 값 형식에 대한 참조를 네이티브 형식에 저장

Boxed 형식에서를 사용 `gcroot` 하 여 네이티브 형식에 값 형식에 대 한 참조를 포함 합니다.

## <a name="example"></a>예제

```cpp
// reference_to_value_in_native.cpp
// compile with: /clr
#using <mscorlib.dll>
#include <vcclr.h>

using namespace System;

public value struct V {
   String ^str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

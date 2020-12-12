---
description: '자세한 정보: 방법: 표준 문자열을 System:: String으로 변환'
title: '방법: 표준 문자열을 System::String으로 변환'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, converting strings to System::String
- string conversion [C++], C++ Standard Library string
- strings [C++], converting
ms.assetid: 1fde79a0-9d0b-44e5-981b-e8f2676c199d
ms.openlocfilehash: b42e321f7819bf61149e17b5281badf4704bdbfb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181360"
---
# <a name="how-to-convert-standard-string-to-systemstring"></a>방법: 표준 문자열을 System::String으로 변환

이 항목에서는 c + + 표준 라이브러리 문자열 ()을로 변환 하는 방법을 보여 줍니다 [\<string>](../standard-library/string.md) <xref:System.String> .

## <a name="example"></a>예제

```cpp
// convert_standard_string_to_system_string.cpp
// compile with: /clr
#include <string>
#include <iostream>
using namespace System;
using namespace std;

int main() {
   string str = "test";
   cout << str << endl;
   String^ str2 = gcnew String(str.c_str());
   Console::WriteLine(str2);

   // alternatively
   String^ str3 = gcnew String(str.c_str());
   Console::WriteLine(str3);
}
```

```Output
test
test
test
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

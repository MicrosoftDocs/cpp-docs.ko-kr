---
description: '자세한 정보: 방법: System:: String을 wchar_t * 또는 char *로 변환'
title: '방법: System::String을 wchar_t* 또는 char*로 변환'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- System::String, converting to char or wchar_t
- PtrToStringChars method
- System::String
- wchart type, converting System::String
- char data type, converting System::String to
ms.assetid: 385da01b-5649-4543-8076-e3e251243ff0
ms.openlocfilehash: 973d9c71e536865188dc03d88821dacce4b20e52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198364"
---
# <a name="how-to-convert-systemstring-to-wchar_t-or-char"></a>방법: System::String을 wchar_t* 또는 char*로 변환

Vcclr에서를 사용 하 여를 `PtrToStringChars` <xref:System.String> 네이티브 또는로 변환할 `wchar_t *` 수 `char *` 있습니다.  CLR 문자열은 내부적으로 유니코드 이므로 항상 와이드 유니코드 문자열 포인터를 반환 합니다. 그런 다음, 다음 예제와 같이 와이드에서 변환할 수 있습니다.

## <a name="example"></a>예제

```cpp
// convert_string_to_wchar.cpp
// compile with: /clr
#include < stdio.h >
#include < stdlib.h >
#include < vcclr.h >

using namespace System;

int main() {
   String ^str = "Hello";

   // Pin memory so GC can't move it while native function is called
   pin_ptr<const wchar_t> wch = PtrToStringChars(str);
   printf_s("%S\n", wch);

   // Conversion to char* :
   // Can just convert wchar_t* to char* using one of the
   // conversion functions such as:
   // WideCharToMultiByte()
   // wcstombs_s()
   // ... etc
   size_t convertedChars = 0;
   size_t  sizeInBytes = ((str->Length + 1) * 2);
   errno_t err = 0;
   char    *ch = (char *)malloc(sizeInBytes);

   err = wcstombs_s(&convertedChars,
                    ch, sizeInBytes,
                    wch, sizeInBytes);
   if (err != 0)
      printf_s("wcstombs_s  failed!\n");

    printf_s("%s\n", ch);
}
```

```Output
Hello
Hello
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

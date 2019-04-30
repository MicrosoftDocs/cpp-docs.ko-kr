---
title: '방법: 관리 되지 않는 리소스를 바이트 배열로 로드'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- native resources, loading into Byte array
- unmanaged resources, loading into Byte array
- native resources
ms.assetid: cdada6cd-6d42-437a-a90f-44a0b18d6a93
ms.openlocfilehash: 641bdf4429bca35800e3fbbbb7622f2651bb3fee
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344963"
---
# <a name="how-to-load-unmanaged-resources-into-a-byte-array"></a>방법: 관리 되지 않는 리소스를 바이트 배열로 로드

이 항목에서는 설명에 관리 되지 않는 리소스를 로드 하는 여러 가지 방법으로 <xref:System.Byte> 배열입니다.

## <a name="example"></a>예제

관리 되지 않는 리소스의 크기를 알고 있으면 CLR 배열 미리 할당할 수 있으며 CLR 배열의 배열 블록에 대 한 포인터를 사용 하 여 배열에 리소스를 로드 합니다.

```
// load_unmanaged_resources_into_Byte_array.cpp
// compile with: /clr
using namespace System;
void unmanaged_func( unsigned char * p ) {
   for ( int i = 0; i < 10; i++ )
      p[ i ] = i;
}

public ref class A {
public:
   void func() {
      array<Byte> ^b = gcnew array<Byte>(10);
      pin_ptr<Byte> p =  &b[ 0 ];
      Byte * np = p;
      unmanaged_func( np );   // pass pointer to the block of CLR array.
      for ( int i = 0; i < 10; i++ )
         Console::Write( b[ i ] );
      Console::WriteLine();
   }
};

int main() {
   A^ g = gcnew A;
   g->func();
}
```

```Output
0123456789
```

## <a name="example"></a>예제

이 샘플에는 관리 되는 배열에는 관리 되지 않는 메모리 블록에서 데이터를 복사 하는 방법을 보여 줍니다.

```
// load_unmanaged_resources_into_Byte_array_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <string.h>
int main() {
   char buf[] = "Native String";
   int len = strlen(buf);
   array<Byte> ^byteArray = gcnew array<Byte>(len + 2);

   // convert any native pointer to IntPtr by doing C-Style cast
   Marshal::Copy( (IntPtr)buf, byteArray, 0, len );
}
```

## <a name="see-also"></a>참고자료

[C++ Interop 사용(암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

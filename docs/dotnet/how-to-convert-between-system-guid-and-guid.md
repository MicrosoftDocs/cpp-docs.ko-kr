---
description: '자세히 알아보기: 방법: System:: Guid와 _GUID 간 변환'
title: '방법: System::Guid 및 _GUID 사이에 변환'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- System::GUID
- GUID, converting to System::GUID
- System::GUID, converting to GUID
ms.assetid: 022c934c-3395-4f04-b498-85ad9bf8c646
ms.openlocfilehash: 1f2eb87f23e7f47221b4506c2c9e328803b800e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304391"
---
# <a name="how-to-convert-between-systemguid-and-_guid"></a>방법: System::Guid 및 _GUID 사이에 변환

다음 코드 샘플에서는와를 변환 하는 방법을 보여 줍니다 <xref:System.Guid> `_GUID` .

## <a name="example"></a>예제

```cpp
// convert_guids.cpp
// compile with: /clr
#include <windows.h>
#include <stdio.h>

using namespace System;

Guid FromGUID( _GUID& guid ) {
   return Guid( guid.Data1, guid.Data2, guid.Data3,
                guid.Data4[ 0 ], guid.Data4[ 1 ],
                guid.Data4[ 2 ], guid.Data4[ 3 ],
                guid.Data4[ 4 ], guid.Data4[ 5 ],
                guid.Data4[ 6 ], guid.Data4[ 7 ] );
}

_GUID ToGUID( Guid& guid ) {
   array<Byte>^ guidData = guid.ToByteArray();
   pin_ptr<Byte> data = &(guidData[ 0 ]);

   return *(_GUID *)data;
}

int main() {
   _GUID ng = {0x11111111,0x2222,0x3333,0x44,0x55,0x55,0x55,0x55,0x55,0x55,0x55};
   Guid mg;

   Console::WriteLine( (mg = FromGUID( ng )).ToString() );
   _GUID ng2 = ToGUID( mg );

   printf_s(  "%x-%x-%x-", ng2.Data1, ng2.Data2, ng2.Data3 );
   for (int i = 0 ; i < 8 ; i++) {
      if (i == 2)
         printf_s("-");
      printf_s("%x", ng2.Data4[i]);
   }
   printf_s("\n");
}
```

```Output
11111111-2222-3333-4455-555555555555
11111111-2222-3333-4455-555555555555
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

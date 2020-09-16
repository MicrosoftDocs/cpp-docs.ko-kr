---
title: '방법: System::String의 문자에 액세스'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: cb62eb0fecbee202e4d01635a60da565241822ee
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686797"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>방법: System::String의 문자에 액세스

<xref:System.String>문자열을 사용 하는 관리 되지 않는 함수에 대 한 고성능 호출을 위해 개체의 문자에 액세스할 수 있습니다 `wchar_t*` . 메서드는 개체의 첫 번째 문자에 대 한 내부 포인터를 생성 <xref:System.String> 합니다. 이 포인터는 직접 조작 하거나 고정 하 여 일반 문자열을 필요로 하는 함수에 전달할 수 있습니다 **`wchar_t`** .

## <a name="examples"></a>예제

`PtrToStringChars` 라고도 하는 <xref:System.Char> 내부 포인터인를 반환 `byref` 합니다. 따라서 가비지 수집의 영향을 받습니다. 네이티브 함수에 전달 하지 않는 한이 포인터를 고정할 필요가 없습니다.

다음과 같은 코드를 생각해 볼 수 있습니다.  `ppchar`는 내부 포인터이 고, 가비지 수집기가 가리키는 문자열을 이동 하는 경우에도 업데이트 됩니다 `ppchar` . [Pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md)를 사용 하지 않으면 코드가 작동 하 고 고정으로 인 한 잠재적인 성능 저하가 발생 하지 않습니다.

네이티브 함수에 전달 하는 경우 고정 포인터 여야 합니다. `ppchar` 가비지 수집기가 관리 되지 않는 스택 프레임의 포인터를 업데이트할 수 없습니다.

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

이 예제에서는 고정이 필요한 위치를 보여 줍니다.

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

내부 포인터는 네이티브 c + + 포인터의 모든 속성을 포함 합니다. 예를 들어이 메서드를 사용 하 여 연결 된 데이터 구조를 탐색 하 고 하나의 포인터만 사용 하 여 삽입 및 삭제를 수행할 수 있습니다.

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>추가 정보

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

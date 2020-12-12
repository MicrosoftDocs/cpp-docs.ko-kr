---
description: '자세한 정보: 방법: 관리 되지 않는 메모리에 개체 참조 유지'
title: '방법: 관리되지 않는 메모리에 개체 참조 유지'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 9c54d0ce376e57c5865c2fef5987d878bfa8d7f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134929"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>방법: 관리되지 않는 메모리에 개체 참조 유지

로 래핑하는 gcroot를 사용 하 여 <xref:System.Runtime.InteropServices.GCHandle> 관리 되지 않는 메모리에 CLR 개체 참조를 저장할 수 있습니다. 또는 직접를 사용할 수 있습니다 `GCHandle` .

## <a name="examples"></a>예제

```cpp
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

`GCHandle` 관리 되지 않는 메모리에서 관리 되는 개체 참조를 유지 하는 방법을 제공 합니다.  메서드를 사용 하 여 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 관리 되는 개체에 대 한 불투명 핸들을 만들고 <xref:System.Runtime.InteropServices.GCHandle.Free%2A> 해제 합니다. 또한 메서드를 <xref:System.Runtime.InteropServices.GCHandle.Target%2A> 사용 하면 관리 코드의 핸들에서 개체 참조를 다시 가져올 수 있습니다.

```cpp
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

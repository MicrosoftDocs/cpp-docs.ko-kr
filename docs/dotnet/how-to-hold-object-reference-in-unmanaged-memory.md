---
title: '방법: 관리 되지 않는 메모리에 개체 참조 유지 | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3153a34844885e2b753bf68d74b7757c5d11fb1d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443464"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>방법: 관리되지 않는 메모리에 개체 참조 유지

래핑하는 gcroot.h를 사용할 수 있습니다 <xref:System.Runtime.InteropServices.GCHandle>, 관리 되지 않는 메모리에 CLR 개체 참조를 유지할 수 있습니다. 사용할 수 있습니다 `GCHandle` 직접.

## <a name="example"></a>예제

```
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

## <a name="example"></a>예제

`GCHandle` 관리 되지 않는 메모리에서 관리 되는 개체 참조를 보유 하는 방법을 제공 합니다.  사용 된 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 불투명 핸들을 관리 되는 개체를 만드는 방법 및 <xref:System.Runtime.InteropServices.GCHandle.Free%2A> 해제 합니다. 또한는 <xref:System.Runtime.InteropServices.GCHandle.Target%2A> 메서드를 사용 하면 관리 코드에 있는 핸들에서 개체 참조를 가져올 수 있습니다.

```
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

[C++ Interop 사용(암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
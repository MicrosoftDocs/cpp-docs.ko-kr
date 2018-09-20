---
title: auto_handle::release | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_handle::release
- auto_handle.release
- msclr.auto_handle.release
- auto_handle::release
dev_langs:
- C++
helpviewer_keywords:
- auto_handle::release
ms.assetid: d4848150-859e-4c61-a946-09d24d3d6577
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5237ec59d8e90a793d6df83d6dbc2c0ff1ec1cb0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391750"
---
# <a name="autohandlerelease"></a>auto_handle::release

개체를 해제 `auto_handle` 관리 합니다.

## <a name="syntax"></a>구문

```
_element_type ^ release();
```

## <a name="return-value"></a>반환 값

출시 된 개체입니다.

## <a name="example"></a>예제

```
// msl_auto_handle_release.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_handle 멤버](../dotnet/auto-handle-members.md)<br/>
[auto_handle::~auto_handle](../dotnet/auto-handle-tilde-auto-handle.md)<br/>
[auto_handle::reset](../dotnet/auto-handle-reset.md)
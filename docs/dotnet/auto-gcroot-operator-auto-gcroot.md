---
title: auto_gcroot::operator auto_gcroot
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_gcroot.operator auto_gcroot
- auto_gcroot::operator auto_gcroot
- msclr.auto_gcroot.operator auto_gcroot
- msclr::auto_gcroot::operator auto_gcroot
helpviewer_keywords:
- auto_gcroot operator
ms.assetid: 43e3f27a-9f68-444f-9149-a9282a9b935a
ms.openlocfilehash: 1c434400774cf1cd96f324298ccff51dd3bf2496
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474505"
---
# <a name="autogcrootoperator-autogcroot"></a>auto_gcroot::operator auto_gcroot

형식 캐스팅 연산자 간의 `auto_gcroot` 및 호환 되는 형식입니다.

## <a name="syntax"></a>구문

```
template<typename _other_type>
operator auto_gcroot<_other_type>();
```

## <a name="return-value"></a>반환 값

현재 `auto_gcroot` 캐스팅할 `auto_gcroot<_other_type>`합니다.

## <a name="example"></a>예제

```
// msl_auto_gcroot_op_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassB^> b = gcnew ClassB("first");
   b->PrintHello();
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_gcroot 멤버](../dotnet/auto-gcroot-members.md)
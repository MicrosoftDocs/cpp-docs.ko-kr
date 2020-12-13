---
description: '자세히 알아보기: 기본값 (c + +)'
title: default (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 83c4a17f513db755395ed978d57c9c6f01f84ca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333005"
---
# <a name="default-c"></a>default(C++)

coclass 내에 정의된 custom 또는 dispinterface가 기본 프로그래밍 인터페이스를 나타낸다는 것을 의미합니다.

## <a name="syntax"></a>구문

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>매개 변수

*interface1*<br/>
특성으로 정의 된 클래스에 따라 개체를 만드는 스크립팅 환경에 사용할 수 있는 기본 인터페이스입니다 **`default`** .

지정된 기본 인터페이스가 없는 경우 처음에 발생하는 비 소스 인터페이스가 기본값으로 사용됩니다.

*interface2*<br/>
필드 기본 소스 인터페이스입니다. 이 인터페이스는 [source](source-cpp.md) 특성을 사용하여 지정해야 합니다.

지정된 기본 소스 인터페이스가 없는 경우 첫 번째 소스 인터페이스가 기본값으로 사용됩니다.

## <a name="remarks"></a>설명

**`default`** C + + 특성에는 [기본](/windows/win32/Midl/default) MIDL 특성과 동일한 기능이 있습니다. **`default`** 특성은 [case](case-cpp.md) 특성에도 사용 됩니다.

## <a name="example"></a>예제

다음 코드에서는 **`default`** coclass의 정의에서를 사용 하 여를 `ICustomDispatch` 기본 프로그래밍 인터페이스로 지정 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[원본](source-cpp.md) 특성에는를 사용 하는 방법에 대 한 예제도 있습니다 **`default`** .

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`** , 데이터 멤버|
|**불가능**|아니요|
|**필수 특성**|**coclass** (또는에 적용 된 경우 **`class`** **`struct`** )|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[coclass](coclass.md)

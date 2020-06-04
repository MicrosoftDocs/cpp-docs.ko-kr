---
title: 바인딩 가능C++ (COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 9e476183374ad2a70864fd46aaa19c616cd3ce91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167357"
---
# <a name="bindable"></a>bindable

속성이 데이터 바인딩을 지원합니다.

## <a name="syntax"></a>구문

```cpp
[bindable]
```

## <a name="remarks"></a>설명

**바인딩** C++ 가능한 특성에는 [바인딩](/windows/win32/Midl/bindable) 가능한 MIDL 특성과 동일한 기능이 있습니다. [Propget](propget.md), [propput](propput.md)또는 [propputref](propputref.md) 특성으로 정의 된 속성에 사용할 수도 있고, 바인딩 가능한 메서드를 수동으로 정의할 수도 있습니다.

다음 MFC 샘플에서는 **바인딩**가능를 사용 하는 방법을 보여 줍니다.

- [컨트롤 샘플: MFC 기반 ActiveX 컨트롤](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [CIRC 샘플: ActiveX 컨트롤](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [TESTHELP 샘플: 도구 설명 및 도움말이 있는 ActiveX 컨트롤](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>예제

다음 코드에서는 속성에 **바인딩** 가능한를 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|인터페이스 메서드|
|**반복 가능**|예|
|**필수 특성**|None|
|**잘못된 특성**|None|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)

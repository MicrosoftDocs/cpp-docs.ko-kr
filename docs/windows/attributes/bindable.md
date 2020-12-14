---
description: '다음에 대 한 자세한 정보: 바인딩 가능'
title: 바인딩 가능 (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 2427becd3353488cc1b62347c04d7ed62e523352
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247490"
---
# <a name="bindable"></a>bindable

속성이 데이터 바인딩을 지원합니다.

## <a name="syntax"></a>구문

```cpp
[bindable]
```

## <a name="remarks"></a>설명

**바인딩** 가능한 c + + 특성에는 [바인딩](/windows/win32/Midl/bindable) 가능한 MIDL 특성과 동일한 기능이 있습니다. [Propget](propget.md), [propput](propput.md)또는 [propputref](propputref.md) 특성으로 정의 된 속성에 사용할 수도 있고, 바인딩 가능한 메서드를 수동으로 정의할 수도 있습니다.

다음 MFC 샘플에서는 **바인딩** 가능를 사용 하는 방법을 보여 줍니다.

- [컨트롤 샘플: ActiveX 컨트롤 MFC-Based](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

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

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)

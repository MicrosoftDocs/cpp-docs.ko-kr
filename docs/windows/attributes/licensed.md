---
description: '자세한 정보: 사용이 허가 됨'
title: 사용이 허가 됨 (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.licensed
helpviewer_keywords:
- licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
ms.openlocfilehash: 348180412c1e8b19994cf5ef3e9bedb4115bfbda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327528"
---
# <a name="licensed"></a>licensed

는 해당 개체가 적용 되는 COM 개체가 사용이 허가 되 고를 사용 하 여 인스턴스화해야 함을 나타냅니다 `IClassFactory2` .

## <a name="syntax"></a>구문

```cpp
[licensed]
```

## <a name="remarks"></a>설명

**사용이 허가** 된 c + + 특성에는 [사용이 허가](/windows/win32/Midl/licensed) 된 MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_licensed.cpp
// compile with: /LD
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {
   HRESULT f();
};

[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),
licensed, threading(free), progid(some.name)]
class CSample : public IMyI {
public:
   int nSize;
};

[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|`coclass`|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)

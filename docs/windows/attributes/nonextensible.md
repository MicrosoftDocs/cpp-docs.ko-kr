---
description: '자세히 알아보기: 비 확장 가능'
title: 비 확장 가능 (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: dfb0eda0fc8c6de367ee29ec3786750ba40395ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327450"
---
# <a name="nonextensible"></a>nonextensible

`IDispatch`구현 시 인터페이스 설명에 나열 된 속성 및 메서드만 포함 하 고 런타임에 추가 멤버로 확장할 수 없도록 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[nonextensible]
```

## <a name="remarks"></a>설명

**비 확장 가능** c + + 특성에는 [비 확장](/windows/win32/Midl/nonextensible) MIDL 특성과 동일한 기능이 있습니다.

**비 확장** 을 사용 하려면 [oleautomation](oleautomation.md) 특성도 필요 합니다.

## <a name="example"></a>예제

다음 코드에서는 **비 확장할** 수 있는 특성을 사용 하는 한 가지 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**interface**|
|**불가능**|아니요|
|**필수 특성**|`dual` 및 `oleautomation` 또는 `dispinterface`|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)

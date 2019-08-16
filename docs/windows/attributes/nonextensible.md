---
title: 비 확장 가능C++ (COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514404"
---
# <a name="nonextensible"></a>nonextensible

`IDispatch` 구현 시 인터페이스 설명에 나열 된 속성 및 메서드만 포함 하 고 런타임에 추가 멤버로 확장할 수 없도록 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[nonextensible]
```

## <a name="remarks"></a>설명

**비 확장 가능** C++ 특성에는 [비 확장](/windows/win32/Midl/nonextensible) MIDL 특성과 동일한 기능이 있습니다.

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

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**interface**|
|**반복 가능**|아니요|
|**필수 특성**|`dual`및 `oleautomation`또는`dispinterface`|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)
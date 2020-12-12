---
description: '자세히 알아보기: 제한 됨'
title: 제한 (c + + COM 특성)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 8c0dc33d1ae7cff3625f1a938cac05c7ac72f474
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329614"
---
# <a name="restricted"></a>restricted

모듈, 인터페이스 또는 인터페이스의 멤버를 임의로 호출할 수 없도록 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>매개 변수

*interfaces*<br/>
COM 개체에서 임의로 호출할 수 없는 하나 이상의 인터페이스입니다. 이 매개 변수는 클래스에 적용 된 경우에만 유효 합니다.

## <a name="remarks"></a>설명

**제한** 된 c + + 특성에는 [제한](/windows/win32/Midl/restricted) 된 MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드는 **제한** 된 특성을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 메서드, **인터페이스**, **`class`** , **`struct`**|
|**불가능**|아니요|
|**필수 특성**|**coclass** (또는에 적용 된 경우 **`class`** **`struct`** )|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[메서드 특성](method-attributes.md)

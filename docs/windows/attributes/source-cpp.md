---
description: '자세한 정보: 소스 (c + +)'
title: source (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 493795f41571fd9c940147eda3b8dd6dd543f18a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327294"
---
# <a name="source-c"></a>source(C++)

클래스에서 연결 지점의 COM 개체에 대 한 소스 인터페이스를 지정 합니다. 속성이 나 메서드에서는 멤버가 이벤트 소스인 개체 또는 변형을 반환 함을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>매개 변수

*interfaces*<br/>
원본 특성을 클래스에 적용할 때 지정 하는 하나 이상의 인터페이스입니다. 소스가 속성 또는 메서드에 적용 되는 경우에는이 매개 변수가 사용 되지 않습니다.

## <a name="remarks"></a>설명

**원본** c + + 특성에는 [소스](/windows/win32/Midl/source) MIDL 특성과 동일한 기능이 있습니다.

[기본](default-cpp.md) 특성을 사용 하 여 개체에 대 한 기본 소스 인터페이스를 지정할 수 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`** , **인터페이스**|
|**불가능**|아니요|
|**필수 특성**|`coclass` (클래스 또는 구조체에 적용 된 경우)|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[coclass](coclass.md)

---
title: readonly (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: 93f7393f76596766e841dfc25f6d12e20e3db618
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514127"
---
# <a name="readonly-c"></a>readonly(C++)

데이터 멤버에 대한 할당을 금지합니다.

## <a name="syntax"></a>구문

```cpp
[readonly]
```

## <a name="remarks"></a>설명

**readonly** C++ 특성에는 [readonly](/windows/win32/Midl/readonly) MIDL 특성과 동일한 기능이 있습니다.

메서드 매개 변수의 수정을 금지하려면 [in](in-cpp.md) 특성을 사용합니다.

## <a name="example"></a>예제

다음 코드에서는 **readonly** 특성의 사용을 보여줍니다.

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|인터페이스 메서드|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[데이터 멤버 특성](data-member-attributes.md)
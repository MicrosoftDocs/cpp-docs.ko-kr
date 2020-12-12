---
description: '다음에 대 한 자세한 정보: requires_category'
title: requires_category (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: 4d2a68e682c4247174ffba630126b5d2f6061788
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327302"
---
# <a name="requires_category"></a>requires_category

대상 클래스의 필수 구성 요소 범주를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>매개 변수

*requires_category*<br/>
필수 범주의 ID입니다.

## <a name="remarks"></a>설명

**Requires_category** c + + 특성은 대상 클래스에 필요한 구성 요소 범주를 지정 합니다. 자세한 내용은 [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category)를 참조 하세요.

이 특성을 사용하려면 [coclass](coclass.md), [progid](progid.md)또는 [vi_progid](vi-progid.md) 특성(또는 이 중 하나를 암시하는 다른 특성)을 동일한 요소에 적용해야 합니다.

## <a name="example"></a>예제

다음 코드에서는 개체가 컨트롤 범주를 구현 해야 합니다.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|`coclass`, 또는 중 하나 이상입니다. `progid` `vi_progid`|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[COM 특성](com-attributes.md)<br/>
[implements_category](implements-category.md)

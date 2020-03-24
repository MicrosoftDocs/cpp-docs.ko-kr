---
title: synchronize (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214515"
---
# <a name="synchronize"></a>synchronize

대상 메서드에 대 한 액세스를 동기화 합니다.

## <a name="syntax"></a>구문

```cpp
[synchronize]
```

## <a name="remarks"></a>주의

**Synchronize** C++ 특성은 개체의 대상 메서드 동기화에 대 한 지원을 구현 합니다. 동기화를 통해 여러 개체에서 대상 메서드의 액세스를 제어 하 여 공용 리소스 (예: 클래스의 메서드)를 사용할 수 있습니다.

이 특성으로 삽입 된 코드는 대상 메서드의 시작 부분에서 적절 한 `Lock` 메서드 (스레딩 모델에 의해 결정 됨)를 호출 합니다. 메서드가 종료 되 면 `Unlock` 자동으로 호출 됩니다. 이러한 함수에 대 한 자세한 내용은 [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock) 을 참조 하세요.

이 특성을 사용하려면 [coclass](coclass.md), [progid](progid.md)또는 [vi_progid](vi-progid.md) 특성(또는 이 중 하나를 암시하는 다른 특성)을 동일한 요소에 적용해야 합니다. 단일 특성을 사용하는 경우 다른 두 특성도 자동으로 적용됩니다. 예를 들어 `progid` 적용 되는 경우 `vi_progid` 및 `coclass`도 적용 됩니다.

## <a name="example"></a>예제

다음 코드는 `CMyClass` 개체의 `UpdateBalance` 메서드에 대 한 동기화를 제공 합니다.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|클래스 메서드, 메서드|
|**반복 가능**|아니요|
|**필수 특성**|`coclass`, `progid`또는 `vi_progid`중 하나 이상입니다.|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[COM 특성](com-attributes.md)

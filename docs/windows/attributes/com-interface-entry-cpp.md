---
description: '자세한 정보: com_interface_entry (c + +)'
title: com_interface_entry (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 2f182149eeac887292391cbb06f625aff261e91f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114887"
---
# <a name="com_interface_entry-c"></a>com_interface_entry(C++)

인터페이스 항목을 대상 클래스의 COM 맵에 추가 합니다.

## <a name="syntax"></a>구문

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>매개 변수

*com_interface_entry*<br/>
항목의 실제 텍스트를 포함 하는 문자열입니다. 가능한 값 목록은 [COM_INTERFACE_ENTRY 매크로](../../atl/reference/com-interface-entry-macros.md)를 참조 하세요.

## <a name="remarks"></a>설명

**Com_interface_entry** c + + 특성은 문자열의 unabridged 콘텐츠를 대상 개체의 com 인터페이스 맵에 삽입 합니다. 특성이 대상 개체에 한 번 적용 되 면 항목이 기존 인터페이스 맵의 시작 부분에 삽입 됩니다. 특성이 동일한 대상 개체에 반복 해 서 적용 되 면 항목이 인터페이스 맵 시작 부분에서 수신 된 순서 대로 삽입 됩니다.

이 특성을 사용하려면 [coclass](coclass.md), [progid](progid.md)또는 [vi_progid](vi-progid.md) 특성(또는 이 중 하나를 암시하는 다른 특성)을 동일한 요소에 적용해야 합니다. 단일 특성을 사용하는 경우 다른 두 특성도 자동으로 적용됩니다. 예를 들어를 적용 하는 경우 `progid` `vi_progid` 및 `coclass` 도 적용 됩니다.

**Com_interface_entry** 를 처음 사용 하는 경우에는 인터페이스 맵의 시작 부분에 새 인터페이스가 삽입 되기 때문에 다음 COM_INTERFACE_ENTRY 유형 중 하나 여야 합니다.

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

**Com_interface_entry** 특성을 추가로 사용 하 여 지원 되는 모든 COM_INTERFACE_ENTRY 유형을 사용할 수 있습니다.

이 제한은 ATL이 인터페이스 맵의 첫 번째 항목을 id로 사용 하기 때문에 필요 합니다 `IUnknown` . 따라서 항목은 유효한 인터페이스 여야 합니다. 예를 들어 다음 코드 샘플은 인터페이스 맵의 첫 번째 항목이 실제 COM 인터페이스를 지정 하지 않기 때문에 유효 하지 않습니다.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>예제

다음 코드에서는의 기존 COM 인터페이스 맵에 두 개의 항목을 추가 합니다 `CMyBaseClass` . 첫 번째는 표준 인터페이스 이며 두 번째는 인터페이스를 숨깁니다 `IDebugTest` .

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

에 대 한 결과 COM 개체 맵은 다음과 같습니다 `CMyBaseClass` .

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|예|
|**필수 특성**|`coclass`, 또는 중 하나 이상입니다. `progid` `vi_progid`|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[COM 특성](com-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)

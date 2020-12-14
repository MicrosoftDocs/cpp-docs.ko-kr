---
description: '자세한 정보: coclass'
title: coclass (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 9ff2198807407a7dfc56649ed80cb1fa2bafc17c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247373"
---
# <a name="coclass"></a>coclass

Com 인터페이스를 구현할 수 있는 COM 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
[coclass]
```

## <a name="remarks"></a>설명

**Coclass** c + + 특성은 생성 된 .idl 파일에 coclass 구문을 배치 합니다.

Coclass를 정의할 때 [uuid](uuid-cpp-attributes.md), [version](version-cpp.md), [스레딩](threading-cpp.md), [vi_progid](vi-progid.md)및 [progid](progid.md) 특성도 지정할 수 있습니다. 이러한 항목 중 하나를 지정 하지 않으면 생성 됩니다.

두 헤더 파일에 **coclass** 특성이 있는 클래스가 포함 되어 있고 GUID를 지정 하지 않는 경우 컴파일러는 두 클래스에 동일한 GUID를 사용 하 고이로 인해 MIDL 오류가 발생 합니다.  따라서 `uuid` **coclass** 를 사용 하는 경우 특성을 사용 해야 합니다.

**ATL 프로젝트**

이 특성이 ATL 프로젝트의 클래스 또는 구조체 정의 앞에 오면 다음과 같이 됩니다.

- 개체에 대 한 자동 등록을 지원 하기 위해 코드 또는 데이터를 삽입 합니다.

- 개체에 대 한 COM 클래스 팩터리를 지 원하는 코드 또는 데이터를 삽입 합니다.

- 구현 하는 코드 또는 데이터를 삽입 하 `IUnknown` 고 개체를 COM에서 만들 수 있는 개체로 만듭니다.

특히, 다음 기본 클래스는 대상 개체에 추가 됩니다.

- [CComCoClass 클래스](../../atl/reference/ccomcoclass-class.md) 는 개체에 대 한 기본 클래스 팩터리 및 집계 모델을 제공 합니다.

- [CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md) 에는 [스레딩](threading-cpp.md) 특성에 의해 지정 된 스레딩 모델 클래스를 기반으로 하는 템플릿이 있습니다. 특성을 `threading` 지정 하지 않으면 기본 스레딩 모델은 아파트입니다.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) 는 대상 개체에 대해 [noncreatable](noncreatable.md) 특성이 지정 되지 않은 경우에 추가 됩니다.

마지막으로, 포함 IDL을 사용 하 여 정의 되지 않은 모든 이중 인터페이스는 해당 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) 클래스로 대체 됩니다. 이중 인터페이스가 포함 IDL에 정의 되어 있는 경우 기본 목록에 있는 특정 인터페이스는 수정 되지 않습니다.

또한 **coclass** 특성은 삽입 된 코드를 통해 또는의 경우 `GetObjectCLSID` 기본 클래스의 정적 메서드로 다음 함수를 사용할 수 있도록 합니다 `CComCoClass` .

- `UpdateRegistry` 대상 클래스의 클래스 팩터리를 등록 합니다.

- `GetObjectCLSID`등록과 관련 된를 사용 하 여 대상 클래스의 CLSID를 가져올 수도 있습니다.

- `GetObjectFriendlyName` 기본적으로는 "" 형식의 문자열을 반환 \<*target class name*> `Object` 합니다. 이 함수가 이미 있으면 추가 되지 않습니다. 대상 클래스에이 함수를 추가 하 여 자동으로 생성 된 것 보다 친숙 한 이름을 반환 합니다.

- `GetProgID`등록과 관련 된는 [progid](progid.md) 특성으로 지정 된 문자열을 반환 합니다.

- `GetVersionIndependentProgID` 에는와 동일한 기능이 `GetProgID` 있지만 [vi_progid](vi-progid.md)로 지정 된 문자열을 반환 합니다.

COM 맵과 관련 된 다음과 같은 변경 내용은 대상 클래스에 적용 됩니다.

- COM 맵은 대상 클래스가 파생 되는 모든 인터페이스에 대 한 항목과, [Com 인터페이스 진입점](../../mfc/com-interface-entry-points.md) 특성에 지정 된 모든 항목 또는 [집계](aggregates.md) 특성에 필요한 모든 항목을 포함 하 여 추가 됩니다.

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 매크로가 COM 맵에 삽입 됩니다.

클래스의 .idl 파일에서 생성 된 coclass의 이름은 클래스와 동일한 이름을 갖습니다.  예를 들어, 다음 샘플을 참조 하 여 coclass에 대 한 클래스 ID에 액세스 하려면 `CMyClass` MIDL에서 생성 된 헤더 파일을 통해 클라이언트에서를 사용 `CLSID_CMyClass` 합니다.

## <a name="example"></a>예제

다음 코드에서는 **coclass** 특성을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

다음 샘플에서는 **coclass** 특성에 의해 삽입 된 코드에 표시 되는 함수의 기본 구현을 재정의 하는 방법을 보여 줍니다. 삽입된 코드 보기에 대한 자세한 정보는 [/Fx](../../build/reference/fx-merge-injected-code.md) 를 참조하세요. 클래스에 사용 하는 모든 기본 클래스 또는 인터페이스는 삽입 된 코드에 표시 됩니다. 또한 클래스가 삽입 된 코드에 기본적으로 포함 되어 있고 해당 클래스를 coclass의 기반으로 명시적으로 지정 하는 경우 특성 공급자가 코드에 지정 된 형식을 사용 합니다.

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[COM 특성](com-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)

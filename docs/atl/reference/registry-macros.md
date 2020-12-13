---
description: '자세한 정보: 레지스트리 매크로'
title: 레지스트리 매크로
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: e1f85e43f64dd34455cb9ec453ab3719b07f67f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138890"
---
# <a name="registry-macros"></a>레지스트리 매크로

이러한 매크로는 유용한 형식 라이브러리 및 레지스트리 기능을 정의 합니다.

|Name|설명|
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|ATL.DLL에 대 한 종속성을 방지 하기 위해 개체에 대 한 등록 코드를 개체에 표시 하도록 지정 합니다.|
|[DECLARE_LIBID](#declare_libid)|ATL이 형식 라이브러리의 *libid* 를 가져오는 방법을 제공 합니다.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|기본 ATL 등록을 방지 합니다.|
|[DECLARE_REGISTRY](#declare_registry)|시스템 레지스트리에서 주 개체의 항목을 입력 하거나 제거 합니다.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|*Appid* 를 자동으로 등록 하는 데 필요한 정보를 지정 합니다.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|명명 된 리소스를 찾고 그 안에 있는 레지스트리 스크립트를 실행 합니다.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|ID 번호로 식별 되는 리소스를 찾아서 그 안에 있는 레지스트리 스크립트를 실행 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a> _ATL_STATIC_REGISTRY

ATL.DLL에 대 한 종속성을 방지 하기 위해 개체에 대 한 등록 코드를 개체에 표시 하도록 지정 하는 기호입니다.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>설명

ATL_STATIC_REGISTRY를 정의 하는 경우 다음 코드를 사용 해야 합니다.

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a> DECLARE_LIBID

ATL이 형식 라이브러리의 *libid* 를 가져오는 방법을 제공 합니다.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>매개 변수

*libid*<br/>
형식 라이브러리의 GUID입니다.

### <a name="remarks"></a>설명

파생 클래스에서 DECLARE_LIBID를 사용 `CAtlModuleT` 합니다.

### <a name="example"></a>예제

특성을 사용 하지 않는 마법사에서 생성 된 ATL 프로젝트에는이 매크로를 사용 하는 샘플이 있습니다.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a> DECLARE_NO_REGISTRY

이 매크로가 표시 되는 클래스에 대 한 기본 ATL 등록을 방지 하려면 DECLARE_NO_REGISTRY을 사용 합니다.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a> DECLARE_REGISTRY

시스템 레지스트리에 표준 클래스 등록을 입력 하거나 시스템 레지스트리에서 제거 합니다.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>매개 변수

*class*<br/>
진행 이전 버전과의 호환성을 위해 포함 되었습니다.

*pid*<br/>
진행 버전별 프로그램 식별자 인 LPCTSTR.

*vpid*<br/>
진행 버전 독립적 프로그램 식별자 인 LPCTSTR.

*nid*<br/>
진행 프로그램에 대 한 설명으로 사용할 레지스트리의 리소스 문자열 인덱스에 해당 하는 UINT입니다.

*flags*<br/>
진행 레지스트리의 프로그램 스레딩 모델을 포함 하는 DWORD입니다. THREADFLAGS_APARTMENT, THREADFLAGS_BOTH 또는 AUTPRXFLAG 값 중 하나 여야 합니다.

### <a name="remarks"></a>설명

표준 등록은 CLSID, 프로그램 ID, 버전 독립 프로그램 ID, 설명 문자열 및 스레드 모델로 구성 됩니다.

ATL 클래스 추가 마법사를 사용 하 여 개체 또는 컨트롤을 만드는 경우 마법사는 스크립트 기반 레지스트리 지원을 자동으로 구현 하 고 파일에 [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) 매크로를 추가 합니다. 스크립트 기반 레지스트리 지원을 원하지 않는 경우이 매크로를 DECLARE_REGISTRY으로 바꾸어야 합니다. DECLARE_REGISTRY은 위에 설명 된 5 개의 기본 키만 레지스트리에 삽입 합니다. 레지스트리에 다른 키를 삽입 하는 코드를 수동으로 작성 해야 합니다.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a> DECLARE_REGISTRY_APPID_RESOURCEID

*Appid* 를 자동으로 등록 하는 데 필요한 정보를 지정 합니다.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>매개 변수

*resid로*<br/>
*Appid* 에 대 한 정보가 포함 된 .rgs 파일의 리소스 id입니다.

*appid*<br/>
GUID

### <a name="remarks"></a>설명

파생 클래스에서 DECLARE_REGISTRY_APPID_RESOURCEID를 사용 `CAtlModuleT` 합니다.

### <a name="example"></a>예제

클래스 코드 추가 마법사를 사용 하 여 ATL 프로젝트에 추가 된 클래스에는이 매크로를 사용 하는 샘플이 포함 됩니다.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a> DECLARE_REGISTRY_RESOURCE

레지스트리 파일을 포함 하는 명명 된 리소스를 가져오고 스크립트를 실행 하 여 시스템 레지스트리에 개체를 입력 하거나 시스템 레지스트리에서 제거 합니다.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 리소스의 문자열 식별자입니다.

### <a name="remarks"></a>설명

ATL 프로젝트 마법사를 사용 하 여 개체 또는 컨트롤을 만드는 경우 마법사는 스크립트 기반 레지스트리 지원을 자동으로 구현 하 고 DECLARE_REGISTRY_RESOURCE와 유사한 [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) 매크로를 파일에 추가 합니다.

최적화 된 레지스트리 액세스를 위해 ATL 레지스트리 구성 요소 (등록자)에 정적으로 연결할 수 있습니다. 등록자 코드에 정적으로 연결 하려면 *.pch* 파일 (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에 다음 줄을 추가 합니다.

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

런타임에 대체 값을 대체 값으로 대체 하려는 경우 DECLARE_REGISTRY_RESOURCE 또는 DECLARE_REGISTRY_RESOURCEID 매크로를 지정 하지 마십시오. 대신, 구조체의 배열을 만듭니다 `_ATL_REGMAP_ENTRIES` . 여기에서 각 항목에는 런타임에 자리 표시자를 대체 하기 위한 값과 쌍을 이루는 변수 자리 표시 자가 포함 됩니다. 그런 다음, 배열을 전달 하 여 [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) 또는 [UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)를 호출 합니다. 이렇게 하면 구조체의 모든 교체 값이 `_ATL_REGMAP_ENTRIES` 등록자의 대체 맵에 추가 됩니다.

대체 가능한 매개 변수 및 스크립팅에 대 한 자세한 내용은 [ATL 레지스트리 구성 요소 (등록자)](../../atl/atl-registry-component-registrar.md)문서를 참조 하세요.

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a> DECLARE_REGISTRY_RESOURCEID

마법사에서 생성 한 UINT를 사용 하 여 문자열 이름이 아니라 리소스를 식별 한다는 점을 제외 하 고 [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) 와 동일 합니다.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 마법사가 생성 한 리소스의 식별자입니다.

### <a name="remarks"></a>설명

ATL 프로젝트 마법사를 사용 하 여 개체 또는 컨트롤을 만들면 마법사에서 자동으로 스크립트 기반 레지스트리 지원을 구현 하 고 파일에 DECLARE_REGISTRY_RESOURCEID 매크로를 추가 합니다.

최적화 된 레지스트리 액세스를 위해 ATL 레지스트리 구성 요소 (등록자)에 정적으로 연결할 수 있습니다. 등록자 코드에 정적으로 연결 하려면 *stdafx.h* 파일에 다음 줄을 추가 합니다 (Visual Studio 2019 이상에서 *.pch. h* ).

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

런타임에 대체 값을 대체 값으로 대체 하려는 경우 DECLARE_REGISTRY_RESOURCE 또는 DECLARE_REGISTRY_RESOURCEID 매크로를 지정 하지 마십시오. 대신, 구조체의 배열을 만듭니다 `_ATL_REGMAP_ENTRIES` . 여기에서 각 항목에는 런타임에 자리 표시자를 대체 하기 위한 값과 쌍을 이루는 변수 자리 표시 자가 포함 됩니다. 그런 다음, 배열을 전달 하 여 [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) 또는 [UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)를 호출 합니다. 이렇게 하면 구조체의 모든 교체 값이 `_ATL_REGMAP_ENTRIES` 등록자의 대체 맵에 추가 됩니다.

대체 가능한 매개 변수 및 스크립팅에 대 한 자세한 내용은 [ATL 레지스트리 구성 요소 (등록자)](../../atl/atl-registry-component-registrar.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)

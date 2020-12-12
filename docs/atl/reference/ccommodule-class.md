---
description: '자세히 알아보기: CComModule 클래스'
title: CComModule 클래스
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: dd0ec6c6aa7d68374a90830b10815a9cbdd54aeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152024"
---
# <a name="ccommodule-class"></a>CComModule 클래스

ATL 7.0부터 `CComModule` 은 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComModule:: GetClassObject](#getclassobject)|지정 된 CLSID의 개체를 만듭니다. Dll에만 해당 합니다.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|`m_hInst`를 반환합니다.|
|[CComModule::GetResourceInstance](#getresourceinstance)|`m_hInstResource`를 반환합니다.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|`m_hInstTypeLib`를 반환합니다.|
|[CComModule::Init](#init)|데이터 멤버를 초기화 합니다.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|시스템 레지스트리에 개체의 표준 클래스 등록을 입력 합니다.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|클래스 개체를 등록 합니다. Exe 전용입니다.|
|[CComModule::RegisterServer](#registerserver)|개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 합니다.|
|[CComModule::RegisterTypeLib](#registertypelib)|형식 라이브러리를 등록합니다.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|클래스 개체를 취소 합니다. Exe 전용입니다.|
|[CComModule::Term](#term)|데이터 멤버를 해제 합니다.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|시스템 레지스트리에서 개체의 표준 클래스 등록을 제거 합니다.|
|[CComModule::UnregisterServer](#unregisterserver)|개체 맵에서 각 개체의 등록을 취소 합니다.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|개체의 표준 클래스 등록을 등록 하거나 등록 취소 합니다.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|ATL 레지스트리 구성 요소에 정적으로 링크 합니다. 지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|개체 맵 정보에 대 한 동기화 된 액세스를 보장 합니다.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|형식 라이브러리 정보에 대 한 동기화 된 액세스를 보장 합니다.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|창 생성 중에 사용 되는 창 클래스 정보 및 정적 데이터에 대 한 동기화 된 액세스를 보장 합니다.|
|[CComModule::m_hInst](#m_hinst)|모듈 인스턴스에 대 한 핸들을 포함 합니다.|
|[CComModule::m_hInstResource](#m_hinstresource)|기본적으로는 모듈 인스턴스에 대 한 핸들을 포함 합니다.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|기본적으로는 모듈 인스턴스에 대 한 핸들을 포함 합니다.|
|[CComModule::m_pObjMap](#m_pobjmap)|모듈 인스턴스에 의해 유지 관리 되는 개체 맵을 가리킵니다.|

## <a name="remarks"></a>설명

> [!NOTE]
> 이 클래스는 더 이상 사용 되지 않으며, ATL 코드 생성 마법사는 이제 이상 버전의, [Catlautothreadmodule](../../atl/reference/catlautothreadmodule-class.md) 및 [bclmodule](../../atl/reference/catlmodule-class.md) 파생 클래스를 사용 합니다. 자세한 내용은 [ATL 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요. 다음 정보는 ATL의 이전 릴리스로 만든 응용 프로그램에서 사용 하기 위한 것입니다. `CComModule` 은 (는) 이전 기능을 위해 여전히 ATL의 일부입니다.

`CComModule` 클라이언트에서 모듈의 구성 요소에 액세스할 수 있도록 COM 서버 모듈을 구현 합니다. `CComModule` 에서는 DLL (in-process) 및 EXE (로컬) 모듈을 모두 지원 합니다.

`CComModule`인스턴스는 개체 맵을 사용 하 여 클래스 개체 정의 집합을 유지 관리 합니다. 이 개체 맵은 구조체의 배열로 구현 `_ATL_OBJMAP_ENTRY` 되며에 대 한 정보를 포함 합니다.

- 시스템 레지스트리에서 개체 설명 입력 및 제거

- 클래스 팩터리를 통해 개체를 인스턴스화합니다.

- 클라이언트와 구성 요소에서 루트 개체 간의 통신 설정

- 클래스 개체의 수명 관리를 수행 하는 중입니다.

ATL COM 응용 프로그램을 실행 하면 마법사에서 `_Module` 의 전역 인스턴스나 `CComModule` 이 클래스에서 파생 된 클래스를 자동으로 생성 합니다. ATL 프로젝트 마법사에 대 한 자세한 내용은 [Atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)문서를 참조 하세요.

뿐만 아니라 `CComModule` ATL은 exe 및 Windows 서비스에 대 한 아파트 모델 모듈을 구현 하는 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)을 제공 합니다. `CComAutoThreadModule`여러 아파트에서 개체를 만들려는 경우에서 모듈을 파생 시킵니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a> CComModule:: GetClassObject

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>매개 변수

*rclsid*<br/>
진행 만들 개체의 CLSID입니다.

*riid*<br/>
진행 요청 된 인터페이스의 IID입니다.

*ppv*<br/>
제한이 *Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않는 경우 *ppv* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

지정 된 CLSID의 개체를 만들고이 개체에 대 한 인터페이스 포인터를 검색 합니다.

`GetClassObject` Dll에만 사용할 수 있습니다.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a> CComModule:: GetModuleInstance

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>반환 값

이 모듈을 식별 하는 HINSTANCE입니다.

### <a name="remarks"></a>설명

[M_hInst](#m_hinst) 데이터 멤버를 반환 합니다.

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a> CComModule:: GetResourceInstance

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>반환 값

HINSTANCE입니다.

### <a name="remarks"></a>설명

[M_hInstResource](#m_hinstresource) 데이터 멤버를 반환 합니다.

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a> CComModule:: GetTypeLibInstance

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>반환 값

HINSTANCE입니다.

### <a name="remarks"></a>설명

[M_hInstTypeLib](#m_hinsttypelib) 데이터 멤버를 반환 합니다.

## <a name="ccommoduleinit"></a><a name="init"></a> CComModule:: Init

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 개체 맵 항목의 배열에 대 한 포인터입니다.

*h*<br/>
진행 또는에 전달 된 HINSTANCE `DLLMain` `WinMain` 입니다.

*plibid*<br/>
진행 프로젝트에 연결 된 형식 라이브러리의 LIBID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

모든 데이터 멤버를 초기화 합니다.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a> CComModule:: m_csObjMap

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>설명

개체 맵에 대 한 동기화 된 액세스를 보장 합니다.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a> CComModule:: m_csTypeInfoHolder

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>설명

형식 라이브러리에 대 한 동기화 된 액세스를 보장 합니다.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a> CComModule:: m_csWindowCreate

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>설명

창 클래스 정보 및 창 생성 중에 사용 되는 정적 데이터에 대 한 동기화 된 액세스를 보장 합니다.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a> CComModule:: m_hInst

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>설명

모듈 인스턴스에 대 한 핸들을 포함 합니다.

[Init](#init) 메서드는 `m_hInst` 또는에 전달 된 핸들로 설정 `DLLMain` 합니다 `WinMain` .

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a> CComModule:: m_hInstResource

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>설명

기본적으로는 모듈 인스턴스에 대 한 핸들을 포함 합니다.

[Init](#init) 메서드는 `m_hInstResource` 또는에 전달 된 핸들로 설정 `DLLMain` 합니다 `WinMain` . 리소스에 대 한 핸들을 명시적으로 설정할 수 있습니다 `m_hInstResource` .

[Getresourceinstance](#getresourceinstance) 메서드는에 저장 된 핸들을 반환 합니다 `m_hInstResource` .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a> CComModule:: m_hInstTypeLib

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>설명

기본적으로는 모듈 인스턴스에 대 한 핸들을 포함 합니다.

[Init](#init) 메서드는 `m_hInstTypeLib` 또는에 전달 된 핸들로 설정 `DLLMain` 합니다 `WinMain` . `m_hInstTypeLib`형식 라이브러리에 대 한 핸들을 명시적으로 설정할 수 있습니다.

[GetTypeLibInstance](#gettypelibinstance) 메서드는에 저장 된 핸들을 반환 합니다 `m_hInstTypeLib` .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a> CComModule:: m_pObjMap

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>설명

모듈 인스턴스에 의해 유지 관리 되는 개체 맵을 가리킵니다.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a> CComModule:: RegisterClassHelper

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 등록할 개체의 CLSID입니다.

*lpszProgID*<br/>
진행 개체와 연결 된 ProgID입니다.

*lpszVerIndProgID*<br/>
진행 개체와 연결 된 버전 독립 ProgID입니다.

*nDescID*<br/>
진행 개체의 설명에 대 한 문자열 리소스의 식별자입니다.

*dwFlags*<br/>
진행 레지스트리에 입력할 스레딩 모델을 지정 합니다. 가능한 값은 THREADFLAGS_APARTMENT, THREADFLAGS_BOTH 또는 AUTPRXFLAG입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

시스템 레지스트리에 개체의 표준 클래스 등록을 입력 합니다.

[UpdateRegistryClass](#updateregistryclass) 메서드는를 호출 합니다 `RegisterClassHelper` .

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a> CComModule:: RegisterClassObjects

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>매개 변수

*dwClsContext*<br/>
진행 클래스 개체가 실행 될 컨텍스트를 지정 합니다. 가능한 값은 CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER 또는 CLSCTX_LOCAL_SERVER입니다. 이러한 값에 대 한 설명은 Windows SDK의 [Clsctx](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 를 참조 하세요.

*dwFlags*<br/>
진행 클래스 개체에 대 한 연결 유형을 결정 합니다. 가능한 값은 REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE 또는 REGCLS_MULTI_SEPARATE입니다. 이러한 값에 대 한 설명은 Windows SDK의 [Regcls](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

다른 응용 프로그램에서 연결할 수 있도록 OLE를 사용 하 여 EXE 클래스 개체를 등록 합니다. 이 메서드는 Exe에 대해서만 사용할 수 있습니다.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a> CComModule:: RegisterServer

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*bRegTypeLib*<br/>
진행 형식 라이브러리를 등록할지 여부를 나타냅니다. 기본값은 FALSE입니다.

*pCLSID*<br/>
진행 등록할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

*Pclsid* 매개 변수에 따라는 단일 클래스 개체 또는 개체 맵의 모든 개체에 대 한 시스템 레지스트리를 업데이트 합니다.

*Bregtypelib* 가 TRUE 이면 형식 라이브러리 정보도 업데이트 됩니다.

개체 맵에 항목을 추가 하는 방법에 대 한 자세한 내용은 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 를 참조 하세요.

`RegisterServer` 는 `DLLRegisterServer` DLL에 대해 또는 `WinMain` 명령줄 옵션을 사용 하 여 EXE를 실행 하는 경우에 의해 자동으로 호출 됩니다 `/RegServer` .

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a> CComModule:: RegisterTypeLib

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>매개 변수

*lpszIndex*<br/>
진행 형식의 문자열입니다 `"\\N"` `N` . 여기서은 TYPELIB 리소스의 정수 인덱스입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

형식 라이브러리에 대 한 정보를 시스템 레지스트리에 추가 합니다.

모듈 인스턴스에 여러 형식 라이브러리가 포함 된 경우이 메서드의 두 번째 버전을 사용 하 여 사용할 형식 라이브러리를 지정 합니다.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a> CComModule:: RevokeClassObjects

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

클래스 개체를 제거 합니다. 이 메서드는 Exe에 대해서만 사용할 수 있습니다.

## <a name="ccommoduleterm"></a><a name="term"></a> CComModule:: Term

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```cpp
void Term() throw();
```

### <a name="remarks"></a>설명

모든 데이터 멤버를 해제 합니다.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a> CComModule:: UnregisterClassHelper

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 등록을 취소할 개체의 CLSID입니다.

*lpszProgID*<br/>
진행 개체와 연결 된 ProgID입니다.

*lpszVerIndProgID*<br/>
진행 개체와 연결 된 버전 독립 ProgID입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

시스템 레지스트리에서 개체의 표준 클래스 등록을 제거 합니다.

[UpdateRegistryClass](#updateregistryclass) 메서드는를 호출 합니다 `UnregisterClassHelper` .

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a> CComModule:: UnregisterServer

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>매개 변수

*bUnRegTypeLib*<br/>
TRUE 이면 형식 라이브러리도 등록 취소 됩니다.

*pCLSID*<br/>
등록을 취소할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 취소 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

*Pclsid* 매개 변수에 따라 단일 클래스 개체 또는 개체 맵의 모든 개체를 등록 취소 합니다.

`UnregisterServer` 는 `DLLUnregisterServer` DLL에 대해 또는 `WinMain` 명령줄 옵션을 사용 하 여 EXE를 실행 하는 경우에 의해 자동으로 호출 됩니다 `/UnregServer` .

개체 맵에 항목을 추가 하는 방법에 대 한 자세한 내용은 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 를 참조 하세요.

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a> CComModule:: UpdateRegistryClass

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
등록 하거나 등록 취소할 개체의 CLSID입니다.

*lpszProgID*<br/>
개체와 연결 된 ProgID입니다.

*lpszVerIndProgID*<br/>
개체와 연결 된 버전 독립 ProgID입니다.

*nDescID*<br/>
개체의 설명에 대 한 문자열 리소스의 식별자입니다.

*szDesc*<br/>
개체의 설명을 포함 하는 문자열입니다.

*dwFlags*<br/>
레지스트리에 입력할 스레딩 모델을 지정 합니다. 가능한 값은 THREADFLAGS_APARTMENT, THREADFLAGS_BOTH 또는 AUTPRXFLAG입니다.

*bRegister*<br/>
개체를 등록 해야 하는지 여부를 나타냅니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

*BRegister* 가 TRUE 이면이 메서드는 시스템 레지스트리에 개체의 표준 클래스 등록을 입력 합니다.

*BRegister* 가 FALSE 이면 개체의 등록이 제거 됩니다.

*BRegister* 의 값에 따라는 `UpdateRegistryClass` [RegisterClassHelper](#registerclasshelper) 또는 [UnregisterClassHelper](#unregisterclasshelper)를 호출 합니다.

[DECLARE_REGISTRY](registry-macros.md#declare_registry) 매크로를 지정 하면 `UpdateRegistryClass` 개체 맵이 처리 될 때가 자동으로 호출 됩니다.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a> CComModule:: UpdateRegistryFromResourceD

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>매개 변수

*lpszRes*<br/>
진행 리소스 이름입니다.

*nResID*<br/>
진행 리소스 ID입니다.

*bRegister*<br/>
진행 개체를 등록 해야 하는지 여부를 나타냅니다.

*pMapEntries*<br/>
진행 스크립트의 대체 가능 매개 변수와 연결 된 값을 저장 하는 대체 맵에 대 한 포인터입니다. ATL은 자동으로 `%MODULE%` 을 사용 합니다. 대체 가능한 추가 매개 변수를 사용 하려면 자세한 내용은 설명 부분을 참조 하십시오. 그렇지 않으면 NULL 기본값을 사용 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

*LpszRes* 또는 *nResID* 에 지정 된 리소스에 포함 된 스크립트를 실행 합니다.

*BRegister* 가 TRUE 이면이 메서드는 시스템 레지스트리에 개체를 등록 합니다. 그렇지 않으면 개체의 등록을 취소 합니다.

[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) 또는 [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) 매크로를 지정 하면 `UpdateRegistryFromResourceD` 개체 맵이 처리 될 때가 자동으로 호출 됩니다.

> [!NOTE]
> 런타임에 대체 값을 대체 하려면 DECLARE_REGISTRY_RESOURCE 또는 DECLARE_REGISTRY_RESOURCEID 매크로를 지정 하지 마십시오. 대신, 구조체의 배열을 만듭니다 `_ATL_REGMAP_ENTRIES` . 여기에서 각 항목에는 런타임에 자리 표시자를 대체 하기 위한 값과 쌍을 이루는 변수 자리 표시 자가 포함 됩니다. 그런 다음 `UpdateRegistryFromResourceD` 를 호출 하 여 *Pmapentries* 매개 변수에 대 한 배열을 전달 합니다. 이렇게 하면 구조의 모든 대체 값이 `_ATL_REGMAP_ENTRIES` 등록자의 대체 맵에 추가 됩니다.

> [!NOTE]
> ATL 레지스트리 구성 요소 (등록자)에 정적으로 연결 하려면 [UpdateRegistryFromResourceS](#updateregistryfromresources)을 참조 하세요.

대체 가능한 매개 변수 및 스크립팅에 대 한 자세한 내용은 [ATL 레지스트리 구성 요소 (등록자)](../../atl/atl-registry-component-registrar.md)문서를 참조 하세요.

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a> CComModule:: UpdateRegistryFromResourceS

ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*lpszRes*<br/>
진행 리소스 이름입니다.

*nResID*<br/>
진행 리소스 ID입니다.

*bRegister*<br/>
진행 리소스 스크립트를 등록 해야 하는지 여부를 나타냅니다.

*pMapEntries*<br/>
진행 스크립트의 대체 가능 매개 변수와 연결 된 값을 저장 하는 대체 맵에 대 한 포인터입니다. ATL은 자동으로 `%MODULE%` 을 사용 합니다. 대체 가능한 추가 매개 변수를 사용 하려면 자세한 내용은 설명 부분을 참조 하십시오. 그렇지 않으면 NULL 기본값을 사용 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

[UpdateRegistryFromResourceD](#updateregistryfromresourced)와 유사하게 `UpdateRegistryFromResourceS`를 제외한 ATL 레지스트리 구성 요소 (등록자)에 대한 정적 링크를 만듭니다.

`UpdateRegistryFromResourceS` 개체 맵이 처리 될 때 자동으로 호출 됩니다 `#define _ATL_STATIC_REGISTRY` *.* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에 추가 합니다.

> [!NOTE]
> 런타임에 대체 값을 대체 하려면 [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) 또는 [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) 매크로를 지정 하지 마십시오. 대신, 구조체의 배열을 만듭니다 `_ATL_REGMAP_ENTRIES` . 여기에서 각 항목에는 런타임에 자리 표시자를 대체 하기 위한 값과 쌍을 이루는 변수 자리 표시 자가 포함 됩니다. 그런 다음 `UpdateRegistryFromResourceS` 를 호출 하 여 *Pmapentries* 매개 변수에 대 한 배열을 전달 합니다. 이렇게 하면 구조의 모든 대체 값이 `_ATL_REGMAP_ENTRIES` 등록자의 대체 맵에 추가 됩니다.

대체 가능한 매개 변수 및 스크립팅에 대 한 자세한 내용은 [ATL 레지스트리 구성 요소 (등록자)](../../atl/atl-registry-component-registrar.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

---
description: '자세히 알아보기: CAtlDllModuleT 클래스'
title: CAtlDllModuleT 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: b6b6f87fc77187b150824fcd67fae254eb6d8f57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147435"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 클래스

이 클래스는 DLL에 대 한 모듈을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CAtlDllModuleT` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlDllModuleT:: CAtlDllModuleT](#catldllmodulet)|생성자입니다.|
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlDllModuleT::D llCanUnloadNow](#dllcanunloadnow)|DLL이 언로드될 수 있는지 테스트 합니다.|
|[CAtlDllModuleT::D llGetClassObject](#dllgetclassobject)|클래스 팩터리를 반환 합니다.|
|[CAtlDllModuleT::D llMain](#dllmain)|DLL (동적 연결 라이브러리)에 대 한 선택적 진입점입니다.|
|[CAtlDllModuleT::D llRegisterServer](#dllregisterserver)|DLL의 개체에 대 한 시스템 레지스트리에 항목을 추가 합니다.|
|[CAtlDllModuleT::D llUnregisterServer](#dllunregisterserver)|DLL의 개체에 대 한 시스템 레지스트리에서 항목을 제거 합니다.|
|[CAtlDllModuleT:: GetClassObject](#getclassobject)|클래스 팩터리를 반환 합니다. [DllGetClassObject](#dllgetclassobject)에 의해 호출 됩니다.|

## <a name="remarks"></a>설명

`CAtlDllModuleT` DLL (동적 연결 라이브러리)의 모듈을 나타내며 모든 DLL 프로젝트에서 사용 하는 함수를 제공 합니다. 이러한 기능을 지 원하는 [이 클래스의 특수화에는 등록](../../atl/reference/catlmodulet-class.md) 지원이 포함 됩니다.

ATL의 모듈에 대 한 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a> CAtlDllModuleT:: CAtlDllModuleT

생성자입니다.

```cpp
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a> CAtlDllModuleT:: ~ CAtlDllModuleT

소멸자입니다.

```cpp
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a> CAtlDllModuleT::D llCanUnloadNow

DLL이 언로드될 수 있는지 테스트 합니다.

```cpp
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>반환 값

DLL이 언로드될 수 있으면 S_OK을 반환 하 고, 그렇지 않으면 S_FALSE을 반환 합니다.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a> CAtlDllModuleT::D llGetClassObject

클래스 팩터리를 반환 합니다.

```cpp
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>매개 변수

*rclsid*<br/>
만들 개체의 CLSID입니다.

*riid*<br/>
요청 된 인터페이스의 IID입니다.

*ppv*<br/>
*Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않는 경우 *ppv* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a> CAtlDllModuleT::D llMain

DLL (동적 연결 라이브러리)에 대 한 선택적 진입점입니다.

```cpp
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>매개 변수

*dwReason*<br/>
DLL_PROCESS_ATTACH로 설정 된 경우 DLL_THREAD_ATTACH 및 DLL_THREAD_DETACH 알림 호출이 사용 하지 않도록 설정 됩니다.

*lpReserved*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

DLL_THREAD_ATTACH 및 DLL_THREAD_DETACH 알림 호출을 사용 하지 않도록 설정 하면 많은 Dll이 있는 다중 스레드 응용 프로그램에 대 한 유용한 최적화를 사용할 수 있습니다.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a> CAtlDllModuleT::D llRegisterServer

DLL의 개체에 대 한 시스템 레지스트리에 항목을 추가 합니다.

```cpp
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>매개 변수

*bRegTypeLib*<br/>
형식 라이브러리를 등록 하려면 TRUE입니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a> CAtlDllModuleT::D llUnregisterServer

DLL의 개체에 대 한 시스템 레지스트리에서 항목을 제거 합니다.

```cpp
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>매개 변수

*bUnRegTypeLib*<br/>
레지스트리에서 형식 라이브러리를 제거 하려면 TRUE입니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a> CAtlDllModuleT:: GetClassObject

지정 된 CLSID의 개체를 만듭니다.

```cpp
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>매개 변수

*rclsid*<br/>
만들 개체의 CLSID입니다.

*riid*<br/>
요청 된 인터페이스의 IID입니다.

*ppv*<br/>
*Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않는 경우 *ppv* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [CAtlDllModuleT::D llgetclassobject](#dllgetclassobject) 에 의해 호출 되며 이전 버전과의 호환성을 위해 포함 되었습니다.

## <a name="see-also"></a>참고 항목

[CAtlModuleT 클래스](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT 클래스](../../atl/reference/catlexemodulet-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

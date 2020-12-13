---
description: '자세한 정보: CAtlModuleT 클래스'
title: CAtlModuleT 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: 841d4a41b7df818d9e966af1050fd9e376d89447
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147227"
---
# <a name="catlmodulet-class"></a>CAtlModuleT 클래스

이 클래스는 ATL 모듈을 구현 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CAtlModuleT` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlModuleT:: CAtlModuleT](#catlmodulet)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlModuleT:: InitLibId](#initlibid)|현재 모듈의 GUID를 포함 하는 데이터 멤버를 초기화 합니다.|
|[CAtlModuleT:: RegisterAppId](#registerappid)|레지스트리에 EXE를 추가 합니다.|
|[CAtlModuleT:: RegisterServer](#registerserver)|레지스트리에 서비스를 추가 합니다.|
|[CAtlModuleT:: UnregisterAppId](#unregisterappid)|레지스트리에서 EXE를 제거 합니다.|
|[CAtlModuleT:: UnregisterServer](#unregisterserver)|레지스트리에서 서비스를 제거 합니다.|
|[CAtlModuleT:: UpdateRegistryAppId](#updateregistryappid)|레지스트리의 EXE 정보를 업데이트 합니다.|

## <a name="remarks"></a>설명

`CAtlModuleT`은 (는) [Catlmodule](../../atl/reference/catlmodule-class.md)에서 파생 되 고 실행 파일 (exe) 또는 서비스 (EXE) ATL 모듈을 구현 합니다. 실행 가능한 모듈은 로컬에서 실행 되는 서버 이며, 서비스 모듈은 Windows를 시작할 때 백그라운드에서 실행 되는 Windows 응용 프로그램입니다.

`CAtlModuleT` 모듈의 초기화, 등록 및 등록 취소를 지원 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a> CAtlModuleT:: CAtlModuleT

생성자입니다.

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>설명

는 [Catlmodulet:: InitLibId](#initlibid)를 호출 합니다.

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a> CAtlModuleT:: InitLibId

현재 모듈의 GUID를 포함 하는 데이터 멤버를 초기화 합니다.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>설명

[Catlmodulet:: catlmodulet](#catlmodulet)생성자에서 호출 됩니다.

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a> CAtlModuleT:: RegisterAppId

레지스트리에 EXE를 추가 합니다.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a> CAtlModuleT:: RegisterServer

레지스트리에 서비스를 추가 합니다.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*bRegTypeLib*<br/>
형식 라이브러리를 등록 하려면 TRUE입니다. 기본값은 FALSE입니다.

*pCLSID*<br/>
등록할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a> CAtlModuleT:: UnregisterAppId

레지스트리에서 EXE를 제거 합니다.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a> CAtlModuleT:: UnregisterServer

레지스트리에서 서비스를 제거 합니다.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*bUnRegTypeLib*<br/>
형식 라이브러리도 등록 취소 되 면 TRUE입니다.

*pCLSID*<br/>
등록을 취소할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 취소 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a> CAtlModuleT:: UpdateRegistryAppId

레지스트리의 EXE 정보를 업데이트 합니다.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>매개 변수

*bRegister*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CAtlModule 클래스](../../atl/reference/catlmodule-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

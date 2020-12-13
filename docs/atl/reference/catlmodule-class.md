---
description: '자세한 정보: CAtlModule 클래스'
title: CAtlModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 3ae2caa59f330f9f43a3ae66e7f5eb38ddabc89c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147240"
---
# <a name="catlmodule-class"></a>CAtlModule 클래스

이 클래스는 여러 ATL 모듈 클래스에서 사용 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlModule:: Cllmodule](#catlmodule)|생성자입니다.|
|[CAtlModule:: ~ CAtlModule](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements)|ATL 레지스트리 구성 요소 (등록자) 대체 맵에 매개 변수를 추가 하려면이 메서드를 재정의 합니다.|
|[CAtlModule:: AddTermFunc](#addtermfunc)|모듈이 종료 될 때 호출할 새 함수를 추가 합니다.|
|[CAtlModule:: GetGITPtr](#getgitptr)|전역 인터페이스 포인터를 반환 합니다.|
|[CAtlModule:: GetLockCount](#getlockcount)|잠금 수를 반환 합니다.|
|[CAtlModule:: Lock](#lock)|잠금 수를 늘립니다.|
|[CAtlModule:: Term](#term)|모든 데이터 멤버를 해제 합니다.|
|[CAtlModule:: Unlock](#unlock)|잠금 횟수를 줄입니다.|
|[CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced)|지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다.|
|[CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|이 메서드는에서 `UpdateRegistryFromResourceD` 레지스트리 업데이트를 수행 하기 위해 호출 합니다.|
|[CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources)|지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다. 이 메서드는 ATL 레지스트리 구성 요소에 정적으로 연결 됩니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlModule:: m_libid](#m_libid)|현재 모듈의 GUID를 포함 합니다.|
|[CAtlModule:: m_pGIT](#m_pgit)|전역 인터페이스 테이블에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

이 클래스는 [CAtlDllModuleT 클래스](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT 클래스](../../atl/reference/catlexemodulet-class.md)및 [CAtlServiceModuleT 클래스](../../atl/reference/catlservicemodulet-class.md) 에서 각각 DLL 응용 프로그램, EXE 응용 프로그램 및 Windows 서비스에 대 한 지원을 제공 하는 데 사용 됩니다.

ATL의 모듈에 대 한 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md)를 참조 하세요.

이 클래스는 이전 버전의 ATL에서 사용 되는 사용 되지 않는 [CComModule 클래스](../../atl/reference/ccommodule-class.md) 를 대체 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a> CAtlModule:: AddCommonRGSReplacements

ATL 레지스트리 구성 요소 (등록자) 대체 맵에 매개 변수를 추가 하려면이 메서드를 재정의 합니다.

```cpp
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>매개 변수

*pRegistrar*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

대체 가능 매개 변수를 사용 하 여 등록자의 클라이언트는 런타임 데이터를 지정할 수 있습니다. 이를 위해 등록자는 스크립트의 대체 가능 매개 변수와 연결 된 값이 입력 되는 대체 맵을 유지 관리 합니다. 등록자는 런타임에 이러한 항목을 만듭니다.

자세한 내용은 [대체 가능한 매개 변수 (등록자의 전처리기) 사용](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 항목을 참조 하세요.

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a> CAtlModule:: AddTermFunc

모듈이 종료 될 때 호출할 새 함수를 추가 합니다.

```cpp
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>매개 변수

*pFunc*<br/>
추가할 함수에 대 한 포인터입니다.

*dw*<br/>
함수에 전달 되는 사용자 정의 데이터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a> CAtlModule:: Cllmodule

생성자입니다.

```cpp
CAtlModule() throw();
```

### <a name="remarks"></a>설명

데이터 멤버를 초기화 하 고 모듈의 스레드를 중심으로 임계 영역을 시작 합니다.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a> CAtlModule:: ~ CAtlModule

소멸자입니다.

```cpp
~CAtlModule() throw();
```

### <a name="remarks"></a>설명

모든 데이터 멤버를 해제 합니다.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a> CAtlModule:: GetGITPtr

전역 인터페이스 테이블에 대 한 포인터를 검색 합니다.

```cpp
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>매개 변수

*ppGIT*<br/>
전역 인터페이스 테이블에 대 한 포인터를 수신 하는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나 오류 발생 시 오류 코드를 반환 합니다. *Ppgit* 가 NULL과 같은 경우 E_POINTER 반환 됩니다.

### <a name="remarks"></a>설명

전역 인터페이스 테이블 개체가 없으면 생성 되 고 해당 주소는 [Catlmodule:: m_pGIT](#m_pgit)멤버 변수에 저장 됩니다.

디버그 빌드에서는 *Ppgit* 가 NULL 이면 어설션 오류가 발생 하 고, 전역 인터페이스 테이블 포인터를 가져올 수 없는 경우에는 어설션 오류가 발생 합니다.

전역 인터페이스 테이블에 대 한 자세한 내용은 [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) 를 참조 하세요.

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a> CAtlModule:: GetLockCount

잠금 수를 반환 합니다.

```cpp
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>반환 값

잠금 수를 반환 합니다. 이 값은 진단 및 디버깅에 유용할 수 있습니다.

## <a name="catlmodulelock"></a><a name="lock"></a> CAtlModule:: Lock

잠금 수를 늘립니다.

```cpp
virtual LONG Lock() throw();
```

### <a name="return-value"></a>반환 값

잠금 수를 늘리고 업데이트 된 값을 반환 합니다. 이 값은 진단 및 디버깅에 유용할 수 있습니다.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a> CAtlModule:: m_libid

현재 모듈의 GUID를 포함 합니다.

```cpp
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a> CAtlModule:: m_pGIT

전역 인터페이스 테이블에 대 한 포인터입니다.

```cpp
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a> CAtlModule:: Term

모든 데이터 멤버를 해제 합니다.

```cpp
void Term() throw();
```

### <a name="remarks"></a>설명

모든 데이터 멤버를 해제 합니다. 이 메서드는 소멸자에서 호출 됩니다.

## <a name="catlmoduleunlock"></a><a name="unlock"></a> CAtlModule:: Unlock

잠금 횟수를 줄입니다.

```cpp
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>반환 값

잠금 횟수를 감소 시키고 업데이트 된 값을 반환 합니다. 이 값은 진단 및 디버깅에 유용할 수 있습니다.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a> CAtlModule:: UpdateRegistryFromResourceD

지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*lpszRes*<br/>
리소스 이름입니다.

*nResID*<br/>
리소스 ID입니다.

*bRegister*<br/>
개체를 등록 해야 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*pMapEntries*<br/>
스크립트의 대체 가능 매개 변수와 연결 된 값을 저장 하는 대체 맵에 대 한 포인터입니다. ATL은 자동 으로% MODULE%를 사용 합니다. 대체 가능한 추가 매개 변수를 사용 하려면 [Catlmodule:: AddCommonRGSReplacements](#addcommonrgsreplacements)를 참조 하세요. 그렇지 않으면 NULL 기본값을 사용 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

*LpszRes 또는 nResID* 에 지정 된 리소스에 포함 된 스크립트를 실행 합니다. *BRegister* 가 TRUE 이면이 메서드는 시스템 레지스트리에 개체를 등록 합니다. 그렇지 않으면 레지스트리에서 개체를 제거 합니다.

ATL 레지스트리 구성 요소 (등록자)에 정적으로 연결 하려면 [Catlmodule:: UpdateRegistryFromResourceS](#updateregistryfromresources)를 참조 하세요.

이 메서드는 [Catlmodule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) 및 [Iregistrar:: resourceunregister 취소](iregistrar-class.md#resourceunregister)를 호출 합니다.

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a> CAtlModule:: UpdateRegistryFromResourceDHelper

이 메서드는에서 `UpdateRegistryFromResourceD` 레지스트리 업데이트를 수행 하기 위해 호출 합니다.

```cpp
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*lpszRes*<br/>
리소스 이름입니다.

*bRegister*<br/>
개체를 등록 해야 하는지 여부를 나타냅니다.

*pMapEntries*<br/>
스크립트의 대체 가능 매개 변수와 연결 된 값을 저장 하는 대체 맵에 대 한 포인터입니다. ATL은 자동 으로% MODULE%를 사용 합니다. 대체 가능한 추가 매개 변수를 사용 하려면 [Catlmodule:: AddCommonRGSReplacements](#addcommonrgsreplacements)를 참조 하세요. 그렇지 않으면 NULL 기본값을 사용 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [UpdateRegistryFromResourceD](#updateregistryfromresourced)의 구현을 제공 합니다.

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a> CAtlModule:: UpdateRegistryFromResourceS

지정 된 리소스에 포함 된 스크립트를 실행 하 여 개체를 등록 하거나 등록 취소 합니다. 이 메서드는 ATL 레지스트리 구성 요소에 정적으로 연결 됩니다.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*nResID*<br/>
리소스 ID입니다.

*lpszRes*<br/>
리소스 이름입니다.

*bRegister*<br/>
리소스 스크립트를 등록 해야 하는지 여부를 나타냅니다.

*pMapEntries*<br/>
스크립트의 대체 가능 매개 변수와 연결 된 값을 저장 하는 대체 맵에 대 한 포인터입니다. ATL은 자동 으로% MODULE%를 사용 합니다. 대체 가능한 추가 매개 변수를 사용 하려면 [Catlmodule:: AddCommonRGSReplacements](#addcommonrgsreplacements)를 참조 하세요. 그렇지 않으면 NULL 기본값을 사용 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

UpdateRegistryFromResourceD를 제외 하 고는 [Catlmodule::](#updateregistryfromresourced) 와 마찬가지로 `CAtlModule::UpdateRegistryFromResourceS` ATL 레지스트리 구성 요소 (등록자)에 대 한 정적 링크를 만듭니다.

## <a name="see-also"></a>참고 항목

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)<br/>
[레지스트리 구성 요소(등록자)](../../atl/atl-registry-component-registrar.md)

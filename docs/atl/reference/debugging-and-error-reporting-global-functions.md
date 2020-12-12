---
description: '자세한 정보: 디버깅 및 오류 보고 전역 함수'
title: 디버깅 및 오류 보고 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: 3c729a7d8e870ce7b104ca53cd83bf8c41112dea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139986"
---
# <a name="debugging-and-error-reporting-global-functions"></a>디버깅 및 오류 보고 전역 함수

이러한 함수는 유용한 디버깅 및 추적 기능을 제공 합니다.

|Name|설명|
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|`GetLastError`HRESULT 형식의 오류 코드를 반환 합니다.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Win32 오류 코드 HRESULT로 변환합니다.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|`IErrorInfo`클라이언트에 오류 정보를 제공 하도록를 설정 합니다.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|`CAtlException`를 throw합니다.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Windows 함수 `GetLastError`의 결과에 따라 오류를 표시하려면 이 함수를 호출합니다.|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a> AtlHresultFromLastError

호출 스레드의 마지막 오류 코드 값을 HRESULT 형식으로 반환합니다.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>설명

`AtlHresultFromLastError``GetLastError`는를 호출 하 여 마지막 오류를 가져온 다음 HRESULT_FROM_WIN32 매크로를 사용 하 여 HRESULT로 변환한 후 오류를 반환 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** comcli .h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a> AtlHresultFromWin32

Win32 오류 코드 HRESULT로 변환합니다.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>매개 변수

*error*<br/>
변환할 오류 값입니다.

### <a name="remarks"></a>설명

HRESULT_FROM_WIN32 매크로를 사용 하 여 Win32 오류 코드를 HRESULT로 변환 합니다.

> [!NOTE]
> 를 사용 하는 대신 `HRESULT_FROM_WIN32(GetLastError())` [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)함수를 사용 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** comcli .h

## <a name="atlreporterror"></a><a name="atlreporterror"></a> AtlReportError

인터페이스를 설정 `IErrorInfo` 하 여 개체의 클라이언트에 오류 정보를 제공 합니다.

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 오류를 보고 하는 개체의 CLSID입니다.

*lpszDesc*<br/>
진행 오류를 설명 하는 문자열입니다. 유니코드 버전은 *lpszDesc* 이 LPCOLESTR 형식이 되도록 지정 합니다. ANSI 버전은 LPCSTR의 유형을 지정 합니다.

*iid*<br/>
진행 오류를 정의 하는 인터페이스의 IID 이거나, 오류가 운영 체제에서 정의 되는 경우 GUID_NULL입니다.

*hRes*<br/>
진행 호출자에 게 반환할 HRESULT입니다.

*nID*<br/>
진행 오류 설명 문자열이 저장 되는 리소스 식별자입니다. 이 값은 0x0200과 0xFFFF 사이에 있어야 합니다. 디버그 빌드에서 *nID* 가 유효한 문자열을 인덱싱하지 않으면 **어설션이** 발생 합니다. 릴리스 빌드에서 오류 설명 문자열은 "알 수 없는 오류"로 설정 됩니다.

*dwHelpID*<br/>
진행 오류에 대 한 도움말 컨텍스트 식별자입니다.

*lpszHelpFile*<br/>
진행 오류를 설명 하는 도움말 파일의 경로 및 이름입니다.

*hInst*<br/>
진행 리소스에 대 한 핸들입니다. 기본적으로이 매개 변수는 이며 `__AtlBaseModuleModule::GetResourceInstance` , 여기서 `__AtlBaseModuleModule` 는 [Catlbasemodule](../../atl/reference/catlbasemodule-class.md) 의 전역 인스턴스이거나 여기에서 파생 된 클래스입니다.

### <a name="return-value"></a>반환 값

*Hres* 매개 변수가 0이 아니면 *hres* 의 값을 반환 합니다. *Hres* 가 0 이면 처음 4 개 버전의가 `AtlReportError` DISP_E_EXCEPTION 반환 됩니다. 마지막 두 버전은 매크로 **MAKE_HRESULT (1, FACILITY_ITF,** )의 결과를 반환 합니다 `nID` .

### <a name="remarks"></a>설명

*LpszDesc* 문자열은 오류에 대 한 텍스트 설명으로 사용 됩니다. 클라이언트는에서 반환 하는 *Hres* 를 받을 때 `AtlReportError` `IErrorInfo` 오류에 대 한 세부 정보를 위해 구조에 액세스할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> `AtlReportError`C + + catch 처리기에서를 사용 하지 마세요. 이러한 함수의 일부 재정의는 내부적으로 함수를 내부적으로 사용 하는 ATL 문자열 변환 매크로를 사용 합니다 `_alloca` . `AtlReportError`C + + catch 처리기에서를 사용 하면 c + + catch 처리기에서 예외가 발생할 수 있습니다.

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atlthrow"></a><a name="atlthrow"></a> AtlThrow

HRESULT 상태 코드를 기반으로 오류를 알리려면이 함수를 호출 합니다.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>매개 변수

*시간*<br/>
표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 오류 조건이 발생 하는 경우 ATL 및 MFC 코드에서 사용 됩니다. 사용자의 코드에서 호출할 수도 있습니다. 이 함수의 기본 구현은 프로젝트, MFC 또는 ATL의 형식 _ATL_NO_EXCEPTIONS 기호 정의에 따라 달라 집니다.

이 함수는 모든 경우에 HRESULT를 디버거에 추적 합니다.

Visual Studio 2015 업데이트 3 이상에서이 함수는 의사 SAL 경고를 방지 하기 위해 __declspec (noreturn) 특성을 사용 합니다.

_ATL_NO_EXCEPTIONS MFC 프로젝트에 정의 되어 있지 않은 경우이 함수는 HRESULT의 값을 기반으로 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md) 을 throw 합니다.

_ATL_NO_EXCEPTIONS이 ATL 프로젝트에 정의 되어 있지 않은 경우 함수는 오류를 [발생](../../atl/reference/catlexception-class.md)시킵니다.

_ATL_NO_EXCEPTIONS 정의 된 경우 함수는 예외를 throw 하는 대신 어설션 오류를 발생 시킵니다.

ATL 프로젝트의 경우 오류가 발생 하는 경우 ATL에서 사용할이 함수의 고유한 구현을 제공할 수 있습니다. 이렇게 하려면와 동일한 시그니처를 사용 하 여 함수를 정의 하 `AtlThrow` 고 `AtlThrow` 함수 이름으로 #define 합니다. 이는 .h를 제외 하 고 (예를 들어, ATL 헤더를 포함 하기 전에이 작업을 수행 해야 함을 의미 합니다. `__declspec(noreturn)`의사 SAL 경고를 방지 하기 위해 함수에 특성을 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a> AtlThrowLastWin32

Windows 함수 `GetLastError`의 결과에 따라 오류를 표시하려면 이 함수를 호출합니다.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>설명

이 함수는의 결과를 `GetLastError` 디버거로 추적 합니다.

_ATL_NO_EXCEPTIONS MFC 프로젝트에 정의 되어 있지 않은 경우이 함수는에서 반환 된 값에 따라 [Cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 또는 [coleexception](../../mfc/reference/coleexception-class.md) 을 throw `GetLastError` 합니다.

_ATL_NO_EXCEPTIONS이 ATL 프로젝트에 정의 되어 있지 않은 경우 함수는 오류를 [발생](../../atl/reference/catlexception-class.md)시킵니다.

_ATL_NO_EXCEPTIONS 정의 된 경우 함수는 예외를 throw 하는 대신 어설션 오류를 발생 시킵니다.

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)<br/>
[디버깅 및 오류 보고 매크로](../../atl/reference/debugging-and-error-reporting-macros.md)

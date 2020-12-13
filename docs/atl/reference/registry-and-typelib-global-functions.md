---
description: '자세한 정보: 레지스트리 및 TypeLib 전역 함수'
title: 레지스트리 및 TypeLib 전역 함수
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: d7420dbbb472f1fc8b01329e9ded4c887e2bd71d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138889"
---
# <a name="registry-and-typelib-global-functions"></a>레지스트리 및 TypeLib 전역 함수

이러한 함수는 형식 라이브러리를 로드 및 등록 하는 기능을 제공 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|지정 된 레지스트리 키를 만듭니다.|
|[AfxRegDeleteKey](#afxregdeletekey)|지정 된 레지스트리 키를 삭제 합니다.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|미리 보기 처리기를 등록 하는 도우미입니다.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 미리 보기 처리기의 등록을 취소 하는 도우미입니다. |
|[AtlRegisterTypeLib](#atlregistertypelib)|이 함수는 형식 라이브러리를 등록하기 위해 호출됩니다.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|이 함수는 형식 라이브러리를 등록 취소 하기 위해 호출 됩니다.|
|[AfxRegOpenKey](#afxregopenkey)|지정 된 레지스트리 키를 엽니다.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|지정 된 레지스트리 키를 엽니다.|
|[AtlLoadTypeLib](#atlloadtypelib)|이 함수는 형식 라이브러리를 로드하기 위해 호출됩니다.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|이 함수는 제공된 리소스에서 레지스트리를 업데이트하기 위해 호출됩니다.|
|[RegistryDataExchange](#registrydataexchange)|이 함수는 시스템 레지스트리에서 읽거나 쓰기 위해 호출됩니다. [레지스트리 데이터 교환 매크로](../../atl/reference/registry-data-exchange-macros.md)에 의해 호출 됩니다.|

이러한 함수는 프로그램에서 정보를 저장 하는 데 사용 하는 레지스트리의 노드를 제어 합니다.

|Name|설명|
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|응용 프로그램이 레지스트리 액세스를 **HKEY_CURRENT_USER** ( **HKCU**) 노드로 리디렉션하는 지 여부를 검색 합니다.|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|응용 프로그램이 레지스트리 액세스를 **HKEY_CURRENT_USER** ( **HKCU**) 노드로 리디렉션하는 지 여부를 설정 합니다.|

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

이 함수를 사용 하 여 응용 프로그램이 레지스트리 액세스를 **HKEY_CURRENT_USER** (**HKCU**) 노드로 리디렉션하는 지 여부를 확인 합니다.

### <a name="syntax"></a>구문

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>매개 변수

*pEnabled*<br/>
제한이 TRUE는 레지스트리 정보가 **HKCU** 노드에 전달 됨을 나타냅니다. FALSE는 응용 프로그램이 레지스트리 정보를 기본 노드에 쓰도록 지정 합니다. 기본 노드는 **HKEY_CLASSES_ROOT** (**HKCR**)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 오류가 발생 하면 HRESULT 오류 코드를 S_OK 합니다.

### <a name="remarks"></a>설명

레지스트리 리디렉션은 기본적으로 사용 되지 않습니다. 이 옵션을 사용 하도록 설정 하면 레지스트리 액세스가 **HKEY_CURRENT_USER\Software\Classes** 으로 리디렉션됩니다.

리디렉션이 전역이 아닙니다. 이 레지스트리 리디렉션의 MFC 및 ATL 프레임 워크도 영향을 받습니다.

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a> AfxRegCreateKey

지정 된 레지스트리 키를 만듭니다.

### <a name="syntax"></a>구문

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
이 함수가 열거나 만드는 키의 이름입니다.

*phkResult*<br/>
열리거나 만든 키에 대 한 핸들을 받는 변수에 대 한 포인터입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a> AfxRegDeleteKey

지정 된 레지스트리 키를 삭제 합니다.

### <a name="syntax"></a>구문

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
삭제할 키의 이름입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

미리 보기 처리기를 등록 하는 도우미입니다.

### <a name="syntax"></a>구문

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>매개 변수

*lpszCLSID*<br/>
처리기의 CLSID를 지정 합니다.

*lpszShortTypeName*<br/>
처리기의 ProgID를 지정 합니다.

*lpszFilterExt*<br/>
이 처리기에 등록 된 파일 확장명을 지정 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a> 서 용 Registertypelib

이 함수는 형식 라이브러리를 등록하기 위해 호출됩니다.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>매개 변수

*Hin Typelib*<br/>
모듈 인스턴스에 대 한 핸들입니다.

*lpszIndex*<br/>
"\N" 형식의 문자열입니다 \\ . 여기서 N은 형식 라이브러리 리소스의 정수 인덱스입니다. 인덱스가 필요 하지 않은 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) 및 [Catlcommodule:: registertypelib](../../atl/reference/catlcommodule-class.md#registertypelib)에서 활용 됩니다.

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a> AfxRegOpenKey

지정 된 레지스트리 키를 엽니다.

### <a name="syntax"></a>구문

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
이 함수가 열거나 만드는 키의 이름입니다.

*phkResult*<br/>
만든 키에 대 한 핸들을 받는 변수에 대 한 포인터입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a> AfxRegOpenKeyEx

지정 된 레지스트리 키를 엽니다.

### <a name="syntax"></a>구문

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
이 함수가 열거나 만드는 키의 이름입니다.

*ulOptions*<br/>
이 매개 변수는 예약 되어 있으며 0 이어야 합니다.

*samDesired*<br/>
키에 대 한 원하는 액세스 권한을 지정 하는 마스크입니다.

*phkResult*<br/>
열린 키에 대 한 핸들을 받는 변수에 대 한 포인터입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

미리 보기 처리기의 등록을 취소 하는 도우미입니다.

### <a name="syntax"></a>구문

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>매개 변수

*lpszCLSID*<br/>
등록을 취소할 처리기의 CLSID를 지정 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

응용 프로그램이 레지스트리 액세스를 **HKEY_CURRENT_USER** (**HKCU**) 노드로 리디렉션하는 지 여부를 설정 합니다.

### <a name="syntax"></a>구문

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 TRUE는 레지스트리 정보가 **HKCU** 노드에 전달 됨을 나타냅니다. FALSE는 응용 프로그램이 레지스트리 정보를 기본 노드에 쓰도록 지정 합니다. 기본 노드는 **HKEY_CLASSES_ROOT** (**HKCR**)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면이 고, 그렇지 않으면 오류가 발생 하면 HRESULT 오류 코드를 S_OK 합니다.

### <a name="remarks"></a>설명

레지스트리 리디렉션은 기본적으로 사용 되지 않습니다. 이 옵션을 사용 하도록 설정 하면 레지스트리 액세스가 **HKEY_CURRENT_USER\Software\Classes** 으로 리디렉션됩니다.

리디렉션이 전역이 아닙니다. 이 레지스트리 리디렉션의 MFC 및 ATL 프레임 워크도 영향을 받습니다.

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a> AtlUnRegisterTypeLib

이 함수는 형식 라이브러리를 등록 취소하기 위해 호출됩니다.

### <a name="syntax"></a>구문

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>매개 변수

*Hin Typelib*<br/>
모듈 인스턴스에 대 한 핸들입니다.

*lpszIndex*<br/>
"\N" 형식의 문자열입니다 \\ . 여기서 N은 형식 라이브러리 리소스의 정수 인덱스입니다. 인덱스가 필요 하지 않은 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 [Catlcommodule:: UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) 및 [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)에서 활용 됩니다.

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a> 없음 Loadtypelib

이 함수는 형식 라이브러리를 로드하기 위해 호출됩니다.

### <a name="syntax"></a>구문

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>매개 변수

*Hin Typelib*<br/>
형식 라이브러리와 연결 된 모듈에 대 한 핸들입니다.

*lpszIndex*<br/>
"\N" 형식의 문자열입니다 \\ . 여기서 N은 형식 라이브러리 리소스의 정수 인덱스입니다. 인덱스가 필요 하지 않은 경우 NULL 일 수 있습니다.

*pbstrPath*<br/>
반환이 성공적 이면 형식 라이브러리와 연결 된 모듈의 전체 경로를 포함 합니다.

*ppTypeLib*<br/>
반환이 성공적 이면, 로드 된 형식 라이브러리에 대 한 포인터에 대 한 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 AtlUnRegisterTypeLib [Registertypelib](#atlregistertypelib) 및 [](#atlunregistertypelib)에서 활용 됩니다.

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a> AtlUpdateRegistryFromResourceD

이 함수는 Visual Studio 2013에서 사용이 중단되었으며, Visual Studio 2015에서 제거되었습니다.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a> RegistryDataExchange

이 함수는 시스템 레지스트리에서 읽거나 쓰기 위해 호출됩니다.

### <a name="syntax"></a>구문

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
현재 개체에 대 한 포인터입니다.

*rdxOp*<br/>
함수에서 수행 해야 하는 작업을 나타내는 열거형 값입니다. 허용 되는 값은 설명 섹션의 표를 참조 하세요.

*pItem*<br/>
레지스트리에서 읽거나 쓸 데이터에 대 한 포인터입니다. 데이터는 레지스트리에서 삭제할 키를 나타낼 수도 있습니다. 기본값은 NULL입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

매크로 [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) 및 [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) 를 호출 하는 함수로 확장 합니다 `RegistryDataExchange` .

함수에서 수행 해야 하는 작업을 나타내는 열거형 값은 다음 표에 나와 있습니다.

|열거형 값|연산|
|----------------|---------------|
|eReadFromReg|레지스트리에서 데이터를 읽습니다.|
|eWriteToReg|레지스트리에 데이터를 씁니다.|
|eDeleteFromReg|레지스트리에서 키를 삭제 합니다.|

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참조

[함수](atl-functions.md)<br/>
[레지스트리 데이터 교환 매크로](registry-data-exchange-macros.md)

---
description: '자세한 정보: 서버 등록 전역 함수'
title: 서버 등록 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: 7841c162c2c7c0c93cd8edcd8fd6d78ae4bb2b1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157739"
---
# <a name="server-registration-global-functions"></a>서버 등록 전역 함수

이러한 함수는 개체 맵의 서버 개체 등록 및 등록 취소를 지원 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|이 함수는 개체 맵의 모든 개체를 등록하기 위해 호출됩니다.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|이 함수는 개체 맵의 모든 개체를 등록 취소하기 위해 호출됩니다.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|이 함수는 클래스 개체를 등록하기 위해 호출됩니다.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|이 함수는 COM 모듈에서 클래스 개체를 취소 하기 위해 호출 됩니다.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|이 함수는 클래스 개체를 가져오기 위해 호출 됩니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a> AtlComModuleRegisterServer

이 함수는 개체 맵의 모든 개체를 등록하기 위해 호출됩니다.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>매개 변수

*pComModule*<br/>
COM 모듈에 대 한 포인터입니다.

*bRegTypeLib*<br/>
형식 라이브러리를 등록 하려면 TRUE입니다.

*pCLSID*<br/>
등록할 개체의 CLSID를 가리킵니다. NULL 인 경우 개체 맵의 모든 개체를 등록 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`AtlComModuleRegisterServer` ATL에서 자동 생성 된 개체 맵을 살펴보고 맵의 각 개체를 등록 합니다. *Pclsid* 가 NULL이 아닌 경우 *pclsid* 가 참조 하는 개체만 등록 됩니다. 그렇지 않으면 모든 개체가 등록 됩니다.

이 함수는 지 수 [Lcommodule:: RegisterServer](catlcommodule-class.md#registerserver)에서 호출 됩니다.

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a> AtlComModuleUnregisterServer

이 함수는 개체 맵의 모든 개체를 등록 취소하기 위해 호출됩니다.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>매개 변수

*pComModule*<br/>
COM 모듈에 대 한 포인터입니다.

*bUnRegTypeLib*<br/>
형식 라이브러리를 등록 하려면 TRUE입니다.

*pCLSID*<br/>
등록을 취소할 개체의 CLSID를 가리킵니다. NULL 인 경우 개체 맵의 모든 개체를 등록 취소 합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`AtlComModuleUnregisterServer` ATL 개체 맵을 탐색 하 고 맵에서 각 개체의 등록을 취소 합니다. *Pclsid* 가 NULL이 아닌 경우 *pclsid* 가 참조 하는 개체만 등록 취소 됩니다. 그렇지 않으면 모든 개체의 등록이 취소 됩니다.

이 함수는 지 수 [Lcommodule:: UnregisterServer](catlcommodule-class.md#unregisterserver)에서 호출 됩니다.

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a> AtlComModuleRegisterClassObjects

이 함수는 클래스 개체를 등록하기 위해 호출됩니다.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>매개 변수

*pComModule*<br/>
COM 모듈에 대 한 포인터입니다.

*dwClsContext*<br/>
클래스 개체가 실행 될 컨텍스트를 지정 합니다. 가능한 값은 CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER 또는 CLSCTX_LOCAL_SERVER입니다. 자세한 내용은 [Clsctx](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 를 참조 하세요.

*dwFlags*<br/>
클래스 개체에 대 한 연결 유형을 결정 합니다. 가능한 값은 REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE 또는 REGCLS_MULTI_SEPARATE입니다. 자세한 내용은 [Regcls](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 [CComModule:: registerclassobjects](ccommodule-class.md#registerclassobjects) (ATL 7.0에서 사용 되지 않음) 및 [CAtlExeModuleT:: registerclassobjects](catlexemodulet-class.md#registerclassobjects)에서 활용 됩니다.

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a> AtlComModuleRevokeClassObjects

이 함수는 실행 개체 테이블에서 클래스 팩터리를 제거하기 위해 호출됩니다.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>매개 변수

*pComModule*<br/>
COM 모듈에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 [CComModule:: RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (ATL 7.0에서 사용 되지 않음) 및 [CAtlExeModuleT:: RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)에서 활용 됩니다.

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a> AtlComModuleGetClassObject

이 함수는 클래스 팩터리를 반환하기 위해 호출됩니다.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>매개 변수

*pComModule*<br/>
COM 모듈에 대 한 포인터입니다.

*rclsid*<br/>
만들 개체의 CLSID입니다.

*riid*<br/>
요청 된 인터페이스의 IID입니다.

*ppv*<br/>
*Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않는 경우 *ppv* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 도우미 함수는 [CComModule:: GetClassObject](ccommodule-class.md#getclassobject) (ATL 7.0에서 사용 되지 않음) 및 [CAtlDllModuleT:: GetClassObject](catldllmodulet-class.md#getclassobject)에서 활용 됩니다.

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)

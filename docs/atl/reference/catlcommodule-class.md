---
title: CAtlComModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863207"
---
# <a name="catlcommodule-class"></a>CAtlComModule 클래스

이 클래스는 COM 서버 모듈을 구현 합니다.

## <a name="syntax"></a>구문

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>구성원

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CAtlComModule:: CAtlComModule](#catlcommodule)|생성자입니다.|
|[CAtlComModule:: ~ CAtlComModule](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[RegisterServer Lcommodule::](#registerserver)|이 메서드를 호출 하 여 개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 합니다.|
|[CAtlComModule:: RegisterTypeLib](#registertypelib)|형식 라이브러리를 등록 하려면이 메서드를 호출 합니다.|
|[UnregisterServer Lcommodule::](#unregisterserver)|개체 맵에 있는 각 개체의 등록을 취소 하려면이 메서드를 호출 합니다.|
|[CAtlComModule:: UnRegisterTypeLib](#unregistertypelib)|형식 라이브러리의 등록을 취소 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

`CAtlComModule` COM 서버 모듈을 구현 하 여 클라이언트가 모듈의 구성 요소에 액세스할 수 있도록 합니다.

이 클래스는 이전 버전의 ATL에서 사용 되는 사용 되지 않는 [CComModule](../../atl/reference/ccommodule-class.md) 클래스를 대체 합니다. 자세한 내용은 [ATL 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

##  <a name="catlcommodule"></a>CAtlComModule:: CAtlComModule

생성자입니다.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>설명

모듈을 초기화 합니다.

##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule

소멸자입니다.

```
~CAtlComModule();
```

### <a name="remarks"></a>설명

모든 클래스 팩터리를 해제 합니다.

##  <a name="registerserver"></a>RegisterServer Lcommodule::

이 메서드를 호출 하 여 개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 합니다.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>매개 변수

*bRegTypeLib*<br/>
형식 라이브러리를 등록 하려면 TRUE입니다. 기본값은 FALSE입니다.

*pCLSID*<br/>
등록할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 됩니다.

### <a name="return-value"></a>Return Value

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)전역 함수를 호출 합니다.

##  <a name="registertypelib"></a>CAtlComModule:: RegisterTypeLib

형식 라이브러리를 등록 하려면이 메서드를 호출 합니다.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>매개 변수

*lpszIndex*<br/>
"\\\N" 형식의 문자열입니다. 여기서 N은 TYPELIB 리소스의 정수 인덱스입니다.

### <a name="return-value"></a>Return Value

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

형식 라이브러리에 대 한 정보를 시스템 레지스트리에 추가 합니다. 모듈 인스턴스에 여러 형식 라이브러리가 포함 된 경우이 메서드의 첫 번째 버전을 사용 하 여 사용할 형식 라이브러리를 지정 합니다.

##  <a name="unregisterserver"></a>UnregisterServer Lcommodule::

개체 맵에 있는 각 개체의 등록을 취소 하려면이 메서드를 호출 합니다.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>매개 변수

*bRegTypeLib*<br/>
형식 라이브러리의 등록을 취소 하려면 TRUE입니다. 기본값은 FALSE입니다.

*pCLSID*<br/>
등록을 취소할 개체의 CLSID를 가리킵니다. NULL (기본값) 이면 개체 맵의 모든 개체가 등록 취소 됩니다.

### <a name="return-value"></a>Return Value

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)전역 함수를 호출 합니다.

##  <a name="unregistertypelib"></a>CAtlComModule:: UnRegisterTypeLib

형식 라이브러리의 등록을 취소 하려면이 메서드를 호출 합니다.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>매개 변수

*lpszIndex*<br/>
"\\\N" 형식의 문자열입니다. 여기서 N은 TYPELIB 리소스의 정수 인덱스입니다.

### <a name="remarks"></a>설명

시스템 레지스트리에서 형식 라이브러리에 대 한 정보를 제거 합니다. 모듈 인스턴스에 여러 형식 라이브러리가 포함 된 경우이 메서드의 첫 번째 버전을 사용 하 여 사용할 형식 라이브러리를 지정 합니다.

### <a name="return-value"></a>Return Value

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="see-also"></a>참고 항목

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

---
description: '자세한 정보: CAtlBaseModule 클래스'
title: CAtlBaseModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: 249b2ad2d133ba0f407e9c5fabcf716b09605972
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147539"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule 클래스

이 클래스는 모든 ATL 프로젝트에서 인스턴스화됩니다.

## <a name="syntax"></a>구문

```cpp
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlBaseModule:: CAtlBaseModule](#catlbasemodule)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlBaseModule:: AddResourceInstance](#addresourceinstance)|저장 된 핸들 목록에 리소스 인스턴스를 추가 합니다.|
|[CAtlBaseModule:: GetHInstanceAt](#gethinstanceat)|지정 된 리소스 인스턴스에 대 한 핸들을 반환 합니다.|
|[CAtlBaseModule:: GetModuleInstance](#getmoduleinstance)|개체에서 모듈 인스턴스를 반환 합니다 `CAtlBaseModule` .|
|[CAtlBaseModule:: GetResourceInstance](#getresourceinstance)|개체에서 리소스 인스턴스를 반환 합니다 `CAtlBaseModule` .|
|[CAtlBaseModule:: RemoveResourceInstance](#removeresourceinstance)|저장 된 핸들 목록에서 리소스 인스턴스를 제거 합니다.|
|[CAtlBaseModule:: SetResourceInstance](#setresourceinstance)|개체의 리소스 인스턴스를 설정 합니다 `CAtlBaseModule` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlBaseModule:: m_bInitFailed](#m_binitfailed)|모듈 초기화가 실패 했는지 여부를 나타내는 변수입니다.|

## <a name="remarks"></a>설명

명명 된 _AtlBaseModule의 인스턴스는 모듈 인스턴스에 대 한 핸들, 리소스를 포함 하는 모듈에 대 한 핸들, 기본 리소스를 제공 하는 모듈에 대 한 핸들, 기본 리소스를 제공 하는 모듈에 대 한 핸들 `CAtlBaseModule` 의 배열을 포함 하는 모든 ATL 프로젝트에 존재 합니다. `CAtlBaseModule` 여러 스레드에서 안전 하 게 액세스할 수 있습니다.

이 클래스는 이전 버전의 ATL에서 사용 되는 사용 되지 않는 [CComModule](../../atl/reference/ccommodule-class.md) 클래스를 대체 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a> CAtlBaseModule:: AddResourceInstance

저장 된 핸들 목록에 리소스 인스턴스를 추가 합니다.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>매개 변수

*hInst*<br/>
추가할 리소스 인스턴스입니다.

### <a name="return-value"></a>반환 값

리소스가 성공적으로 추가 되었으면 true를 반환 하 고 그렇지 않으면 false를 반환 합니다.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a> CAtlBaseModule:: CAtlBaseModule

생성자입니다.

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>설명

`CAtlBaseModule`를 만듭니다.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a> CAtlBaseModule:: GetHInstanceAt

지정 된 리소스 인스턴스에 대 한 핸들을 반환 합니다.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>매개 변수

*i*<br/>
리소스 인스턴스 번호입니다.

### <a name="return-value"></a>반환 값

리소스 인스턴스에 대 한 핸들을 반환 하거나, 해당 하는 리소스 인스턴스가 없으면 NULL을 반환 합니다.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a> CAtlBaseModule:: GetModuleInstance

개체에서 모듈 인스턴스를 반환 합니다 `CAtlBaseModule` .

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>반환 값

모듈 인스턴스를 반환 합니다.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a> CAtlBaseModule:: GetResourceInstance

리소스 인스턴스를 반환 합니다.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>반환 값

리소스 인스턴스를 반환 합니다.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a> CAtlBaseModule:: m_bInitFailed

모듈 초기화가 실패 했는지 여부를 나타내는 변수입니다.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>설명

모듈이 초기화 되었으면 True이 고, 초기화에 실패 하면 false입니다.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a> CAtlBaseModule:: RemoveResourceInstance

저장 된 핸들 목록에서 리소스 인스턴스를 제거 합니다.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>매개 변수

*hInst*<br/>
제거할 리소스 인스턴스입니다.

### <a name="return-value"></a>반환 값

리소스가 성공적으로 제거 되 면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a> CAtlBaseModule:: SetResourceInstance

개체의 리소스 인스턴스를 설정 합니다 `CAtlBaseModule` .

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>매개 변수

*hInst*<br/>
새 리소스 인스턴스입니다.

### <a name="return-value"></a>반환 값

업데이트 된 리소스 인스턴스를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

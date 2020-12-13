---
description: '자세한 정보: CAtlWinModule 클래스'
title: CAtlWinModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: 4ed0c52a59401fa5411fd6d5acbcaf72f31aeb11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152572"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 클래스

이 클래스는 ATL 창 구성 요소에 대 한 지원을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlWinModule:: CAtlWinModule](#catlwinmodule)|생성자입니다.|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlWinModule:: AddCreateWndData](#addcreatewnddata)|데이터 개체를 추가 합니다.|
|[CAtlWinModule:: ExtractCreateWndData](#extractcreatewnddata)|창 모듈 데이터 개체에 대 한 포인터를 반환 합니다.|

## <a name="remarks"></a>설명

이 클래스는 창 고 기능을 필요로 하는 모든 ATL 클래스를 지원 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a> CAtlWinModule:: AddCreateWndData

이 메서드는 구조체를 초기화 하 고 추가 `_AtlCreateWndData` 합니다.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>매개 변수

*pData*<br/>
`_AtlCreateWndData`초기화 되어 현재 모듈에 추가 되는 구조에 대 한 포인터입니다.

*pObject*<br/>
개체의 포인터에 대 한 포인터 **`this`** 입니다.

### <a name="remarks"></a>설명

이 메서드는 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) 구조체를 초기화 하는 [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) 를 호출 합니다. 이 구조체는 **`this`** 창 프로시저에서 클래스 인스턴스를 가져오는 데 사용 되는 포인터를 저장 합니다.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a> CAtlWinModule:: CAtlWinModule

생성자입니다.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>설명

초기화에 실패 하면 **EXCEPTION_NONCONTINUABLE** 예외가 발생 합니다.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a> CAtlWinModule:: ~ CAtlWinModule

소멸자입니다.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a> CAtlWinModule:: ExtractCreateWndData

이 메서드는 구조체에 대 한 포인터를 반환 합니다 `_AtlCreateWndData` .

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>반환 값

`_AtlCreateWndData` [AddCreateWndData](#addcreatewnddata)를 사용 하 여 이전에 추가 된 구조에 대 한 포인터를 반환 하거나, 사용할 수 있는 개체가 없으면 NULL을 반환 합니다.

## <a name="see-also"></a>참고 항목

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

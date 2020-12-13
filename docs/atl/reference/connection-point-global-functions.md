---
description: '자세한 정보: 연결 지점 전역 함수'
title: 연결 지점 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 33a9f81b086b572bb31f730e4a6ce1bac0fb45d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141143"
---
# <a name="connection-point-global-functions"></a>연결 지점 전역 함수

이러한 함수는 연결 지점과 싱크 맵에 대 한 지원을 제공 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|함수|설명|
|-|-|
|[AtlAdvise](#atladvise)|개체의 연결 지점과 클라이언트의 싱크 간에 연결을 만듭니다.|
|[AtlUnadvise](#atlunadvise)|를 통해 설정 된 연결을 종료 `AtlAdvise` 합니다.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|이벤트 싱크 맵에 항목을 제안 하거나 제안 하지 않습니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atladvise"></a><a name="atladvise"></a> 가 나 Advise

개체의 연결 지점과 클라이언트의 싱크 간에 연결을 만듭니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>매개 변수

*pUnkCP*<br/>
진행 클라이언트에서 연결 하려는 개체의에 대 한 포인터입니다 `IUnknown` .

*pUnk*<br/>
진행 클라이언트의에 대 한 포인터 `IUnknown` 입니다.

*iid*<br/>
진행 연결 지점의 GUID입니다. 일반적으로이는 연결 지점에서 관리 하는 송신 인터페이스와 동일 합니다.

*pdw*<br/>
제한이 연결을 고유 하 게 식별 하는 쿠키에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

싱크는 연결 지점에서 지 원하는 나가는 인터페이스를 구현 합니다. 클라이언트는 *pdw* 쿠키를 사용 하 여 [AtlUnadvise](#atlunadvise)에 전달 하 여 연결을 제거 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a> AtlUnadvise

이 [를 통해 설정](#atladvise)된 연결을 종료 합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>매개 변수

*pUnkCP*<br/>
진행 `IUnknown` 클라이언트와 연결 된 개체의에 대 한 포인터입니다.

*iid*<br/>
진행 연결 지점의 GUID입니다. 일반적으로이는 연결 지점에서 관리 하는 송신 인터페이스와 동일 합니다.

*dw*<br/>
진행 연결을 고유 하 게 식별 하는 쿠키입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a> AtlAdviseSinkMap

개체의 싱크 이벤트 맵에서 모든 항목을 advise하거나 unadvise하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
진행 싱크 맵을 포함 하는 개체에 대 한 포인터입니다.

*bAdvise*<br/>
진행 모든 싱크 항목이 advise 되 면 TRUE입니다. 모든 싱크 항목이 advise 되지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)<br/>
[연결 지점 매크로](../../atl/reference/connection-point-macros.md)

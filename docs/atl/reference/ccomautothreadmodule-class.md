---
description: '자세히 알아보기: CComAutoThreadModule 클래스'
title: CComAutoThreadModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: fe6ded878a054bdcdc2569c8ca347e2ac20410b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146941"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 클래스

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>매개 변수

*ThreadAllocator*<br/>
진행 스레드 선택을 관리 하는 클래스입니다. 기본값은 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)입니다.

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|함수|설명|
|-|-|
|[CreateInstance](#createinstance)|스레드를 선택한 다음 연결 된 아파트에서 개체를 만듭니다.|
|[GetDefaultThreads](#getdefaultthreads)|정적인 프로세서 수를 기준으로 모듈의 스레드 수를 동적으로 계산 합니다.|
|[Init](#init)|모듈의 스레드를 만듭니다.|
|[잠금](#lock)|모듈 및 현재 스레드에서 잠금 횟수를 증가 시킵니다.|
|[잠금 해제](#unlock)|모듈 및 현재 스레드에서 잠금 횟수를 감소 시킵니다.|

### <a name="data-members"></a>데이터 멤버

|데이터 멤버|설명|
|-|-|
|[dwThreadID](#dwthreadid)|현재 스레드의 식별자를 포함 합니다.|
|[m_Allocator](#m_allocator)|스레드 선택을 관리 합니다.|
|[m_nThreads](#m_nthreads)|모듈의 스레드 수를 포함 합니다.|
|[m_pApartments](#m_papartments)|모듈의 아파트를 관리 합니다.|

## <a name="remarks"></a>설명

> [!NOTE]
> 이 클래스는 구식 [Lautothreadmodule](../../atl/reference/catlautothreadmodule-class.md) 및 [bclmodule](../../atl/reference/catlmodule-class.md) 파생 클래스로 대체 되었습니다. 다음 정보는 ATL의 이전 릴리스와 함께 사용 하기 위한 것입니다.

`CComAutoThreadModule`[CComModule](../../atl/reference/ccommodule-class.md) 에서 파생 되어 Exe 및 Windows 서비스용 스레드 풀링된 아파트 모델 COM 서버를 구현 합니다. `CComAutoThreadModule`[CComApartment](../../atl/reference/ccomapartment-class.md) 를 사용 하 여 모듈의 각 스레드에 대 한 아파트를 관리 합니다.

`CComAutoThreadModule`여러 아파트에서 개체를 만들려는 경우에서 모듈을 파생 시킵니다. [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 을 클래스 팩터리로 지정 하려면 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 매크로도 포함 해야 합니다.

기본적으로 ATL COM 응용 프로그램 마법사 (Visual Studio .NET의 ATL 프로젝트 마법사)는에서 모듈을 파생 합니다 `CComModule` . 을 사용 하려면 `CComAutoThreadModule` 클래스 정의를 수정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a> CComAutoThreadModule:: CreateInstance

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>매개 변수

*pfnCreateInstance*<br/>
진행 Creator 함수에 대 한 포인터입니다.

*riid*<br/>
진행 요청 된 인터페이스의 IID입니다.

*ppvObj*<br/>
제한이 *Riid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobj* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

스레드를 선택한 다음 연결 된 아파트에서 개체를 만듭니다.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a> CComAutoThreadModule::d wThreadID

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>설명

현재 스레드의 식별자를 포함 합니다.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a> CComAutoThreadModule:: GetDefaultThreads

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>반환 값

EXE 모듈에서 만들 스레드 수입니다.

### <a name="remarks"></a>설명

이 정적 함수는 프로세서 수에 따라 EXE 모듈의 최대 스레드 수를 동적으로 계산 합니다. 기본적으로이 반환 값은 [Init](#init) 메서드에 전달 되어 스레드를 만듭니다.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a> CComAutoThreadModule:: Init

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 개체 맵 항목의 배열에 대 한 포인터입니다.

*h*<br/>
진행 또는에 전달 된 HINSTANCE `DLLMain` `WinMain` 입니다.

*plibid*<br/>
진행 프로젝트에 연결 된 형식 라이브러리의 LIBID에 대 한 포인터입니다.

*nThreads*<br/>
진행 만들 스레드 수입니다. 기본적으로 *Nthreads* 는 [GetDefaultThreads](#getdefaultthreads)에서 반환 하는 값입니다.

### <a name="remarks"></a>설명

데이터 멤버를 초기화 하 고 *nthreads* 로 지정 된 스레드 수를 만듭니다.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a> CComAutoThreadModule:: Lock

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
LONG Lock();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

모듈 및 현재 스레드에 대 한 잠금 수의 원자성 증분을 수행 합니다. `CComAutoThreadModule` 모듈 잠금 수를 사용 하 여 클라이언트가 모듈에 액세스 하 고 있는지 여부를 확인 합니다. 현재 스레드의 잠금 수는 통계 목적으로 사용 됩니다.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a> CComAutoThreadModule:: m_Allocator

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>설명

스레드 선택을 관리 하는 개체입니다. 기본적으로 `ThreadAllocator` 클래스 템플릿 매개 변수는 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)입니다.

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a> CComAutoThreadModule:: m_nThreads

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
int m_nThreads;
```

### <a name="remarks"></a>설명

EXE 모듈의 스레드 수를 포함 합니다. [Init](#init) 를 호출 하면 `m_nThreads` 가 *nthreads* 매개 변수 값으로 설정 됩니다. 각 스레드의 연결 된 아파트는 [CComApartment](../../atl/reference/ccomapartment-class.md) 개체를 통해 관리 됩니다.

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a> CComAutoThreadModule:: m_pApartments

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>설명

는 각각 모듈의 아파트를 관리 하는 [CComApartment](../../atl/reference/ccomapartment-class.md) 개체의 배열을 가리킵니다. 배열의 요소 수는 [m_nThreads](#m_nthreads) 멤버를 기반으로 합니다.

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a> CComAutoThreadModule:: Unlock

ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md) 를 참조 하세요.

```
LONG Unlock();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

모듈 및 현재 스레드에 대 한 잠금 수의 원자성 감소를 수행 합니다. `CComAutoThreadModule` 모듈 잠금 수를 사용 하 여 클라이언트가 모듈에 액세스 하 고 있는지 여부를 확인 합니다. 현재 스레드의 잠금 수는 통계 목적으로 사용 됩니다.

모듈 잠금 수가 0에 도달 하면 모듈을 언로드할 수 있습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

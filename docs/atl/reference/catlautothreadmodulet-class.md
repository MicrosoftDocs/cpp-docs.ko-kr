---
description: '자세한 정보: CAtlAutoThreadModuleT 클래스'
title: CAtlAutoThreadModuleT 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: ad55c78488567c12477c427b99a527b8154ddd22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158415"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 클래스

이 클래스는 스레드 풀의 아파트 모델 COM 서버를 구현 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>매개 변수

*T*<br/>
COM 서버를 구현 하는 클래스입니다.

*ThreadAllocator*<br/>
스레드 선택을 관리 하는 클래스입니다. 기본값은 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)입니다.

*dwWait*<br/>
제한 시간 간격 (밀리초)을 지정 합니다. 기본값은 무한 이며이는 메서드의 시간 제한 간격이 경과 하지 않음을 의미 합니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlAutoThreadModuleT:: GetDefaultThreads](#getdefaultthreads)|이 정적 함수는 프로세서 수에 따라 EXE 모듈의 최대 스레드 수를 동적으로 계산 하 고 반환 합니다.|

## <a name="remarks"></a>설명

[Catlautothreadmodule](../../atl/reference/catlautothreadmodule-class.md) 클래스는 `CAtlAutoThreadModuleT` 스레드 풀의 아파트 모델 COM 서버를 구현 하기 위해에서 파생 됩니다. 사용 되지 않는 클래스 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)을 대체 합니다.

> [!NOTE]
> 이 클래스는 dll에서 사용 하면 안 됩니다. 기본 *Dwwait* 값 무한은 dll이 언로드될 때 교착 상태가 발생 하기 때문입니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a> CAtlAutoThreadModuleT:: GetDefaultThreads

이 정적 함수는 프로세서 수에 따라 EXE 모듈의 최대 스레드 수를 동적으로 계산 하 고 반환 합니다.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>반환 값

EXE 모듈에서 만들 스레드 수입니다.

### <a name="remarks"></a>설명

스레드 수를 계산 하는 다른 방법을 사용 하려는 경우이 메서드를 재정의 합니다. 기본적으로 스레드 수는 프로세서 수를 기반으로 합니다.

## <a name="see-also"></a>참고 항목

[IAtlAutoThreadModule 클래스](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule 클래스](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)

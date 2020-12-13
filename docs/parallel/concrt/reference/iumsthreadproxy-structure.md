---
description: '자세한 정보: IUMSThreadProxy 구조체'
title: IUMSThreadProxy 구조체
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 02eb999b35143e4fc9e0416e02abb60c3c64768d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334322"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 구조체

실행 스레드에 대한 추상화입니다. 해당 스케줄러에 UMS(사용자 모드 예약 가능) 스레드를 부여하려는 경우 스케줄러 정책 요소 `SchedulerKind`의 값을 `UmsThreadDefault`로 설정하고 `IUMSScheduler` 인터페이스를 구현합니다. UMS 스레드는 Windows 7 이상 버전의 64비트 운영 체제에서만 지원됩니다.

## <a name="syntax"></a>구문

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IUMSThreadProxy:: EnterCriticalRegion](#entercriticalregion)|중요 한 영역을 입력 하기 위해 호출 됩니다. 중요 한 지역 내에서 스케줄러는 지역에서 발생 하는 비동기 차단 작업을 관찰 하지 않습니다. 즉, 스케줄러는 UMS 스레드에 대해 페이지 폴트, 스레드 일시 중단, 커널 비동기 프로시저 호출 (Apc) 등에 대해 다시 입력할 되지 않습니다.|
|[IUMSThreadProxy:: EnterHyperCriticalRegion](#enterhypercriticalregion)|중요 한 영역을 입력 하기 위해 호출 됩니다. 중요 한 영역 내에서 스케줄러는 지역에서 발생 하는 차단 작업을 관찰 하지 않습니다. 이는 스케줄러가 UMS 스레드에 대한 함수 호출 차단, 차단되는 잠금 가져오기 시도, 페이지 폴트, 스레드 보류, 커널 비동기 프로시저 호출(APC) 등에 재진입되지 않음을 의미합니다.|
|[IUMSThreadProxy:: ExitCriticalRegion](#exitcriticalregion)|중요 한 영역을 종료 하기 위해 호출 됩니다.|
|[IUMSThreadProxy:: ExitHyperCriticalRegion](#exithypercriticalregion)|중요 한 영역을 끝내기 위해 호출 됩니다.|
|[IUMSThreadProxy:: GetCriticalRegionType](#getcriticalregiontype)|스레드 프록시가 포함 된 임계 영역 종류를 반환 합니다. 중요 한 영역은 중요 한 영역에 대 한 상위 집합 이므로 코드가 중요 한 영역을 입력 한 다음, 중요 한 영역을 입력 하면이 `InsideHyperCriticalRegion` 반환 됩니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a> IUMSThreadProxy:: EnterCriticalRegion 메서드

중요 한 영역을 입력 하기 위해 호출 됩니다. 중요 한 지역 내에서 스케줄러는 지역에서 발생 하는 비동기 차단 작업을 관찰 하지 않습니다. 즉, 스케줄러는 UMS 스레드에 대해 페이지 폴트, 스레드 일시 중단, 커널 비동기 프로시저 호출 (Apc) 등에 대해 다시 입력할 되지 않습니다.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>반환 값

중요 지역의 새 깊이입니다. 중요 한 지역은 재진입입니다.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a> IUMSThreadProxy:: EnterHyperCriticalRegion 메서드

중요 한 영역을 입력 하기 위해 호출 됩니다. 중요 한 영역 내에서 스케줄러는 지역에서 발생 하는 차단 작업을 관찰 하지 않습니다. 이는 스케줄러가 UMS 스레드에 대한 함수 호출 차단, 차단되는 잠금 가져오기 시도, 페이지 폴트, 스레드 보류, 커널 비동기 프로시저 호출(APC) 등에 재진입되지 않음을 의미합니다.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>반환 값

중요 한 hyper-v 영역의 새 깊이입니다. 하이퍼에 중요 한 지역은 재진입입니다.

### <a name="remarks"></a>설명

스케줄러는 호출 하는 메서드와 이러한 지역에서 획득 하는 잠금의 상당히 주의 해야 합니다. 이러한 지역의 코드가 스케줄러에서 예약을 담당 하는 항목에서 보유 하 고 있는 잠금에서 차단 되는 경우 교착 상태가 뒤따르게 수 있습니다.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a> IUMSThreadProxy:: ExitCriticalRegion 메서드

중요 한 영역을 종료 하기 위해 호출 됩니다.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>반환 값

중요 지역의 새 깊이입니다. 중요 한 지역은 재진입입니다.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a> IUMSThreadProxy:: ExitHyperCriticalRegion 메서드

중요 한 영역을 끝내기 위해 호출 됩니다.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>반환 값

중요 한 hyper-v 영역의 새 깊이입니다. 하이퍼에 중요 한 지역은 재진입입니다.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a> IUMSThreadProxy:: GetCriticalRegionType 메서드

스레드 프록시가 포함 된 임계 영역 종류를 반환 합니다. 중요 한 영역은 중요 한 영역에 대 한 상위 집합 이므로 코드가 중요 한 영역을 입력 한 다음, 중요 한 영역을 입력 하면이 `InsideHyperCriticalRegion` 반환 됩니다.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>반환 값

스레드 프록시를 포함 하는 중요 한 영역의 형식입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[IUMSScheduler 구조체](iumsscheduler-structure.md)

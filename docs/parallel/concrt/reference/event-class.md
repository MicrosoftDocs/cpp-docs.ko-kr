---
title: "event 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2301e06554d99529c7d4e4e5215208dc4265970
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="event-class"></a>event 클래스
동시성 런타임을 명시적으로 인식하는 수동 다시 설정 이벤트입니다.  
  
## <a name="syntax"></a>구문  
  
```
class event;
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[~ event 소멸자](#dtor)|이벤트를 제거합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[reset](#reset)|이벤트 신호 되지 않은 상태로 다시 설정합니다.|  
|[set](#set)|이벤트를 발생을 시킵니다.|  
|[wait](#wait)|이벤트가 신호를 받을 때까지 기다립니다.|  
|[wait_for_multiple](#wait_for_multiple)|여러 이벤트 신호를 받을 때까지 기다립니다.|  
  
### <a name="public-constants"></a>공용 상수  
  
|이름|설명|  
|----------|-----------------|  
|[timeout_infinite](#timeout_infinite)|대기 시간이 초과되지 않아야 함을 나타내는 값입니다.|  
  
## <a name="remarks"></a>설명  
 자세한 내용은 참조 [동기화 데이터 구조](../../../parallel/concrt/synchronization-data-structures.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `event`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** concrt.h  
  
 **네임스페이스:** 동시성  
  
##  <a name="ctor"></a> 이벤트 

 새 이벤트를 생성 합니다.  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>설명  
  
##  <a name="dtor"></a> ~ 이벤트 

 이벤트를 제거합니다.  
  
```
~event();
```  
  
### <a name="remarks"></a>설명  
 소멸자가 실행 될 때 이벤트에서 대기 하는 스레드가 있습니다 사용할 수 있습니다. 이벤트가 해당 이벤트를 계속 대기 중인 스레드와 함께 소멸할 수 있도록 허용하면 정의되지 않은 동작이 발생합니다.  
  
##  <a name="reset"></a> 다시 설정 

 이벤트 신호 되지 않은 상태로 다시 설정합니다.  
  
```
void reset();
```  
  
##  <a name="set"></a> 설정 

 이벤트를 발생을 시킵니다.  
  
```
void set();
```  
  
### <a name="remarks"></a>설명  
 이벤트에 신호를 보내면 이벤트를 대기하고 있는 임의 수의 컨텍스트가 실행 가능하게 됩니다.  
  
##  <a name="timeout_infinite"></a> timeout_infinite 

 대기 시간이 초과되지 않아야 함을 나타내는 값입니다.  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="wait"></a> 대기 

 이벤트가 신호를 받을 때까지 기다립니다.  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>매개 변수  
 `_Timeout`  
 대기 시간이 초과 되기 전에 기간 (밀리초) 나타냅니다. 값 `COOPERATIVE_TIMEOUT_INFINITE` 제한 시간이 없음을 나타냅니다.  
  
### <a name="return-value"></a>반환 값  
 대기가 충족 된 경우 값 `0` 반환 되 고, 그러지 않으면 값 `COOPERATIVE_WAIT_TIMEOUT` 신호 이벤트 하지 않고 대기 시간이 초과 되었음을 나타냅니다.  
  
> [!IMPORTANT]
>  유니버설 Windows 플랫폼 (UWP) 응용 프로그램에서 호출 하지 마십시오 `wait` ASTA 스레드에서 있으므로이 현재 스레드를 차단할 수는 앱이 응답 하지 않는 발생할 수 있습니다.  
  
##  <a name="wait_for_multiple"></a> wait_for_multiple 

 여러 이벤트 신호를 받을 때까지 기다립니다.  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>매개 변수  
 `_PPEvents`  
 배열 대기 하는 이벤트입니다. 배열 내 이벤트 수로 표시 됩니다는 `count` 매개 변수입니다.  
  
 `count`  
 제공 된 배열 내에서 이벤트의 개수는 `_PPEvents` 매개 변수입니다.  
  
 `_FWaitAll`  
 경우 값으로 설정 `true`, 매개 변수는 지정 된 배열 내에서 모든 이벤트에 제공 하는 `_PPEvents` 매개 변수는 대기를 만족 하려면 신호를 보내야 합니다. 경우 값으로 설정 `false`, 지정 된 배열 내에서 모든 이벤트에 제공 하는 `_PPEvents` 신호 매개 변수는 대기를 만족 합니다.  
  
 `_Timeout`  
 대기 시간이 초과 되기 전에 기간 (밀리초) 나타냅니다. 값 `COOPERATIVE_TIMEOUT_INFINITE` 제한 시간이 없음을 나타냅니다.  
  
### <a name="return-value"></a>반환 값  
 배열 내의 인덱스에 제공 된 대기가 충족 된 경우는 `_PPEvents` ; 대기 조건을 만족 하는 매개 변수, 값 `COOPERATIVE_WAIT_TIMEOUT` 조건이 충족 될 하지 않고 대기 시간이 초과 되었음을 나타냅니다.  
  
### <a name="remarks"></a>설명  
 경우 매개 변수 `_FWaitAll` 값으로 설정 `true` 함수에서 반환 하는 인덱스는 모든 이벤트 신호를 보내야 하는 대기를 만족를 나타내려면 값 아닌지 사실 제외 특별 한 의미가 없습니다를 전달 `COOPERATIVE_WAIT_TIMEOUT`합니다.  
  
> [!IMPORTANT]
>  유니버설 Windows 플랫폼 (UWP) 응용 프로그램에서 호출 하지 마십시오 `wait_for_multiple` ASTA 스레드에서 있으므로이 현재 스레드를 차단할 수는 앱이 응답 하지 않는 발생할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [concurrency 네임스페이스](concurrency-namespace.md)

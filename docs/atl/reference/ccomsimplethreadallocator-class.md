---
description: '자세히 알아보기: CComSimpleThreadAllocator 클래스'
title: CComSimpleThreadAllocator 클래스
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 5925707ecd459475d9e9002af76fb76dd9cf9d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142189"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 클래스

이 클래스는 클래스에 대 한 스레드 선택을 관리 `CComAutoThreadModule` 합니다.

## <a name="syntax"></a>구문

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComSimpleThreadAllocator:: GetThread](#getthread)|스레드를 선택 합니다.|

## <a name="remarks"></a>설명

`CComSimpleThreadAllocator`[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)에 대 한 스레드 선택을 관리 합니다. `CComSimpleThreadAllocator::GetThread` 는 각 스레드를 순환 하 고 시퀀스의 다음 항목을 반환 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a> CComSimpleThreadAllocator:: GetThread

시퀀스에서 다음 스레드를 지정 하 여 스레드를 선택 합니다.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>매개 변수

*pApt*<br/>
ATL의 기본 구현에서는 사용 되지 않습니다.

*nThreads*<br/>
EXE 모듈의 최대 스레드 수입니다.

### <a name="return-value"></a>반환 값

0과 (*Nthreads* -1) 사이의 정수입니다. EXE 모듈의 스레드 중 하나를 식별 합니다.

### <a name="remarks"></a>설명

`GetThread`를 재정의 하 여 다른 방법으로 선택 하거나 *pApt* 매개 변수를 사용할 수 있습니다.

`GetThread` 는 [CComAutoThreadModule:: CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)에 의해 호출 됩니다.

## <a name="see-also"></a>참고 항목

[CComApartment 클래스](../../atl/reference/ccomapartment-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

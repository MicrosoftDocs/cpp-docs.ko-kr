---
description: '자세히 알아보기: IThreadPoolConfig 인터페이스'
title: IThreadPoolConfig 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: 143b456b08f7c5a14f99739cfe6bf424a3ee4baf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158012"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 인터페이스

이 인터페이스는 스레드 풀을 구성 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[GetSize](#getsize)|풀의 스레드 수를 가져오려면이 메서드를 호출 합니다.|
|[GetTimeout](#gettimeout)|스레드 풀에서 스레드가 종료 될 때까지 대기 하는 최대 시간 (밀리초)을 가져오려면이 메서드를 호출 합니다.|
|[SetSize](#setsize)|풀의 스레드 수를 설정 하려면이 메서드를 호출 합니다.|
|[SetTimeout](#settimeout)|스레드 풀에서 스레드가 종료 될 때까지 대기 하는 최대 시간 (밀리초)을 설정 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 인터페이스는 [Cthreadpool](../../atl/reference/cthreadpool-class.md)에서 구현 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a> IThreadPoolConfig:: GetSize

풀의 스레드 수를 가져오려면이 메서드를 호출 합니다.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>매개 변수

*pnNumThreads*<br/>
제한이 성공 시 풀의 스레드 수를 받는 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a> IThreadPoolConfig:: GetTimeout

스레드 풀에서 스레드가 종료 될 때까지 대기 하는 최대 시간 (밀리초)을 가져오려면이 메서드를 호출 합니다.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>매개 변수

*pdwMaxWait*<br/>
제한이 성공 시 스레드 풀에서 스레드가 종료 될 때까지 대기 하는 최대 시간 (밀리초)을 받는 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[IThreadPoolConfig:: GetSize](#getsize)를 참조 하세요.

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a> IThreadPoolConfig:: SetSize

풀의 스레드 수를 설정 하려면이 메서드를 호출 합니다.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>매개 변수

*nNumThreads*<br/>
풀에서 요청 된 스레드 수입니다.

*Nnumthreads* 가 음수 이면 총 스레드 수를 가져오기 위해 컴퓨터의 프로세서 수에 해당 절대값을 곱합니다.

*Nnumthreads* 가 0 인 경우 총 스레드 수를 얻기 위해 컴퓨터의 프로세서 수에 ATLS_DEFAULT_THREADSPERPROC을 곱합니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[IThreadPoolConfig:: GetSize](#getsize)를 참조 하세요.

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a> IThreadPoolConfig:: SetTimeout

스레드 풀에서 스레드가 종료 될 때까지 대기 하는 최대 시간 (밀리초)을 설정 하려면이 메서드를 호출 합니다.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>매개 변수

*dwMaxWait*<br/>
스레드 풀에서 스레드가 종료 될 때까지 대기 하는 요청 된 최대 시간 (밀리초)입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="example"></a>예제

[IThreadPoolConfig:: GetSize](#getsize)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 클래스](../../atl/reference/cthreadpool-class.md)

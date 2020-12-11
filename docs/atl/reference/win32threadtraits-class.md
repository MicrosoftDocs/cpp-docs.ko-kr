---
description: '자세히 알아보기: Win32ThreadTraits 클래스'
title: Win32ThreadTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: 6dc752c5e8d527f9329c7f4274243a8561dd6339
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157596"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 클래스

이 클래스는 Windows 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하지 않는 경우이 클래스를 사용 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class Win32ThreadTraits
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Win32ThreadTraits:: CreateThread](#createthread)|정적인 CRT 함수를 사용 하지 않아야 하는 스레드를 만들려면이 함수를 호출 합니다.|

## <a name="remarks"></a>설명

스레드 특성은 특정 스레드 형식에 대 한 생성 함수를 제공 하는 클래스입니다. 생성 함수에는 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 함수와 동일한 시그니처와 의미 체계가 있습니다.

스레드 특성은 다음 클래스에서 사용 됩니다.

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [C이상 스레드](../../atl/reference/cworkerthread-class.md)

스레드가 CRT 함수를 사용 하는 경우 대신 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 를 사용 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a> Win32ThreadTraits:: CreateThread

CRT 함수를 사용 하지 않아야 하는 스레드를 만들려면이 함수를 호출 합니다.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>매개 변수

*lpsa*<br/>
새 스레드의 보안 특성입니다.

*dwStackSize*<br/>
새 스레드의 스택 크기입니다.

*pfnThreadProc*<br/>
새 스레드의 스레드 프로시저입니다.

*pvParam*<br/>
스레드 프로시저에 전달할 매개 변수입니다.

*dwCreationFlags*<br/>
생성 플래그 (0 또는 CREATE_SUSPENDED)입니다.

*pdwThreadId*<br/>
제한이 성공 시 새로 만든 스레드의 스레드 ID를 받는 DWORD 변수의 주소입니다.

### <a name="return-value"></a>반환 값

새로 만든 스레드에 대 한 핸들 또는 실패 시 NULL을 반환 합니다. [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 확장 오류 정보를 가져옵니다.

### <a name="remarks"></a>설명

이 함수에 대 한 매개 변수에 대 한 자세한 내용은 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 를 참조 하세요.

이 함수 `CreateThread` 는를 호출 하 여 스레드를 만듭니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

---
title: CRTThreadTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496546"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 클래스

이 클래스는 CRT 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하는 경우이 클래스를 사용 합니다.

> [!IMPORTANT]
>  이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CRTThreadTraits
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|정적인 CRT 함수를 사용할 수 있는 스레드를 만들려면이 함수를 호출 합니다.|

## <a name="remarks"></a>설명

스레드 특성은 특정 스레드 형식에 대 한 생성 함수를 제공 하는 클래스입니다. 생성 함수에는 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 함수와 동일한 시그니처와 의미 체계가 있습니다.

스레드 특성은 다음 클래스에서 사용 됩니다.

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

스레드가 CRT 함수를 사용 하지 않을 경우 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) 를 대신 사용 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

CRT 함수를 사용할 수 있는 스레드를 만들려면이 함수를 호출 합니다.

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

이 함수는 [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) 를 호출 하 여 스레드를 만듭니다.

## <a name="see-also"></a>참고자료

[클래스 개요](../../atl/atl-class-overview.md)

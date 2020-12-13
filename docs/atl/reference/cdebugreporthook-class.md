---
description: '자세히 알아보기: CDebugReportHook 클래스'
title: CDebugReportHook 클래스
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 0b26965114caefb8727a34b99a7cacb30c415aac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141975"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 클래스

이 클래스를 사용 하 여 디버그 보고서를 명명 된 파이프로 보낼 수 있습니다.

## <a name="syntax"></a>구문

```
class CDebugReportHook
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|[SetPipeName](#setpipename), [SetTimeout](#settimeout)및 [seok](#sethook)를 호출 합니다.|
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|[CDebugReportHook:: RemoveHook](#removehook)를 호출 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|정적인 C 런타임 디버그 보고 프로세스에 연결 되는 사용자 지정 보고 함수입니다.|
|[CDebugReportHook:: RemoveHook](#removehook)|이 메서드를 호출 하 여 디버그 보고서를 명명 된 파이프로 보내고 이전 보고서 후크를 복원 합니다.|
|[CDebugReportHook:: Seok](#sethook)|이 메서드를 호출 하 여 디버그 보고서를 명명 된 파이프로 보내기 시작 합니다.|
|[CDebugReportHook::SetPipeName](#setpipename)|이 메서드를 호출 하 여 디버그 보고서를 보낼 파이프의 이름과 컴퓨터를 설정 합니다.|
|[CDebugReportHook:: SetTimeout](#settimeout)|이 메서드를 호출 하 여이 클래스에서 명명 된 파이프를 사용할 수 있을 때까지 대기 하는 시간 (밀리초)을 설정 합니다.|

## <a name="remarks"></a>설명

디버그 보고서를 명명 된 파이프로 보내기 위해 서비스 또는 응용 프로그램의 디버그 빌드에서이 클래스의 인스턴스를 만듭니다. 디버그 [보고서는](debugging-and-error-reporting-macros.md#atltrace) [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 를 호출 하거나이 함수에 대 한 [래퍼를 사용](debugging-and-error-reporting-macros.md#atlassert) 하 여 생성 됩니다.

이 클래스를 사용 하면 비 대화형 [윈도우 스테이션](/windows/win32/winstation/window-stations)에서 실행 되는 구성 요소를 대화형으로 디버그할 수 있습니다.

디버그 보고서는 스레드의 기본 보안 컨텍스트를 사용 하 여 전송 됩니다. 웹 응용 프로그램에서와 같이 낮은 권한의 사용자가 발생 하는 상황에서 디버그 보고서를 볼 수 있도록 가장을 일시적으로 사용할 수 없습니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a> CDebugReportHook::CDebugReportHook

[SetPipeName](#setpipename), [SetTimeout](#settimeout)및 [seok](#sethook)를 호출 합니다.

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>매개 변수

*szMachineName*<br/>
디버그 출력을 보내야 하는 컴퓨터의 이름입니다. 기본값은 로컬 컴퓨터입니다.

*szPipeName*<br/>
디버그 출력을 보내야 하는 명명 된 파이프의 이름입니다.

*dwTimeout*<br/>
이 클래스에서 명명 된 파이프가 사용 가능 해질 때까지 대기 하는 시간 (밀리초)입니다.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a> CDebugReportHook:: ~ CDebugReportHook

[CDebugReportHook:: RemoveHook](#removehook)를 호출 합니다.

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a> CDebugReportHook::CDebugReportHookProc

C 런타임 디버그 보고 프로세스에 연결 되는 사용자 지정 보고 함수입니다.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 유형 (_CRT_WARN, _CRT_ERROR 또는 _CRT_ASSERT)입니다.

*message*<br/>
메시지 문자열입니다.

*returnValue*<br/>
[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)에서 반환 해야 하는 값입니다.

### <a name="return-value"></a>반환 값

후크가 메시지를 완전히 처리 하 여 추가 보고가 필요 하지 않으면 FALSE를 반환 합니다. `_CrtDbgReport`에서 일반적인 방법으로 메시지를 보고 해야 하는 경우 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

보고 함수는 명명 된 파이프를 열고 다른 쪽 끝에 있는 프로세스와 통신 하려고 합니다. 파이프가 사용 중인 경우 보고 함수는 파이프가 사용 가능 하지 않거나 제한 시간이 만료 될 때까지 대기 합니다. 제한 시간은 생성자 또는 [CDebugReportHook:: SetTimeout](#settimeout)에 대 한 호출로 설정할 수 있습니다.

이 함수의 코드는 호출 스레드의 기본 보안 컨텍스트에서 실행 됩니다. 즉,이 함수를 실행 하는 동안에는 가장이 사용 되지 않습니다.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a> CDebugReportHook:: RemoveHook

이 메서드를 호출 하 여 디버그 보고서를 명명 된 파이프로 보내고 이전 보고서 후크를 복원 합니다.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>설명

[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) 를 호출 하 여 이전 보고서 후크를 복원 합니다.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a> CDebugReportHook:: Seok

이 메서드를 호출 하 여 디버그 보고서를 명명 된 파이프로 보내기 시작 합니다.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>설명

[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) 를 호출 하 여 [CDebugReportHookProc](#cdebugreporthookproc) 를 통해 명명 된 파이프로 라우팅되는 디버그 보고서를 포함 합니다. 이 클래스는 [removehook](#removehook) 호출 될 때 복원할 수 있도록 이전 보고서 후크를 계속 추적 합니다.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a> CDebugReportHook::SetPipeName

이 메서드를 호출 하 여 디버그 보고서를 보낼 파이프의 이름과 컴퓨터를 설정 합니다.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>매개 변수

*szMachineName*<br/>
디버그 출력을 보내야 하는 컴퓨터의 이름입니다.

*szPipeName*<br/>
디버그 출력을 보내야 하는 명명 된 파이프의 이름입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a> CDebugReportHook:: SetTimeout

이 메서드를 호출 하 여이 클래스에서 명명 된 파이프를 사용할 수 있을 때까지 대기 하는 시간 (밀리초)을 설정 합니다.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>매개 변수

*dwTimeout*<br/>
이 클래스에서 명명 된 파이프가 사용 가능 해질 때까지 대기 하는 시간 (밀리초)입니다.

## <a name="see-also"></a>참고 항목

[클래스](../../atl/reference/atl-classes.md)

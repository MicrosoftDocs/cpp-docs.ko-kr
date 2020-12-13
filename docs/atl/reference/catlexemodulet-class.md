---
description: '자세히 알아보기: CAtlExeModuleT 클래스'
title: CAtlExeModuleT 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: f6b91ec011e2cfebaf09a5a78119c65688c4a153
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147409"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT 클래스

이 클래스는 응용 프로그램에 대 한 모듈을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CAtlExeModuleT` 입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlExeModuleT:: CAtlExeModuleT](#catlexemodulet)|생성자입니다.|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlExeModuleT:: InitializeCom](#initializecom)|COM을 초기화 합니다.|
|[CAtlExeModuleT::P arseCommandLine](#parsecommandline)|명령줄을 구문 분석 하 고 필요한 경우 등록을 수행 합니다.|
|[CAtlExeModuleT::P ostMessageLoop](#postmessageloop)|이 메서드는 메시지 루프가 종료 된 직후에 호출 됩니다.|
|[CAtlExeModuleT::P reMessageLoop](#premessageloop)|이 메서드는 메시지 루프를 입력 하기 바로 전에 호출 됩니다.|
|[CAtlExeModuleT:: RegisterClassObjects](#registerclassobjects)|클래스 개체를 등록 합니다.|
|[CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects)|클래스 개체를 취소 합니다.|
|[CAtlExeModuleT:: Run](#run)|이 메서드는 EXE 모듈의 코드를 실행 하 여 초기화 하 고, 메시지 루프를 실행 하 고, 정리 합니다.|
|[CAtlExeModuleT:: RunMessageLoop](#runmessageloop)|이 메서드는 메시지 루프를 실행 합니다.|
|[CAtlExeModuleT:: UninitializeCom](#uninitializecom)|초기화 하지 않습니다 COM.|
|[CAtlExeModuleT:: Unlock](#unlock)|모듈의 잠금 횟수를 줄입니다.|
|[CAtlExeModuleT:: WinMain](#winmain)|이 메서드는 EXE를 실행 하는 데 필요한 코드를 구현 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)|모듈을 종료 하는 지연이 있어야 함을 나타내는 플래그입니다.|
|[CAtlExeModuleT:: m_dwPause](#m_dwpause)|종료 하기 전에 모든 개체가 해제 되도록 하는 일시 중지 값입니다.|
|[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)|모듈 언로드를 지연 하는 데 사용 되는 제한 시간 값입니다.|

## <a name="remarks"></a>설명

`CAtlExeModuleT` 응용 프로그램 (EXE)에 대 한 모듈을 나타내며 EXE를 만들고, 명령줄을 처리 하 고, 클래스 개체를 등록 하 고, 메시지 루프를 실행 하 고, 종료 시 정리 하는 작업을 지 원하는 코드를 포함 합니다.

이 클래스는 EXE 서버의 COM 개체가 지속적으로 만들어지고 제거 될 때 성능을 향상 시 키도 록 설계 되었습니다. 마지막 COM 개체가 해제 된 후 EXE는 [CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout) 데이터 멤버로 지정 된 기간 동안 대기 합니다. 이 기간 동안 활동이 없으면 (즉, COM 개체가 생성 되지 않음) 종료 프로세스가 시작 됩니다.

[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown) 데이터 멤버는 EXE에서 위에 정의 된 메커니즘을 사용 해야 하는지 여부를 결정 하는 데 사용 되는 플래그입니다. False로 설정 하면 모듈이 즉시 종료 됩니다.

ATL의 모듈에 대 한 자세한 내용은 [Atl 모듈 클래스](../../atl/atl-module-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a> CAtlExeModuleT:: CAtlExeModuleT

생성자입니다.

```cpp
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>설명

EXE 모듈을 초기화할 수 없는 경우에는 더 이상 처리 하지 않고 WinMain이 즉시 반환 됩니다.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a> CAtlExeModuleT:: ~ CAtlExeModuleT

소멸자입니다.

```cpp
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a> CAtlExeModuleT:: InitializeCom

COM을 초기화 합니다.

```cpp
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 생성자에서 호출 되며 기본 구현과 다른 방식으로 COM을 초기화 하도록 재정의할 수 있습니다. 기본 구현에서는 `CoInitializeEx(NULL, COINIT_MULTITHREADED)` `CoInitialize(NULL)` 프로젝트 구성에 따라 또는를 호출 합니다.

이 메서드를 재정의 하려면 일반적으로 [CAtlExeModuleT:: UninitializeCom](#uninitializecom)를 재정의 해야 합니다.

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a> CAtlExeModuleT:: m_bDelayShutdown

모듈을 종료 하는 지연이 있어야 함을 나타내는 플래그입니다.

```cpp
bool m_bDelayShutdown;
```

### <a name="remarks"></a>설명

자세한 내용은 [CAtlExeModuleT 개요](../../atl/reference/catlexemodulet-class.md) 를 참조 하세요.

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a> CAtlExeModuleT:: m_dwPause

종료 하기 전에 모든 개체가 사라졌는지 확인 하는 데 사용 되는 일시 중지 값입니다.

```cpp
DWORD m_dwPause;
```

### <a name="remarks"></a>설명

[CAtlExeModuleT:: InitializeCom](#initializecom) 를 호출한 후이 값을 변경 하 여 서버를 종료 하는 일시 중지 값으로 사용 되는 시간 (밀리초)을 설정 합니다. 기본값은 1000 밀리초입니다.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a> CAtlExeModuleT:: m_dwTimeOut

모듈 언로드를 지연 하는 데 사용 되는 제한 시간 값입니다.

```cpp
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>설명

[CAtlExeModuleT:: InitializeCom](#initializecom) 를 호출한 후이 값을 변경 하 여 서버를 종료 하는 시간 제한 값으로 사용 되는 시간 (밀리초)을 정의 합니다. 기본값은 5000밀리초입니다. 자세한 내용은 [CAtlExeModuleT 개요](../../atl/reference/catlexemodulet-class.md) 를 참조 하세요.

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a> CAtlExeModuleT::P arseCommandLine

명령줄을 구문 분석 하 고 필요한 경우 등록을 수행 합니다.

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>매개 변수

*lpCmdLine*<br/>
응용 프로그램에 전달 된 명령줄입니다.

*pnRetCode*<br/>
등록에 해당 하는 HRESULT입니다 (발생 한 경우).

### <a name="return-value"></a>반환 값

응용 프로그램을 계속 실행 해야 하면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [CAtlExeModuleT:: WinMain](#winmain) 에서 호출 되며 명령줄 스위치를 처리 하기 위해 재정의할 수 있습니다. 기본 구현에서는 **/RegServer** 및 **/UnRegServer** 명령줄 인수가 있는지 확인 하 고 등록 또는 등록 취소를 수행 합니다.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a> CAtlExeModuleT::P ostMessageLoop

이 메서드는 메시지 루프가 종료 된 직후에 호출 됩니다.

```cpp
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 응용 프로그램 정리를 수행 하려면이 메서드를 재정의 합니다. 기본 구현에서는 [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects)를 호출 합니다.

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a> CAtlExeModuleT::P reMessageLoop

이 메서드는 메시지 루프를 입력 하기 바로 전에 호출 됩니다.

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
WinMain에서 *Nshowcmd* 매개 변수로 전달 되는 값입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

응용 프로그램에 대 한 사용자 지정 초기화 코드를 추가 하려면이 메서드를 재정의 합니다. 기본 구현에서는 클래스 개체를 등록 합니다.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a> CAtlExeModuleT:: RegisterClassObjects

다른 응용 프로그램에서 연결할 수 있도록 OLE에 클래스 개체를 등록 합니다.

```cpp
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>매개 변수

*dwClsContext*<br/>
클래스 개체가 실행 될 컨텍스트를 지정 합니다. 가능한 값은 CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER 또는 CLSCTX_LOCAL_SERVER입니다.

*dwFlags*<br/>
클래스 개체에 대 한 연결 유형을 결정 합니다. 가능한 값은 REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE 또는 REGCLS_MULTI_SEPARATE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK을 반환 하 고, 등록할 클래스가 없는 경우 S_FALSE 하거나, 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a> CAtlExeModuleT:: RevokeClassObjects

클래스 개체를 제거 합니다.

```cpp
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK을 반환 하 고, 등록할 클래스가 없는 경우 S_FALSE 하거나, 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlexemoduletrun"></a><a name="run"></a> CAtlExeModuleT:: Run

이 메서드는 EXE 모듈의 코드를 실행 하 여 초기화 하 고, 메시지 루프를 실행 하 고, 정리 합니다.

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
창이 표시 되는 방법을 지정 합니다. 이 매개 변수는 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) 섹션에서 설명 하는 값 중 하나일 수 있습니다. 기본값은 SW_HIDE입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드를 재정의할 수 있습니다. 그러나 실제로 [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)또는 [CAtlExeModuleT::P ostmessageloop](#postmessageloop) 를 재정의 하는 것이 더 좋습니다.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a> CAtlExeModuleT:: RunMessageLoop

이 메서드는 메시지 루프를 실행 합니다.

```cpp
void RunMessageLoop() throw();
```

### <a name="remarks"></a>설명

이 메서드를 재정의 하 여 메시지 루프의 동작을 변경할 수 있습니다.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a> CAtlExeModuleT:: UninitializeCom

초기화 하지 않습니다 COM.

```cpp
static void UninitializeCom() throw();
```

### <a name="remarks"></a>설명

기본적으로이 메서드는 [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) 를 호출 하며 소멸자에서 호출 됩니다. [CAtlExeModuleT:: InitializeCom](#initializecom)를 재정의 하는 경우이 메서드를 재정의 합니다.

## <a name="catlexemoduletunlock"></a><a name="unlock"></a> CAtlExeModuleT:: Unlock

모듈의 잠금 횟수를 줄입니다.

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값을 반환 합니다.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a> CAtlExeModuleT:: WinMain

이 메서드는 EXE를 실행 하는 데 필요한 코드를 구현 합니다.

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>매개 변수

*nShowCmd*<br/>
창이 표시 되는 방법을 지정 합니다. 이 매개 변수는 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) 섹션에서 설명 하는 값 중 하나일 수 있습니다.

### <a name="return-value"></a>반환 값

실행 파일의 반환 값을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드를 재정의할 수 있습니다. [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT::P ostmessageloop](#postmessageloop)또는 [CAtlExeModuleT:: RunMessageLoop](#runmessageloop) 재정의가 충분 한 유연성을 제공 하지 않을 경우 `WinMain` 이 메서드를 사용 하 여 함수를 재정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ATLDuck 샘플](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT 클래스](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 클래스](../../atl/reference/catldllmodulet-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)

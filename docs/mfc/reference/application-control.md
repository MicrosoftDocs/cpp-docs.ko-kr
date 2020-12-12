---
description: '자세히 알아보기: 응용 프로그램 제어'
title: 애플리케이션 컨트롤
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 20a777f5b7bb20870e9156ee090ff24ec4690f14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322826"
---
# <a name="application-control"></a>애플리케이션 컨트롤

OLE에서는 응용 프로그램 및 해당 개체에 대 한 상당한 제어가 필요 합니다. OLE 시스템 Dll은 응용 프로그램을 자동으로 시작 및 해제 하 고, 개체의 프로덕션 및 수정 작업을 조정 하는 등의 작업을 수행할 수 있어야 합니다. 이 항목의 함수는 이러한 요구 사항을 충족 합니다. 이러한 함수는 OLE 시스템 Dll에서 호출 하는 것 외에 응용 프로그램 에서도 호출 되어야 합니다.

### <a name="application-control"></a>애플리케이션 컨트롤

| Name | 설명 |
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|애플리케이션이 종료될 수 있는지 여부를 나타냅니다.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|응용 프로그램의 현재 메시지 필터를 검색 합니다.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|현재 사용자 제어 플래그를 검색 합니다.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|사용자 컨트롤 플래그를 설정 하거나 해제 합니다.|
|[AfxOleLockApp](#afxolelockapp)|응용 프로그램의 최대 활성 개체 수에 대 한 프레임 워크의 전역 수를 늘립니다.|
|[AfxOleLockControl](#afxolelockcontrol)| 지정 된 컨트롤의 클래스 팩터리를 잠급니다. |
|[AfxOleUnlockApp](#afxoleunlockapp)|응용 프로그램에서 프레임 워크의 활성 개체 수를 줄입니다.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 지정 된 컨트롤의 클래스 팩터리를 잠금 해제 합니다. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|OLE 시스템 레지스트리에 서버를 등록 합니다.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|*Typename* 개체 명령에 대 한 사용자 인터페이스를 구현 합니다.|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a> AfxOleCanExitApp

애플리케이션이 종료될 수 있는지 여부를 나타냅니다.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>반환 값

애플리케이션이 종료될 수 있으면 0이 아닌 값이고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

개체에 대해 해결되지 않은 참조가 있으면 애플리케이션이 종료될 수 없습니다. 전역 함수 `AfxOleLockApp` 및 `AfxOleUnlockApp`은 각각 애플리케이션의 개체에 대한 참조 수를 늘리거나 줄입니다. 이 카운터가 0이 아니면 애플리케이션이 종료될 수 없습니다. 카운터가 0이 아니면 사용자가 시스템 메뉴에서 닫기를 선택하거나 파일 메뉴에서 종료를 선택할 때 애플리케이션의 기본 창이 숨겨집니다(삭제되지 않음). 프레임 워크는에서이 함수를 호출 `CFrameWnd::OnClose` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a> AfxOleGetMessageFilter

응용 프로그램의 현재 메시지 필터를 검색 합니다.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>반환 값

현재 메시지 필터에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`COleMessageFilter` `AfxGetApp` 현재 응용 프로그램 개체에 액세스 하기 위해를 호출 하는 것 처럼 현재 파생 개체에 액세스 하려면이 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>요구 사항

**헤더**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a> AfxOleGetUserCtrl

현재 사용자 제어 플래그를 검색 합니다.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>반환 값

사용자가 응용 프로그램을 제어 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자가 명시적으로 열거나 새 문서를 만든 경우 사용자가 응용 프로그램을 제어할 수 있습니다. 사용자가 응용 프로그램을 OLE 시스템 Dll에서 시작 하지 않은 경우 (즉, 사용자가 시스템 셸을 사용 하 여 응용 프로그램을 시작한 경우)에도 사용자가 제어할 수 있습니다.

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a> AfxOleSetUserCtrl

에 대 한 참조에서 설명 하는 사용자 제어 플래그를 설정 하거나 해제 합니다 `AfxOleGetUserCtrl` .

```cpp
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>매개 변수

*bUserCtrl*<br/>
사용자 컨트롤 플래그를 설정 하거나 지우도록 지정 합니다.

### <a name="remarks"></a>설명

프레임 워크는 사용자가 문서를 만들거나 로드할 때이 함수를 호출 하지만, 컨테이너 응용 프로그램에서 포함 된 개체를 로드 하는 것과 같은 간접 작업을 통해 문서를 로드 하거나 만들 때이 함수를 호출 합니다.

응용 프로그램의 다른 작업에서 사용자를 응용 프로그램의 제어에 배치 해야 하는 경우이 함수를 호출 합니다.

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a> Afxolelockapp 호출

응용 프로그램의 최대 활성 개체 수에 대 한 프레임 워크의 전역 수를 늘립니다.

```cpp
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>설명

프레임 워크는 응용 프로그램에서 활성 상태인 개체의 수를 유지 합니다. `AfxOleLockApp`및 `AfxOleUnlockApp` 함수는 각각이 개수를 증가 및 감소 시킵니다.

사용자가 활성 개체를 포함 하는 응용 프로그램을 닫으려고 하면 (활성 개체의 수가 0이 아닌 응용 프로그램) 프레임 워크가 완전히 종료 되는 대신 사용자의 뷰에서 응용 프로그램을 숨깁니다. `AfxOleCanExitApp`함수는 응용 프로그램을 종료할 수 있는지 여부를 나타냅니다.

`AfxOleLockApp`클라이언트 응용 프로그램에서 사용 하는 동안 해당 개체를 제거 하는 것이 바람직하지 않은 경우 OLE 인터페이스를 노출 하는 개체에서를 호출 합니다. 또한 `AfxOleUnlockApp` 생성자에서를 호출 하는 개체의 소멸자에서를 호출 `AfxOleLockApp` 합니다. 기본적으로 `COleDocument` 및 파생 클래스는 응용 프로그램을 자동으로 잠그고 잠금 해제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a> 가 afxoleunlockapp

응용 프로그램에서 프레임 워크의 활성 개체 수를 줄입니다.

```cpp
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>설명

자세한 `AfxOleLockApp` 내용은를 참조 하십시오.

활성 개체 수가 0에 도달 하면 `AfxOleOnReleaseAllObjects` 가 호출 됩니다.

### <a name="example"></a>예제

[Afxolelockapp 호출](#afxolelockapp)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

컨트롤과 연결된 동적으로 생성된 데이터가 메모리에 유지되도록 지정된 컨트롤의 클래스 팩터리를 잠급니다.

### <a name="syntax"></a>구문

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>매개 변수

*가*<br/>
컨트롤의 고유 클래스 ID입니다.

*lpszProgID*<br/>
컨트롤의 고유 프로그램 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤의 클래스 팩터리가 성공적으로 잠겼을 경우 0이 아닌 값이고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이렇게 하면 컨트롤 표시 속도가 상당히 빨라질 수 있습니다. 예를 들어 대화 상자에서 컨트롤을 만들고 이 컨트롤을 `AfxOleLockControl`로 잠글 경우에는 대화 상자를 표시 또는 삭제할 때마다 대화 상자를 만들고 종료할 필요가 없습니다. 사용자가 대화 상자를 반복해서 열고 닫는 경우, 컨트롤을 잠그면 성능이 크게 향상될 수 있습니다. 컨트롤을 제거할 준비가 되면 `AfxOleUnlockControl`을 호출합니다.

### <a name="example"></a>예제

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a> AfxOleRegisterServerClass

이 함수를 사용 하면 OLE 시스템 레지스트리에 서버를 등록할 수 있습니다.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
서버의 OLE 클래스 ID에 대 한 참조입니다.

*lpszClassName*<br/>
서버 개체의 클래스 이름을 포함 하는 문자열에 대 한 포인터입니다.

*lpszShortTypeName*<br/>
서버 개체 형식의 짧은 이름 (예: "Chart")을 포함 하는 문자열에 대 한 포인터입니다.

*lpszLongTypeName*<br/>
서버 개체 형식의 긴 이름을 포함 하는 문자열에 대 한 포인터입니다 (예: "Microsoft Excel 5.0 차트").

*nAppType*<br/>
OLE 응용 프로그램의 유형을 지정 하는 OLE_APPTYPE 열거형에서 가져온 값입니다. 가능한 값은 다음과 같습니다.

- OAT_INPLACE_SERVER 서버에는 전체 서버 사용자 인터페이스가 있습니다.

- OAT_SERVER 서버는 포함만 지원 합니다.

- OAT_CONTAINER 컨테이너는 포함에 대 한 링크를 지원 합니다.

- OAT_DISPATCH_OBJECT `IDispatch` 가능 개체입니다.

*rglpszRegister*<br/>
키에 대 한 기존 값을 찾을 수 없는 경우 OLE 시스템 레지스트리에 추가할 키와 값을 나타내는 문자열에 대 한 포인터의 배열입니다.

*rglpszOverwrite*<br/>
레지스트리에 지정 된 키에 대 한 기존 값이 포함 된 경우 OLE 시스템 레지스트리에 추가할 키와 값을 나타내는 문자열에 대 한 포인터의 배열입니다.

### <a name="return-value"></a>반환 값

서버 클래스가 성공적으로 등록 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

대부분의 응용 프로그램은 `COleTemplateServer::Register` 를 사용 하 여 응용 프로그램의 문서 유형을 등록할 수 있습니다. 응용 프로그램의 시스템 레지스트리 형식이 일반적인 패턴에 맞지 않는 경우 `AfxOleRegisterServerClass` 더 많은 제어를 위해를 사용할 수 있습니다.

레지스트리는 키와 값 집합으로 구성 됩니다. *RglpszRegister* 및 *rglpszOverwrite* 인수는 각각 키와 **NULL** 문자 ()로 구분 된 값으로 구성 되는 문자열에 대 한 포인터의 배열입니다 `'\0'` . 이러한 각 문자열에는 해당 위치가 문자 시퀀스 *%1* 에서 *%5 (* 으)로 표시 되는 대체 가능 매개 변수가 있을 수 있습니다.

기호는 다음과 같이 채워집니다.

|기호|값|
|------------|-----------|
|%1|문자열 형식의 클래스 ID|
|%2|클래스 이름|
|%3|실행 파일의 경로|
|%4|약식 형식 이름|
|%5|Long 형식 이름|

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a> AfxOleSetEditMenu

*Typename* 개체 명령에 대 한 사용자 인터페이스를 구현 합니다.

```cpp
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>매개 변수

*pClient*<br/>
클라이언트 OLE 항목에 대 한 포인터입니다.

*pMenu*<br/>
업데이트할 메뉴 개체에 대 한 포인터입니다.

*iMenuItem*<br/>
업데이트할 메뉴 항목의 인덱스입니다.

*nIDVerbMin*<br/>
기본 동사에 해당 하는 명령 ID입니다.

*nIDVerbMax*<br/>
마지막 동사에 해당 하는 명령 ID입니다.

*nIDConvert*<br/>
변환 메뉴 항목의 ID입니다.

### <a name="remarks"></a>설명

서버에서 기본 동사로 인식 하면 메뉴 항목은 "동사 *typename* 개체"가 되 고 사용자가 명령을 선택 하면 *nIDVerbMin* 명령이 전송 됩니다. 서버에서 여러 동사를 인식 하는 경우 메뉴 항목은 " *typename* 개체"가 되 고 사용자가 명령을 선택 하면 모든 동사가 나열 된 하위 메뉴가 나타납니다. 사용자가 하위 메뉴에서 동사를 선택 하면 첫 번째 동사를 선택 하면 *nIDVerbMin* 가 전송 되 고 두 번째 동사가 선택 된 경우 *nIDVerbMin* + 1이 전송 됩니다. 기본 `COleDocument` 구현에서는이 기능을 자동으로 처리 합니다.

클라이언트의 응용 프로그램 리소스 스크립트 ()에 다음 문이 있어야 합니다. RC) 파일:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>요구 사항

**헤더**: afxole

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

지정 된 컨트롤의 클래스 팩터리를 잠금 해제 합니다.

### <a name="syntax"></a>구문

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>매개 변수

*가*<br/>
컨트롤의 고유 클래스 ID입니다.

*lpszProgID*<br/>
컨트롤의 고유 프로그램 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤의 클래스 팩터리가 성공적으로 잠금 해제 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

컨트롤은로 잠겨 `AfxOleLockControl` 있으므로 컨트롤과 연결 된 동적으로 생성 된 데이터는 메모리에 유지 됩니다. 컨트롤이 표시 될 때마다 컨트롤을 만들고 제거할 필요가 없기 때문에 컨트롤의 표시 속도를 크게 높일 수 있습니다. 컨트롤을 제거할 준비가 되면 `AfxOleUnlockControl`을 호출합니다.

### <a name="example"></a>예제

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>

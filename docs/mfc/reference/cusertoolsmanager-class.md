---
description: '자세히 알아보기: CUserToolsManager 클래스'
title: CUserToolsManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: 1c6b3b6ec2912a0093929ac117d878d54ed9757f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344954"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 클래스

응용 프로그램에서 [Cusertool 클래스](../../mfc/reference/cusertool-class.md) 개체의 컬렉션을 유지 관리 합니다. 사용자 도구는 외부 애플리케이션을 실행하는 메뉴 항목입니다. `CUserToolsManager` 개체를 사용하면 사용자 또는 개발자가 응용 프로그램에 새 사용자 도구를 추가할 수 있습니다. 사용자 도구와 연결된 명령 실행을 지원하고 사용자 도구에 관한 정보를 Windows 레지스트리를 저장합니다.

## <a name="syntax"></a>구문

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|`CUserToolsManager`를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|새 사용자 도구를 만듭니다.|
|[CUserToolsManager:: FindTool](#findtool)|`CMFCUserTool`지정 된 명령 ID와 연결 된 개체에 대 한 포인터를 반환 합니다.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|**사용자 지정** 대화 상자의 **도구** 탭에 있는 **인수** 메뉴와 연결 된 리소스 ID를 반환 합니다.|
|[CUserToolsManager:: GetDefExt](#getdefext)|**파일 열기** 대화 상자 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 기본 확장명을 반환 합니다.|
|[CUserToolsManager:: GetFilter](#getfilter)|**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 파일 필터를 반환 합니다.|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|**사용자 지정** 대화 상자의 **도구** 탭에 있는 **초기 디렉터리** 메뉴와 연결 된 리소스 ID를 반환 합니다.|
|[CUserToolsManager:: GetMaxTools](#getmaxtools)|응용 프로그램에 할당 될 수 있는 최대 사용자 도구 수를 반환 합니다.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|사용자 도구에 대 한 메뉴 항목 자리 표시자의 명령 ID를 반환 합니다.|
|[CUserToolsManager::GetUserTools](#getusertools)|사용자 도구 목록에 대 한 참조를 반환 합니다.|
|[CUserToolsManager::InvokeTool](#invoketool)|지정 된 명령 ID를 가진 사용자 도구와 연결 된 응용 프로그램을 실행 합니다.|
|[CUserToolsManager:: IsUserToolCmd](#isusertoolcmd)|명령 ID가 사용자 도구와 연결 되어 있는지 여부를 확인 합니다.|
|[CUserToolsManager:: LoadState](#loadstate)|Windows 레지스트리에서 사용자 도구에 대 한 정보를 로드 합니다.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|지정 된 사용자 도구를 사용자 도구 목록에서 아래로 이동 합니다.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|지정 된 사용자 도구를 사용자 도구 목록에서 위로 이동 합니다.|
|[CUserToolsManager::RemoveTool](#removetool)|응용 프로그램에서 지정 된 사용자 도구를 제거 합니다.|
|[CUserToolsManager:: SaveState](#savestate)|사용자 도구에 대 한 정보를 Windows 레지스트리에 저장 합니다.|
|[CUserToolsManager:: SetDefExt](#setdefext)|**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 기본 확장명을 지정 합니다.|
|[CUserToolsManager::SetFilter](#setfilter)|**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 파일 필터를 지정 합니다.|

## <a name="remarks"></a>설명

응용 프로그램에 사용자 도구를 통합 하려면 다음을 수행 해야 합니다.

1. 사용자 도구 메뉴 항목에 대 한 메뉴 항목 및 연결 된 명령 ID를 예약 합니다.

2. 사용자가 응용 프로그램에서 정의할 수 있는 각 사용자 도구에 대해 순차적 명령 ID를 예약 합니다.

3. [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 메서드를 호출 하 고 메뉴 명령 id, 첫 번째 사용자 도구 명령 id 및 마지막 사용자 도구 명령 id와 같은 매개 변수를 제공 합니다.

응용 프로그램당 전역 개체가 하나만 있어야 합니다 `CUserToolsManager` .

사용자 도구에 대 한 예제는 VisualStudioDemo 샘플 프로젝트를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 개체에 대 한 참조를 검색 하는 방법과 `CUserToolsManager` 새로운 사용자 도구를 만드는 방법을 보여 줍니다. 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxusertoolsmanager

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a> CUserToolsManager::CreateNewTool

새 사용자 도구를 만듭니다.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>반환 값

새로 만든 사용자 도구에 대 한 포인터 이거나 사용자 도구 수가 최대값을 초과 하는 경우 NULL입니다. 반환 된 형식은 `CWinAppEx::EnableUserTools` *Ptoolrtc* 매개 변수로에 전달 되는 형식과 동일 합니다.

### <a name="remarks"></a>설명

이 메서드는 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 에 대 한 호출에 제공 된 범위에서 사용 가능한 첫 번째 메뉴 명령 id를 찾고 사용자 도구에이 id를 할당 합니다.

도구 수가 최대값에 도달 하면 메서드가 실패 합니다. 이는 범위 내의 모든 명령 Id가 사용자 도구에 할당 될 때 발생 합니다. [CUserToolsManager:: GetMaxTools](#getmaxtools)를 호출 하 여 최대 도구 수를 검색할 수 있습니다. [CUserToolsManager:: GetUserTools](#getusertools) 메서드를 호출 하 여 도구 목록에 액세스할 수 있습니다.

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a> CUserToolsManager::CUserToolsManager

`CUserToolsManager`를 생성합니다. 각 응용 프로그램에는 사용자 도구 관리자가 하나만 있어야 합니다.

```
CUserToolsManager();

CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>매개 변수

*uiCmdToolsDummy*<br/>
진행 프레임 워크에서 사용자 도구 메뉴의 명령 ID에 대 한 자리 표시자로 사용 하는 부호 없는 정수입니다.

*uiCmdFirst*<br/>
진행 첫 번째 사용자 도구 명령의 명령 ID입니다.

*uiCmdLast*<br/>
진행 Last user tool 명령의 명령 ID입니다.

*pToolRTC*<br/>
진행 [CUserToolsManager:: CreateNewTool](#createnewtool) 가 만드는 클래스입니다. 이 클래스를 사용 하 여 기본 구현 대신 [Cusertool 클래스](../../mfc/reference/cusertool-class.md) 의 파생 된 형식을 사용할 수 있습니다.

*uArgMenuID*<br/>
진행 인수 팝업 메뉴의 메뉴 리소스 ID입니다.

*uInitDirMenuID*<br/>
진행 초기 디렉터리 팝업 메뉴의 메뉴 리소스 ID입니다.

### <a name="remarks"></a>설명

이 생성자를 호출 하지 마세요. 대신 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 를 호출 하 여 사용자 도구를 사용 하도록 설정 하 고 [CWinAppEx:: GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) 를 호출 하 여에 대 한 포인터를 가져옵니다 `CUserToolsManager` . 자세한 내용은 [사용자 정의 도구](../../mfc/user-defined-tools.md)를 참조 하세요.

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a> CUserToolsManager:: FindTool

지정 된 명령 ID와 연결 된 [Cusertool 클래스](../../mfc/reference/cusertool-class.md) 개체에 대 한 포인터를 반환 합니다.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>매개 변수

*uiCmdId*<br/>
진행 메뉴 명령 식별자입니다.

### <a name="return-value"></a>반환 값

성공 하면 [Cusertool 클래스](../../mfc/reference/cusertool-class.md) 또는 파생 개체에 대 한 포인터 `CUserTool` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`FindTool`이 성공 하면 반환 된 형식이 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)에 대 한 *ptoolrtc* 매개 변수의 형식과 동일 합니다.

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a> CUserToolsManager::GetArgumentsMenuID

**사용자 지정** 대화 상자의 **도구** 탭에 있는 **인수** 메뉴와 연결 된 리소스 ID를 반환 합니다.

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>반환 값

메뉴 리소스의 식별자입니다.

### <a name="remarks"></a>설명

[CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 의 *uArgMenuID* 매개 변수는 리소스의 ID를 지정 합니다.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a> CUserToolsManager:: GetDefExt

**파일 열기** 대화 상자 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 기본 확장명을 반환 합니다.

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>반환 값

`CString`확장을 포함 하는 개체에 대 한 참조입니다.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a> CUserToolsManager:: GetFilter

**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 파일 필터를 반환 합니다.

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>반환 값

필터를 포함 하는 개체에 대 한 참조입니다 `CString` .

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a> CUserToolsManager::GetInitialDirMenuID

**사용자 지정** 대화 상자의 **도구** 탭에 있는 **초기 디렉터리** 메뉴와 연결 된 리소스 ID를 반환 합니다.

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>반환 값

메뉴 리소스 식별자입니다.

### <a name="remarks"></a>설명

반환 된 ID는 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)의 *uInitDirMenuID* 매개 변수에 지정 됩니다.

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a> CUserToolsManager:: GetMaxTools

응용 프로그램에 할당 될 수 있는 최대 사용자 도구 수를 반환 합니다.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>반환 값

할당할 수 있는 최대 사용자 도구 수입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 할당할 수 있는 최대 도구 수를 검색 하려면이 메서드를 호출 합니다. 이 숫자는 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)에 전달 하는 *Uicmdfirst* 매개 변수를 통한 *Uicmdfirst* 범위의 id 수입니다.

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a> CUserToolsManager::GetToolsEntryCmd

사용자 도구에 대 한 메뉴 항목 자리 표시자의 명령 ID를 반환 합니다.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>반환 값

자리 표시자의 명령 ID입니다.

### <a name="remarks"></a>설명

사용자 도구를 사용 하도록 설정 하려면 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)를 호출 합니다. *UiCmdToolsDummy* 매개 변수는 tools entry 명령의 명령 ID를 지정 합니다. 이 메서드는 도구 항목 명령 ID를 반환 합니다. 메뉴에서 해당 ID가 사용 되는 경우에는 메뉴가 나타날 때 사용자 도구 목록으로 대체 됩니다.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a> CUserToolsManager::GetUserTools

사용자 도구 목록에 대 한 참조를 반환 합니다.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>반환 값

사용자 도구 목록이 포함 된 [CObList 클래스](../../mfc/reference/coblist-class.md) 개체에 대 한 const 참조입니다.

### <a name="remarks"></a>설명

[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) 개체가 유지 관리 하는 사용자 도구 목록을 검색 하려면이 메서드를 호출 합니다. 각 사용자 도구는 [Cusertool 클래스](../../mfc/reference/cusertool-class.md) 형식의 개체 또는에서 파생 된 형식으로 표시 됩니다 `CUserTool` . 이 형식은 [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 를 호출 하 여 사용자 도구를 사용 하도록 설정 하는 경우 *ptoolrtc* 매개 변수로 지정 됩니다.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a> CUserToolsManager::InvokeTool

지정 된 명령 ID를 가진 사용자 도구와 연결 된 응용 프로그램을 실행 합니다.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>매개 변수

*uiCmdId*<br/>
진행 사용자 도구와 연결 된 메뉴 명령 ID입니다.

### <a name="return-value"></a>반환 값

사용자 도구와 연결 된 명령이 성공적으로 실행 되 면 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Uicmdid* 로 지정 된 명령 ID를 가진 사용자 도구와 연결 된 응용 프로그램을 실행 하려면이 메서드를 호출 합니다.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a> CUserToolsManager:: IsUserToolCmd

명령 ID가 사용자 도구와 연결 되어 있는지 여부를 확인 합니다.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>매개 변수

*uiCmdId*<br/>
진행 메뉴 항목의 명령 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령 ID가 사용자 도구와 연결 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 명령 ID가 명령 ID 범위에 있는지 여부를 확인 합니다. [CWinAppEx:: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) 를 호출할 때 범위를 지정 하 여 사용자 도구를 사용 하도록 설정 합니다.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a> CUserToolsManager:: LoadState

Windows 레지스트리에서 사용자 도구에 대 한 정보를 로드 합니다.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 Windows 레지스트리 키의 경로입니다.

### <a name="return-value"></a>반환 값

상태가 성공적으로 로드 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows 레지스트리에서 개체의 상태를 로드 `CUserToolsManager` 합니다.

일반적으로이 메서드는 직접 호출 하지 않습니다. [CWinAppEx:: LoadState](../../mfc/reference/cwinappex-class.md#loadstate) 는이를 작업 영역 초기화 프로세스의 일부로 호출 합니다.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a> CUserToolsManager::MoveToolDown

지정 된 사용자 도구를 사용자 도구 목록에서 아래로 이동 합니다.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>매개 변수

*pTool*<br/>
진행 이동할 사용자 도구를 지정 합니다.

### <a name="return-value"></a>반환 값

사용자 도구를 성공적으로 아래로 이동 했으면 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Ptool* 에서 지정 하는 도구가 내부 목록에 없거나 목록에서 해당 도구가 마지막에 있는 경우 메서드가 실패 합니다.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a> CUserToolsManager::MoveToolUp

지정 된 사용자 도구를 사용자 도구 목록에서 위로 이동 합니다.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>매개 변수

*pTool*<br/>
진행 이동할 사용자 도구를 지정 합니다.

### <a name="return-value"></a>반환 값

사용자 도구가 성공적으로 이동 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Ptool* 매개 변수가 지정 하는 도구가 내부 목록에 없거나 도구가 목록의 첫 번째 도구 항목인 경우 메서드가 실패 합니다.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a> CUserToolsManager::RemoveTool

응용 프로그램에서 지정 된 사용자 도구를 제거 합니다.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>매개 변수

*pTool*<br/>
[in, out] 제거할 사용자 도구에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

도구가 성공적으로 제거 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

도구가 성공적으로 제거 되 면이 메서드는 *Ptool* 을 삭제 합니다.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a> CUserToolsManager:: SaveState

사용자 도구에 대 한 정보를 Windows 레지스트리에 저장 합니다.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 Windows 레지스트리 키에 대 한 경로입니다.

### <a name="return-value"></a>반환 값

상태가 성공적으로 저장 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메서드는 개체의 현재 상태를 `CUserToolsManager` Windows 레지스트리에 저장 합니다.

일반적으로이 메서드를 직접 호출 하지 않아도 되며, [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate) 는 응용 프로그램의 작업 영역 serialization 프로세스의 일부로 자동으로 호출 합니다.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a> CUserToolsManager:: SetDefExt

**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 기본 확장명을 지정 합니다.

```cpp
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>매개 변수

*strDefExt*<br/>
진행 기본 파일 이름 확장명을 포함 하는 텍스트 문자열입니다.

### <a name="remarks"></a>설명

사용자가 사용자 도구와 연결할 응용 프로그램을 선택할 때 표시 되는 **파일 열기** 대화 상자에서 기본 파일 이름 확장명을 지정 하려면이 메서드를 호출 합니다. 기본값은 "exe"입니다.

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a> CUserToolsManager::SetFilter

**파일 열기** 대화 상자 ( [CFileDialog 클래스](../../mfc/reference/cfiledialog-class.md))가 **사용자 지정** 대화 상자의 **도구** 탭에 있는 **명령** 필드에서 사용 하는 파일 필터를 지정 합니다.

```cpp
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>매개 변수

*strFilter*<br/>
진행 필터를 지정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool 클래스](../../mfc/reference/cusertool-class.md)

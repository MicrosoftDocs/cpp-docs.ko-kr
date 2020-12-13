---
description: '자세히 알아보기: CMouseManager 클래스'
title: CMouseManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: 9816583aa9d05b76f97f1be1487898b5827fbcae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331553"
---
# <a name="cmousemanager-class"></a>CMouseManager 클래스

사용자가 해당 뷰 내에서 두 번 클릭할 때 다른 명령을 특정 [CView](../../mfc/reference/cview-class.md) 개체와 연결할 수 있습니다.

## <a name="syntax"></a>구문

```
class CMouseManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMouseManager:: AddView](#addview)|`CView` **사용자 지정** 대화 상자에 개체를 추가 합니다. 사용자 **지정** 대화 상자를 사용 하면 나열 된 각 뷰에 대해 두 번 클릭을 명령과 연결할 수 있습니다.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|사용자가 제공 된 뷰 내에서 두 번 클릭할 때 실행 되는 명령을 반환 합니다.|
|[CMouseManager:: GetViewIconId](#getviewiconid)|제공 된 뷰 ID와 연결 된 아이콘을 반환 합니다.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|제공 된 뷰 이름과 연결 된 뷰 ID를 반환 합니다.|
|[CMouseManager:: GetViewNames](#getviewnames)|추가 된 모든 뷰 이름 목록을 검색 합니다.|
|[CMouseManager:: LoadState](#loadstate)|`CMouseManager`Windows 레지스트리에서 상태를 로드 합니다.|
|[CMouseManager:: SaveState](#savestate)|`CMouseManager`Windows 레지스트리에 상태를 씁니다.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|제공 된 명령과 제공 된 뷰를 연결 합니다.|

## <a name="remarks"></a>설명

`CMouseManager`클래스는 개체의 컬렉션을 유지 관리 합니다 `CView` . 각 보기는 이름 및 ID로 식별 됩니다. 이러한 보기는 **사용자 지정** 대화 상자에 표시 됩니다. 사용자는 사용자 **지정** 대화 상자를 통해 뷰와 연결 된 명령을 변경할 수 있습니다. 사용자가 해당 뷰를 두 번 클릭 하면 연결 된 명령이 실행 됩니다. 코딩 관점에서이를 지원 하려면 WM_LBUTTONDBLCLK 메시지를 처리 하 고 해당 개체에 대 한 코드에서 [CWinAppEx:: OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) 함수를 호출 해야 합니다. `CView`

개체를 수동으로 만들지 마십시오 `CMouseManager` . 응용 프로그램의 프레임 워크에 의해 생성 됩니다. 사용자가 응용 프로그램을 종료 하는 경우에도 자동으로 제거 됩니다. 응용 프로그램에 대 한 마우스 관리자에 대 한 포인터를 가져오려면 [CWinAppEx:: GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)를 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxmousemanager

## <a name="cmousemanageraddview"></a><a name="addview"></a> CMouseManager:: AddView

사용자 지정 마우스 동작을 지원 하기 위해 [CMouseManager 클래스](../../mfc/reference/cmousemanager-class.md) 를 사용 하 여 [CView](../../mfc/reference/cview-class.md) 개체를 등록 합니다.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>매개 변수

*iViewId*<br/>
진행 뷰 ID입니다.

*uiViewNameResId*<br/>
진행 뷰 이름을 참조 하는 리소스 문자열 ID입니다.

*uiIconId*<br/>
진행 보기 아이콘 ID입니다.

*iId*<br/>
진행 뷰 ID입니다.

*lpszViewName*<br/>
진행 보기 이름입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자 지정 마우스 동작을 지원 하기 위해 뷰를 개체에 등록 해야 합니다 `CMouseManager` . 클래스에서 파생 된 개체는 `CView` 마우스 관리자를 사용 하 여 등록할 수 있습니다. 보기와 연결 된 문자열과 아이콘은 **사용자 지정** 대화 상자의 **마우스** 탭에 표시 됩니다.

*IViewId* 및 *iId* 와 같은 뷰 id를 만들고 유지 관리 하는 것은 프로그래머의 책임입니다.

사용자 지정 마우스 동작을 제공 하는 방법에 대 한 자세한 내용은 [키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)을 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 `CMouseManager` `CWinAppEx::GetMouseManager` 클래스의 메서드 및 메서드를 사용 하 여 개체에 대 한 포인터를 검색 하는 방법을 보여 줍니다 `AddView` `CMouseManager` . 이 코드 조각은 [상태 컬렉션 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a> CMouseManager::GetViewDblClickCommand

사용자가 제공 된 뷰 내에서 두 번 클릭할 때 실행 되는 명령을 반환 합니다.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>매개 변수

*iId*<br/>
진행 뷰 ID입니다.

### <a name="return-value"></a>반환 값

뷰가 명령과 연결 된 경우 명령 식별자입니다. 그렇지 않으면 0입니다.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a> CMouseManager:: GetViewIconId

뷰 ID와 연결 된 아이콘을 검색 합니다.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>매개 변수

*iViewId*<br/>
진행 뷰 ID입니다.

### <a name="return-value"></a>반환 값

성공 하면 아이콘 리소스 식별자입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CMouseManager:: AddView](#addview)를 사용 하 여 뷰가 먼저 등록 되지 않은 경우이 메서드는 실패 합니다.

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a> CMouseManager::GetViewIdByName

뷰 이름과 연결 된 뷰 ID를 검색 합니다.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 뷰 이름입니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 보기 ID 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 [CMouseManager:: AddView](#addview)를 사용 하 여 등록 된 뷰를 검색 합니다.

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a> CMouseManager:: GetViewNames

등록 된 모든 뷰 이름의 목록을 검색 합니다.

```cpp
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>매개 변수

*listOfNames*<br/>
제한이 개체에 대 한 참조 `CStringList` 입니다.

### <a name="remarks"></a>설명

이 메서드는 `listOfNames` [CMouseManager:: addview](#addview)를 사용 하 여 등록 된 모든 뷰의 이름으로 매개 변수를 채웁니다.

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a> CMouseManager:: LoadState

레지스트리에서 [CMouseManager 클래스](../../mfc/reference/cmousemanager-class.md) 의 상태를 로드 합니다.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 레지스트리 키의 경로입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레지스트리에서 로드 되는 상태 정보에는 등록 된 뷰, 뷰 식별자 및 관련 명령이 포함 됩니다. *LpszProfileName* 매개 변수가 NULL 인 경우이 함수는 `CMouseManager` [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)에 의해 제어 되는 기본 레지스트리 위치에서 데이터를 로드 합니다.

대부분의 경우이 함수를 직접 호출할 필요가 없습니다. 작업 영역 초기화 프로세스의 일부로 호출 됩니다. 작업 영역 초기화 프로세스에 대 한 자세한 내용은 [CWinAppEx:: LoadState](../../mfc/reference/cwinappex-class.md#loadstate)를 참조 하세요.

## <a name="cmousemanagersavestate"></a><a name="savestate"></a> CMouseManager:: SaveState

[CMouseManager 클래스](../../mfc/reference/cmousemanager-class.md) 의 상태를 레지스트리에 씁니다.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 레지스트리 키의 경로입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레지스트리에 기록 된 상태 정보에는 등록 된 보기, 뷰 식별자 및 관련 명령이 모두 포함 됩니다. *LpszProfileName* 매개 변수가 NULL 인 경우이 함수는 `CMouseManager` [CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)에 의해 제어 되는 기본 레지스트리 위치에 데이터를 씁니다.

대부분의 경우이 함수를 직접 호출할 필요가 없습니다. 작업 영역 serialization 프로세스의 일부로 호출 됩니다. 작업 영역 serialization 프로세스에 대 한 자세한 내용은 [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate)를 참조 하세요.

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a> CMouseManager::SetCommandForDblClk

사용자 지정 명령을 마우스 관리자에 처음 등록 된 뷰와 연결 합니다.

```cpp
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*iViewId*<br/>
진행 뷰 식별자입니다.

*uiCmd*<br/>
진행 명령 식별자입니다.

### <a name="remarks"></a>설명

사용자 지정 명령을 뷰와 연결 하려면 먼저 [CMouseManager:: AddView](#addview)를 사용 하 여 뷰를 등록 해야 합니다. `AddView`메서드에는 입력 매개 변수로 보기 식별자가 필요 합니다. 뷰를 등록 한 후 `CMouseManager::SetCommandForDblClk` 에는에 제공한 것과 동일한 뷰 식별자 입력 매개 변수를 사용 하 여를 호출할 수 있습니다 `AddView` . 이후에 사용자가 등록 된 뷰에서 마우스를 두 번 클릭 하면 응용 프로그램에서 *Uicmd* 로 표시 되는 명령을 실행 합니다. 사용자 지정 마우스 동작을 지원 하려면 마우스 관리자를 사용 하 여 등록 된 보기도 사용자 지정 해야 합니다. 사용자 지정 마우스 동작에 대 한 자세한 내용은 [키보드 및 마우스 사용자 지정](../keyboard-and-mouse-customization.md)을 참조 하세요.

*Uicmd* 를 0으로 설정 하면 지정 된 뷰가 더 이상 명령과 연결 되지 않습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)<br/>
[키보드 및 마우스 사용자 지정](../../mfc/keyboard-and-mouse-customization.md)

---
description: '자세히 알아보기: CSnapInItemImpl 클래스'
title: CSnapInItemImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: c1c63f5b60d57743087bffde214d9b8addef5b8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140558"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 클래스

이 클래스는 스냅인 노드 개체를 구현 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `CSnapInItemImpl` 입니다.

*Bi이상 압력*<br/>
개체가 스냅인 확장인 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|상황에 맞는 메뉴에 메뉴 항목을 추가 합니다.|
|[CSnapInItemImpl:: Command](#command)|사용자 지정 메뉴 항목이 선택 될 때 콘솔에서 호출 됩니다.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|스냅인의 속성 시트에 페이지를 추가 합니다.|
|[CSnapInItemImpl:: FillData](#filldata)|스냅인 개체의 정보를 지정 된 스트림에 복사 합니다.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|`RESULTDATAITEM`스냅인의 구조를 검색 합니다.|
|[CSnapInItemImpl:: GetResultViewType](#getresultviewtype)|결과 창에서 사용 하는 뷰의 유형을 결정 합니다.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|`SCOPEDATAITEM`스냅인의 구조를 검색 합니다.|
|[CSnapInItemImpl:: Notify](#notify)|사용자가 수행 하는 작업의 스냅인에 알리기 위해 콘솔에서 호출 됩니다.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|스냅인 노드가 속성 페이지를 지원 하는지 여부를 확인 하기 위해 호출 됩니다.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|스냅인 개체의 메뉴 삽입 플래그를 수정 합니다.|
|[CSnapInItemImpl:: Set Buttoninfo](#settoolbarbuttoninfo)|지정 된 도구 모음 단추의 정보를 설정 합니다.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|상황에 맞는 메뉴 항목의 상태를 업데이트 합니다.|
|[CSnapInItemImpl:: Updatetool바 단추](#updatetoolbarbutton)|지정 된 도구 모음 단추의 상태를 업데이트 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSnapInItemImpl:: m_bstrDisplayName](#m_bstrdisplayname)|스냅인 개체의 이름입니다.|
|[CSnapInItemImpl:: m_resultDataItem](#m_resultdataitem)|`RESULTDATAITEM`개체에서 사용 하는 Windows 구조체 `CSnapInItemImpl` 입니다.|
|[CSnapInItemImpl:: m_scopeDataItem](#m_scopedataitem)|`SCOPEDATAITEM`개체에서 사용 하는 Windows 구조체 `CSnapInItemImpl` 입니다.|

## <a name="remarks"></a>설명

`CSnapInItemImpl` 메뉴 항목 및 도구 모음을 추가 하 고 스냅인 노드에 대 한 명령을 적절 한 처리기 함수에 전달 하는 등의 스냅인 노드 개체에 대 한 기본 구현을 제공 합니다. 이러한 기능은 다양 한 인터페이스 및 맵 형식을 사용 하 여 구현 됩니다. 기본 구현은 파생 클래스의 올바른 인스턴스를 확인 한 다음 올바른 인스턴스로 메시지를 전달 하 여 node 개체로 전송 된 알림을 처리 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 고 대/스냅. h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a> CSnapInItemImpl::AddMenuItems

이 메서드는 Win32 함수 [IExtendContextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)를 구현 합니다.

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>매개 변수

*piCallback*<br/>
진행 `IContextMenuCallback` 상황에 맞는 메뉴에 항목을 추가할 수 있는에 대 한 포인터입니다.

*pInsertionAllowed*<br/>
[in, out] 사용할 수 있는 MMC (Microsoft Management Console) 정의 메뉴 항목 삽입 지점을 식별 합니다. 다음 플래그를 조합 하 여 사용할 수 있습니다.

- 상황에 맞는 메뉴의 맨 위에 CCM_INSERTIONALLOWED_TOP 항목을 삽입할 수 있습니다.

- CCM_INSERTIONALLOWED_NEW 항목은 새로 만들기 하위 메뉴에 삽입할 수 있습니다.

- 작업 하위 메뉴에 CCM_INSERTIONALLOWED_TASK 항목을 삽입할 수 있습니다.

- CCM_INSERTIONALLOWED_VIEW 항목은 도구 모음 보기 메뉴 또는 결과 창 상황에 맞는 메뉴의 보기 하위 메뉴에 삽입할 수 있습니다.

*type*<br/>
진행 개체의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- 범위 창 컨텍스트에 대 한 CCT_SCOPE 데이터 개체입니다.

- 결과 창 컨텍스트에 대 한 데이터 개체를 CCT_RESULT 합니다.

- 스냅인 관리자 컨텍스트에 대 한 CCT_SNAPIN_MANAGER 데이터 개체입니다.

- CCT_UNINITIALIZED 데이터 개체의 형식이 잘못 되었습니다.

## <a name="csnapinitemimplcommand"></a><a name="command"></a> CSnapInItemImpl:: Command

이 메서드는 Win32 함수 [IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)를 구현 합니다.

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>매개 변수

*lCommandID*<br/>
진행 메뉴 항목의 명령 식별자를 지정 합니다.

*type*<br/>
진행 개체의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- 범위 창 컨텍스트에 대 한 CCT_SCOPE 데이터 개체입니다.

- 결과 창 컨텍스트에 대 한 데이터 개체를 CCT_RESULT 합니다.

- 스냅인 관리자 컨텍스트에 대 한 CCT_SNAPIN_MANAGER 데이터 개체입니다.

- CCT_UNINITIALIZED 데이터 개체의 형식이 잘못 되었습니다.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a> CSnapInItemImpl::CreatePropertyPages

이 메서드는 Win32 함수 [IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)를 구현 합니다.

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>매개 변수

*lpProvider*<br/>
진행 인터페이스에 대 한 포인터 `IPropertySheetCallback` 입니다.

*처리*<br/>
진행 MMCN_PROPERTY_CHANGE 알림 메시지를 적절 한 데이터 클래스로 라우팅하는 데 사용 되는 핸들을 지정 합니다.

*pUnk*<br/>
진행 `IExtendPropertySheet` 노드에 대 한 컨텍스트 정보를 포함 하는 개체의 인터페이스에 대 한 포인터입니다.

*type*<br/>
진행 개체의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- 범위 창 컨텍스트에 대 한 CCT_SCOPE 데이터 개체입니다.

- 결과 창 컨텍스트에 대 한 데이터 개체를 CCT_RESULT 합니다.

- 스냅인 관리자 컨텍스트에 대 한 CCT_SNAPIN_MANAGER 데이터 개체입니다.

- CCT_UNINITIALIZED 데이터 개체의 형식이 잘못 되었습니다.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a> CSnapInItemImpl::CSnapInItemImpl

`CSnapInItemImpl` 개체를 생성합니다.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a> CSnapInItemImpl:: FillData

이 함수는 항목에 대 한 정보를 검색 하기 위해 호출 됩니다.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>매개 변수

*f*<br/>
진행 클립보드의 서식 (텍스트, 서식 있는 텍스트 또는 OLE 항목의 서식 있는 텍스트)입니다.

*pStream*<br/>
진행 개체 데이터를 포함 하는 스트림에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수를 올바르게 구현 하려면 *cf* 로 표시 된 클립보드 형식에 따라 올바른 정보를 스트림 (*pstream*)에 복사 합니다.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a> CSnapInItemImpl:: GetResultViewType

스냅인 개체의 결과 창에 대 한 뷰 형식을 검색 하려면이 함수를 호출 합니다.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>매개 변수

*ppViewType*<br/>
제한이 반환 된 뷰 형식의 주소에 대 한 포인터입니다.

*pViewOptions*<br/>
제한이 소유 하는 스냅인에서 지정한 옵션을 콘솔에 제공 하는 MMC_VIEW_OPTIONS 열거형에 대 한 포인터입니다. 이 값은 다음 중 하나일 수 있습니다.

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001은 보기 메뉴에 표준 목록 보기 선택을 **표시** 하지 않도록 콘솔에 지시 합니다. 스냅인을 사용 하 여 결과 뷰 창에만 고유한 사용자 지정 보기를 표시할 수 있습니다. 이 플래그는 현재 정의 된 유일한 옵션 플래그입니다.

- MMC_VIEW_OPTIONS_NONE = 0은 기본 뷰 옵션을 허용 합니다.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a> CSnapInItemImpl::GetScopePaneInfo

스냅인의 구조를 검색 하려면이 함수를 호출 `SCOPEDATAITEM` 합니다.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>매개 변수

*pScopeDataItem*<br/>
제한이 `SCOPEDATAITEM` 개체의 구조에 대 한 포인터 `CSnapInItemImpl` 입니다.

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a> CSnapInItemImpl::GetResultPaneInfo

스냅인의 구조를 검색 하려면이 함수를 호출 `RESULTDATAITEM` 합니다.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>매개 변수

*pResultDataItem*<br/>
제한이 `RESULTDATAITEM` 개체의 구조에 대 한 포인터 `CSnapInItemImpl` 입니다.

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a> CSnapInItemImpl:: m_bstrDisplayName

노드 항목에 대해 표시 되는 문자열을 포함 합니다.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a> CSnapInItemImpl:: m_scopeDataItem

`SCOPEDATAITEM`스냅인 데이터 개체의 구조입니다.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a> CSnapInItemImpl:: m_resultDataItem

스냅인 데이터 개체의 [Resultdataitem](/windows/win32/api/mmc/ns-mmc-resultdataitem) 구조체입니다.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a> CSnapInItemImpl:: Notify

사용자가 스냅인 개체를 사용 하 여 작업할 때 호출 됩니다.

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>매개 변수

*event*<br/>
진행 사용자가 수행 하는 작업을 식별 합니다. 다음과 같은 알림이 가능 합니다.

- 창이 활성화 및 비활성화 될 때 전송 MMCN_ACTIVATE.

- 결과 창에 이미지를 추가 하는 MMCN_ADD_IMAGES 전송 됩니다.

- 사용자가 도구 모음 단추 중 하나를 클릭 하면 MMCN_BTN_CLICK 전송 됩니다.

- 사용자가 목록 보기 항목에서 마우스 단추를 클릭할 때 전송 되는 MMCN_CLICK.

- 사용자가 목록 보기 항목에서 마우스 단추를 두 번 클릭 하면 전송 MMCN_DBLCLICK.

- 개체를 삭제 해야 함을 스냅인에 알리기 위해 MMCN_DELETE 전송 됩니다.

- 폴더를 확장 또는 축소 해야 하는 경우에 MMCN_EXPAND 전송 됩니다.

- 창이 최소화 되거나 최대화 될 때 전송 MMCN_MINIMIZED.

- 스냅인 개체의 뷰가 변경 될 것으로 스냅인 개체를 알리기 위해 전송 MMCN_PROPERTY_CHANGE입니다.

- 지정 된 노드 아래에 추가 된 하위 트리 전체를 스냅인에서 삭제 해야 하는 경우에 MMCN_REMOVE_CHILDREN 전송 됩니다.

- 이름 바꾸기를 처음으로 쿼리 하 고 두 번째를 실행 하 여 이름을 바꿀 MMCN_RENAME.

- 범위 또는 결과 뷰 창의 항목이 선택 될 때 전송 MMCN_SELECT.

- 범위 항목을 처음 선택 하거나 선택 취소 하면 MMCN_SHOW 전송 됩니다.

- 변경이 발생할 때 스냅인이 모든 보기를 업데이트할 수 있는 경우 MMCN_VIEW_CHANGE 전송 됩니다.

*인수가*<br/>
진행 알림 유형에 따라 달라 집니다.

*param*<br/>
진행 알림 유형에 따라 달라 집니다.

*pComponentData*<br/>
제한이 을 구현 하는 개체에 대 한 포인터 `IComponentData` 입니다. 알림이 전달 되 고 있지 않으면이 매개 변수는 NULL입니다 `IComponentData::Notify` .

*pComponent*<br/>
제한이 을 구현 하는 개체에 대 한 포인터 `IComponent` 입니다. 알림이 전달 되 고 있지 않으면이 매개 변수는 NULL입니다 `IComponent::Notify` .

*type*<br/>
진행 개체의 유형을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- 범위 창 컨텍스트에 대 한 CCT_SCOPE 데이터 개체입니다.

- 결과 창 컨텍스트에 대 한 데이터 개체를 CCT_RESULT 합니다.

- 스냅인 관리자 컨텍스트에 대 한 CCT_SNAPIN_MANAGER 데이터 개체입니다.

- CCT_UNINITIALIZED 데이터 개체의 형식이 잘못 되었습니다.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a> CSnapInItemImpl::QueryPagesFor

스냅인 노드가 속성 페이지를 지원 하는지 여부를 확인 하기 위해 호출 됩니다.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a> CSnapInItemImpl::SetMenuInsertionFlags

이 함수를 호출 하 여 *pInsertionAllowed* 에 지정 된 메뉴 삽입 플래그를 스냅인 개체에 대해 수정 합니다.

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>매개 변수

*bBeforeInsertion*<br/>
진행 항목이 상황에 맞는 메뉴에 추가 되기 전에 함수를 호출 해야 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

*pInsertionAllowed*<br/>
[in, out] 사용할 수 있는 MMC (Microsoft Management Console) 정의 메뉴 항목 삽입 지점을 식별 합니다. 다음 플래그를 조합 하 여 사용할 수 있습니다.

- 상황에 맞는 메뉴의 맨 위에 CCM_INSERTIONALLOWED_TOP 항목을 삽입할 수 있습니다.

- CCM_INSERTIONALLOWED_NEW 항목은 새로 만들기 하위 메뉴에 삽입할 수 있습니다.

- 작업 하위 메뉴에 CCM_INSERTIONALLOWED_TASK 항목을 삽입할 수 있습니다.

- CCM_INSERTIONALLOWED_VIEW 항목은 도구 모음 보기 메뉴 또는 결과 창 상황에 맞는 메뉴의 보기 하위 메뉴에 삽입할 수 있습니다.

### <a name="remarks"></a>설명

기본 스냅인을 개발 하는 경우 타사 확장에서 추가할 수 있는 메뉴 항목의 종류를 제한 하는 방법으로 삽입 플래그를 다시 설정할 수 있습니다. 예를 들어 기본 스냅인은 CCM_INSERTIONALLOWED_NEW 플래그를 지워 확장이 자체 새 메뉴 항목 만들기를 추가 하지 못하게 할 수 있습니다.

원래 지워진 *pInsertionAllowed* 에서 비트를 설정 하지 않아야 합니다. 이후 버전의 MMC는 현재 정의 되지 않은 비트를 사용할 수 있으므로 현재 정의 되지 않은 비트를 변경 하면 안 됩니다.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a> CSnapInItemImpl:: Set Buttoninfo

도구 모음이 만들어지기 전에이 함수를 호출 하 여 스냅인 개체의 도구 모음 단추 스타일을 수정 합니다.

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 설정할 도구 모음 단추의 ID입니다.

*fsState*<br/>
진행 단추의 상태 플래그입니다. 다음 중 하나 이상이 될 수 있습니다.

- TBSTATE_CHECKED 단추에 TBSTYLE_CHECKED 스타일이 있으며 눌러져 있습니다.

- 사용자 입력을 허용 하는 단추를 TBSTATE_ENABLED 합니다. 이 상태가 없는 단추는 사용자 입력을 허용 하지 않으며 회색입니다.

- TBSTATE_HIDDEN 단추가 표시 되지 않고 사용자 입력을 받을 수 없습니다.

- 단추가 회색으로 표시 TBSTATE_INDETERMINATE.

- 단추를 누르는 TBSTATE_PRESSED입니다.

- TBSTATE_WRAP 단추 뒤에 줄 바꿈이 있습니다. 단추에도 TBSTATE_ENABLED 있어야 합니다.

*fsType*<br/>
진행 단추의 상태 플래그입니다. 다음 중 하나 이상이 될 수 있습니다.

- TBSTYLE_BUTTON 표준 누름 단추를 만듭니다.

- TBSTYLE_CHECK 사용자가 클릭할 때마다 눌린 상태를 전환 하는 단추를 만듭니다. 단추는 누름 상태일 때 다른 배경색을 가집니다.

- TBSTYLE_CHECKGROUP 그룹의 다른 단추를 누를 때까지 누른 상태를 유지 하는 확인 단추를 만듭니다.

- TBSTYLE_GROUP 그룹의 다른 단추를 누를 때까지 누름 상태를 유지 하는 단추를 만듭니다.

- TBSTYLE_SEP은 단추 그룹 사이에 작은 간격을 제공 하는 구분 기호를 만듭니다. 이 스타일이 있는 단추는 사용자 입력을 수신 하지 않습니다.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a> CSnapInItemImpl::UpdateMenuState

스냅인 개체의 상황에 맞는 메뉴에 삽입 되기 전에 메뉴 항목을 수정 하려면이 함수를 호출 합니다.

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 설정할 메뉴 항목의 ID입니다.

*pBuf*<br/>
진행 업데이트할 메뉴 항목에 대 한 문자열에 대 한 포인터입니다.

*flags*<br/>
진행 새 상태 플래그를 지정 합니다. 다음 플래그를 조합 하 여 사용할 수 있습니다.

- MF_POPUP 상황에 맞는 메뉴 내의 하위 메뉴 임을 지정 합니다. 메뉴 항목, 삽입 지점을 비롯 하 여이 하위 메뉴에는를 사용 하 여이 하위 메뉴가 추가 될 수 있습니다 `lCommandID` `IInsertionPointID` .

- MF_BITMAP 및 MF_OWNERDRAW 이러한 플래그는 허용 되지 않으며 반환 값이 E_INVALIDARG 됩니다.

- MF_SEPARATOR 가로 분할 선을 그립니다. `IContextMenuProvider`MF_SEPARATOR 설정 된 메뉴 항목만 추가할 수 있습니다.

- MF_CHECKED 메뉴 항목 옆에 확인 표시를 배치 합니다.

- 메뉴 항목을 선택할 수 없도록 메뉴 항목을 사용 하지 않도록 설정 하 MF_DISABLED 플래그는 회색으로 표시 하지 않습니다.

- MF_ENABLED 메뉴 항목을 선택 하 여 회색 상태에서 복원할 수 있습니다.

- MF_GRAYED 메뉴 항목을 사용 하지 않도록 설정 합니다. graying 선택할 수 없습니다.

- MF_MENUBARBREAK는 메뉴 모음의 MF_MENUBREAK 플래그와 동일 하 게 작동 합니다. 드롭다운 메뉴, 하위 메뉴 또는 바로 가기 메뉴의 경우 새 열은 수직선으로 이전 열과 구분 됩니다.

- 열을 구분 하지 않고 새 줄 (메뉴 모음의 경우) 이나 새 열 (드롭다운 메뉴, 하위 메뉴 또는 바로 가기 메뉴의 경우)에 항목을 배치 MF_MENUBREAK 합니다.

- MF_UNCHECKED는 항목 옆에 확인 표시를 두지 않습니다 (기본값).

다음 플래그 그룹을 함께 사용할 수 없습니다.

- MF_DISABLED, MF_ENABLED 및 MF_GRAYED.

- MF_MENUBARBREAK 및 MF_MENUBREAK.

- MF_CHECKED 및 MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a> CSnapInItemImpl:: Updatetool바 단추

표시 되기 전에이 함수를 호출 하 여 스냅인 개체의 도구 모음 단추를 수정 합니다.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>매개 변수

*id*<br/>
업데이트할 도구 모음 단추의 단추 ID를 지정 합니다.

*fsState*<br/>
도구 모음 단추 상태를 지정 합니다. 이 상태를 설정 하는 경우 TRUE를 반환 합니다. 다음 플래그를 조합 하 여 사용할 수 있습니다.

- 사용이 단추는 사용자 입력을 허용 합니다. 이 상태가 없는 단추는 사용자 입력을 허용 하지 않으며 회색입니다.

- 선택 된 스타일을 가지 며 단추를 누르는 중임을 확인 합니다.

- 숨김 단추가 표시 되지 않고 사용자 입력을 받을 수 없습니다.

- 비활성화 됨 단추는 회색으로 표시 됩니다.

- BUTTONPRESSED 단추를 눌렀습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)

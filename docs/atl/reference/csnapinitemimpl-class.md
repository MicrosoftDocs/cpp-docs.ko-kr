---
title: CSnapInItemImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1355173bafcf026a7f1bfba771a7769b202c92c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 클래스
이 클래스에 스냅인 노드 개체를 구현 하기 위한 메서드를 제공 합니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 파생 된 클래스에 `CSnapInItemImpl`합니다.  
  
 *bIsExtension*  
 **True 이면** 개체가 스냅인 확장; 그렇지 않으면 **FALSE**합니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|생성자입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|상황에 맞는 메뉴에 메뉴 항목을 추가합니다.|  
|[CSnapInItemImpl::Command](#command)|사용자 지정 메뉴 항목이 선택 될 때 콘솔에서 호출 됩니다.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|스냅인의 속성 시트에 페이지를 추가합니다.|  
|[CSnapInItemImpl::FillData](#filldata)|스냅인 개체에 지정 된 스트림으로 정보를 복사 합니다.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|검색 된 **RESULTDATAITEM** 스냅인의 구조입니다.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|결과 창에서 사용 하는 보기의 유형을 결정 합니다.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|검색 된 **SCOPEDATAITEM** 스냅인의 구조입니다.|  
|[CSnapInItemImpl::Notify](#notify)|사용자가 수행한 작업의 스냅인에 알리기 위해 콘솔에서 호출 됩니다.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|스냅인에서 노드 속성 페이지에서 지원 하는지 확인 하기 위해 호출 합니다.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|스냅인 개체에 대 한 메뉴 삽입 플래그를 수정합니다.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|지정 된 도구 모음 단추 정보를 설정합니다.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|상황에 맞는 메뉴 항목의 상태를 업데이트합니다.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|지정 된 도구 모음 단추의 상태를 업데이트합니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|스냅인 개체의 이름입니다.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows **RESULTDATAITEM** 에서 사용 하는 구조는 `CSnapInItemImpl` 개체입니다.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows **SCOPEDATAITEM** 에서 사용 하는 구조는 `CSnapInItemImpl` 개체입니다.|  
  
## <a name="remarks"></a>설명  
 `CSnapInItemImpl`메뉴 항목 및 도구 모음을 추가 하 고 적절 한 처리기 함수에 스냅인 노드에 대 한 명령을 전달 등의 한 스냅인 노드 개체에 대 한 기본 구현을 제공 합니다. 이 기능은 여러 가지 다른 인터페이스를 사용 하 여 구현 됩니다 있으며 형식을 매핑합니다. 파생된 클래스의 올바른 인스턴스를 확인 하 고 다음 올바른 인스턴스로 메시지를 전달 하 여 노드 개체를 전송 하는 알림을 처리 하는 기본 구현 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlsnap.h  
  
##  <a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems  
 이 메서드는 Win32 함수를 구현 [IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841)합니다.  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>매개 변수  
 *변수인 piCallback*  
 [in] 에 대 한 포인터는 **IContextMenuCallback** 상황에 맞는 메뉴에 항목을 추가할 수 있는 합니다.  
  
 `pInsertionAllowed`  
 [out에서] 식별 MMC Microsoft Management Console 정의 메뉴 항목 삽입 지점을 사용할 수 있는 합니다. 이 다음 플래그의 조합 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_TOP** 상황에 맞는 메뉴 맨 위에 있는 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_NEW** 새로 만들기 하위 메뉴에 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_TASK** 작업 하위 메뉴에 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_VIEW** 결과 창 상황에 맞는 메뉴의 뷰 하위 메뉴 또는 도구 모음 보기 메뉴에 항목을 삽입할 수 있습니다.  
  
 `type`  
 [in] 개체의 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **CCT_SCOPE** 범위 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_RESULT** 결과 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_SNAPIN_MANAGER** 스냅인 관리자 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_UNINITIALIZED** 데이터 개체 유형이 잘못 되었습니다.  
  
##  <a name="command"></a>CSnapInItemImpl::Command  
 이 메서드는 Win32 함수를 구현 [IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842)합니다.  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>매개 변수  
 *lCommandID*  
 [in] 메뉴 항목의 명령 식별자를 지정합니다.  
  
 `type`  
 [in] 개체의 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **CCT_SCOPE** 범위 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_RESULT** 결과 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_SNAPIN_MANAGER** 스냅인 관리자 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_UNINITIALIZED** 데이터 개체 유형이 잘못 되었습니다.  
  
##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages  
 이 메서드는 Win32 함수를 구현 [IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846)합니다.  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>매개 변수  
 *lpProvider*  
 [in] 에 대 한 포인터는 **IPropertySheetCallback** 인터페이스입니다.  
  
 *핸들*  
 [in] 사용 되는 핸들을 지정 하 여 경로로 **MMCN_PROPERTY_CHANGE** 알림 메시지를 적절 한 데이터 클래스.  
  
 *pUnk*  
 [in] 에 대 한 포인터는 **IExtendPropertySheet** 노드에 대 한 컨텍스트 정보를 포함 하는 개체에 대 한 인터페이스입니다.  
  
 `type`  
 [in] 개체의 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **CCT_SCOPE** 범위 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_RESULT** 결과 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_SNAPIN_MANAGER** 스냅인 관리자 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_UNINITIALIZED** 데이터 개체 유형이 잘못 되었습니다.  
  
##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl  
 `CSnapInItemImpl` 개체를 생성합니다.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>CSnapInItemImpl::FillData  
 이 함수는 항목에 대 한 정보를 검색 하 라고 합니다.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>매개 변수  
 `cf`  
 [in] 형식 (텍스트, 서식 있는 텍스트 또는 OLE 항목과 서식 있는 텍스트) 클립보드의입니다.  
  
 `pStream`  
 [in] 개체 데이터를 포함 하는 스트림입니다에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 올바르게 구현 하려면 올바른 정보를 스트림으로 복사 ( `pStream`)에 설정 된 클립보드 형식에 따라 `cf`합니다.  
  
##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType  
 스냅인 개체의 결과 창에 대 한 보기의 유형을 검색 하려면이 함수를 호출 합니다.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>매개 변수  
 *ppViewType*  
 [out] 반환 된 뷰 유형의 주소에 대 한 포인터입니다.  
  
 *pViewOptions*  
 [out] 에 대 한 포인터는 **MMC_VIEW_OPTIONS** 소유 스냅인에서 지정 된 옵션은 콘솔을 제공 하는 열거형입니다. 이 값은 다음 중 하나일 수 있습니다.  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0x00000001 콘솔에서 선택할 수 있는 표준 목록 보기를 표시 하지 않는 것을 지시는 **보기** 메뉴. 스냅인만 결과 뷰 창에서에서 자체 사용자 지정 보기를 표시할 수 있습니다. 이 이번에 정의 된 유일한 옵션 플래그입니다.  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 허용 하는 기본 보기 옵션입니다.  
  
##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo  
 검색 하려면이 함수 호출의 **SCOPEDATAITEM** 스냅인의 구조입니다.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>매개 변수  
 *pScopeDataItem*  
 [out] 에 대 한 포인터는 **SCOPEDATAITEM** 의 구조는 `CSnapInItemImpl` 개체입니다.  
  
##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo  
 검색 하려면이 함수 호출의 **RESULTDATAITEM** 스냅인의 구조입니다.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>매개 변수  
 *pResultDataItem*  
 [out] 에 대 한 포인터는 **RESULTDATAITEM** 의 구조는 `CSnapInItemImpl` 개체입니다.  
  
##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName  
 노드 항목에 대해 표시 되는 문자열을 포함 합니다.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM` 스냅인 데이터 개체의 구조가 있습니다.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165) 스냅인 데이터 개체의 구조입니다.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>CSnapInItemImpl::Notify  
 스냅인 개체는 사용자가 대상이 되는 경우 호출 됩니다.  
  
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
 `event`  
 [in] 사용자가 수행 되는 동작을 식별 합니다. 다음과 같은 알림이 발생할 수 있습니다.  
  
- **MMCN_ACTIVATE** 활성화 및 비활성화 되는 경우 창이 전송 합니다.  
  
- **MMCN_ADD_IMAGES** 이미지를 추가 하려면 결과 창에 전송 합니다.  
  
- **MMCN_BTN_CLICK** 사용자가 도구 모음 단추 중 하나를 클릭할 때 보냅니다.  
  
- **MMCN_CLICK** 목록 보기 항목에 마우스 단추를 클릭할 때 보냅니다.  
  
- **MMCN_DBLCLICK** 목록 보기 항목의 마우스 단추를 두 번 클릭할 때 전송 합니다.  
  
- **MMCN_DELETE** 개체 되어야 하는 스냅인 알리기 위해 전송 삭제 합니다.  
  
- **MMCN_EXPAND** 폴더를 확장 하거나 수축 해야 할 때를 전송 합니다.  
  
- **MMCN_MINIMIZED** 최대화 되거나 최소화 되는 경우 창이 전송 합니다.  
  
- **MMCN_PROPERTY_CHANGE** 스냅인 개체의 보기를 변경 하려고 하는 스냅인 개체를 통보 합니다.  
  
- **MMCN_REMOVE_CHILDREN** 스냅인에 지정 된 노드 아래의 추가 전체 하위 트리를 삭제 해야 하는 경우 전송 합니다.  
  
- **MMCN_RENAME** 이름 바꾸기 작업을 수행 하는 이름 바꾸기에 대 한 쿼리를 처음으로 및 두 번째 시간 전송 합니다.  
  
- **MMCN_SELECT** 범위 또는 결과 뷰 창에서 항목을 선택한 경우 전송 합니다.  
  
- **MMCN_SHOW** 범위 항목을 선택 하거나 처음으로 선택 취소 하는 경우 전송 합니다.  
  
- **MMCN_VIEW_CHANGE** 스냅인 수를 업데이트할 때 모든 뷰는 변경이 발생할 때 전송 합니다.  
  
 `arg`  
 [in] 알림 유형에 따라 다릅니다.  
  
 `param`  
 [in] 알림 유형에 따라 다릅니다.  
  
 *pComponentData*  
 [out] 구현 하는 개체에 대 한 포인터 **IComponentData**합니다. 이 매개 변수는 **NULL** 에서 알림을 전달 되는 경우 **IComponentData::Notify**합니다.  
  
 *pComponent*  
 [out] 구현 하는 개체에 대 한 포인터 **IComponent**합니다. 이 매개 변수는 **NULL** 에서 알림을 전달 되는 경우 **IComponent::Notify**합니다.  
  
 `type`  
 [in] 개체의 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **CCT_SCOPE** 범위 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_RESULT** 결과 창 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_SNAPIN_MANAGER** 스냅인 관리자 컨텍스트에 대 한 데이터 개체입니다.  
  
- **CCT_UNINITIALIZED** 데이터 개체 유형이 잘못 되었습니다.  
  
##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor  
 스냅인에서 노드 속성 페이지에서 지원 하는지 확인 하기 위해 호출 합니다.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags  
 로 지정 된 메뉴 삽입 플래그를 수정 하려면이 함수를 호출 `pInsertionAllowed`, 스냅인 개체에 대 한 합니다.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>매개 변수  
 *bBeforeInsertion*  
 [in] 항목 상황에 맞는 메뉴;에 추가 되기 전에 함수를 호출 해야 하면 0이 아니고 그렇지 않으면 0입니다.  
  
 `pInsertionAllowed`  
 [out에서] 식별 MMC Microsoft Management Console 정의 메뉴 항목 삽입 지점을 사용할 수 있는 합니다. 이 다음 플래그의 조합 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_TOP** 상황에 맞는 메뉴 맨 위에 있는 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_NEW** 새로 만들기 하위 메뉴에 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_TASK** 작업 하위 메뉴에 항목을 삽입할 수 있습니다.  
  
- **CCM_INSERTIONALLOWED_VIEW** 결과 창 상황에 맞는 메뉴의 뷰 하위 메뉴 또는 도구 모음 보기 메뉴에 항목을 삽입할 수 있습니다.  
  
### <a name="remarks"></a>설명  
 기본 스냅인을 개발 하는 경우 공급 업체 확장을 추가할 수 있는 메뉴 항목의 종류를 제한 하는 방법으로 삽입 플래그를 설정할 수 있습니다. 예를 들어 기본 스냅인 지울 수는 **CCM_INSERTIONALLOWED_NEW** 플래그 확장 자신의 새로 만들기 메뉴 항목을 추가 하지 못하도록 합니다.  
  
 비트를 설정 하려고 해서는 안 `pInsertionAllowed` 원래 선택을 취소 하는 합니다. 이후 버전의 MMC 현재 현재 정의 되어 있지 않은 비트를 변경 하지 않아야 하므로 정의 된 비트를 사용할 수 있습니다.  
  
##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo  
 도구 모음을 만들기 전에 스냅인 개체의 모든 도구 모음 단추 스타일을 수정 하려면이 함수를 호출 합니다.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>매개 변수  
 `id`  
 [in] 도구 모음 단추를 설정의 ID입니다.  
  
 `fsState`  
 [in] 단추의 상태 플래그입니다. 다음 중 하나 이상을 하나일 수 있습니다.  
  
- `TBSTATE_CHECKED`단추에는 **TBSTYLE_CHECKED** 눌렀는지 및 스타일 지정 합니다.  
  
- `TBSTATE_ENABLED`단추는 사용자 입력을 허용합니다. 이 상태를 갖지 않는 단추 사용자 입력을 받아들이지 않는 흐리게 표시 됩니다.  
  
- `TBSTATE_HIDDEN`단추가 표시 되지 않으며 사용자 입력을 받을 수 없습니다.  
  
- `TBSTATE_INDETERMINATE`단추가 흐리게 표시 됩니다.  
  
- `TBSTATE_PRESSED`추가 되 고 합니다.  
  
- `TBSTATE_WRAP`줄 바꿈을 단추는 다음과 같습니다. 단추 있어야는 `TBSTATE_ENABLED`합니다.  
  
 *fsType*  
 [in] 단추의 상태 플래그입니다. 다음 중 하나 이상을 하나일 수 있습니다.  
  
- `TBSTYLE_BUTTON`표준 누름 단추를 만듭니다.  
  
- `TBSTYLE_CHECK`단추 누름 또는 not 누른 상태로 될 때마다 사용자가을 설정/해제를 만듭니다. 단추는 눌린 상태로 될 때 다른 배경색을 합니다.  
  
- `TBSTYLE_CHECKGROUP`그룹의 다른 단추를 누를 때까지 누른 상태로 유지 되는 확인 단추를 만듭니다.  
  
- `TBSTYLE_GROUP`그룹의 다른 단추를 누를 때까지 누른 상태로 유지 되는 단추를 만듭니다.  
  
- `TBSTYLE_SEP`단추 그룹 간에 작은 간격을 제공 하는 구분 기호를 만듭니다. 이 스타일 있는 단추는 사용자 입력을 받지 않습니다.  
  
##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState  
 스냅인 개체의 상황에 맞는 메뉴에 삽입 하기 전에 메뉴 항목을 수정 하려면이 함수를 호출 합니다.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>매개 변수  
 `id`  
 [in] 설정할 메뉴 항목의 ID입니다.  
  
 `pBuf`  
 [in] 업데이트할 메뉴 항목에 대 한 문자열에 대 한 포인터입니다.  
  
 `flags`  
 [in] 새 상태 플래그를 지정합니다. 이 다음 플래그의 조합 수 있습니다.  
  
- **MF_POPUP** 상황에 맞는 메뉴 내에서 하위 메뉴 임을 지정 합니다. 메뉴 항목, 삽입 지점 및 추가 하위 메뉴를 사용 하 여이 하위 메뉴에 추가할 수 있습니다는 **lCommandID** 으로 자신의 **IInsertionPointID**합니다.  
  
- **MF_BITMAP** 및 `MF_OWNERDRAW` 이러한 플래그는 사용할 수 없으며 값을 반환 하면 `E_INVALIDARG`합니다.  
  
- **MF_SEPARATOR** 가로 구분선을 그립니다. 만 **IContextMenuProvider** 있는 메뉴 항목을 추가 하도록 허용 된 **MF_SEPARATOR** 설정 합니다.  
  
- **MF_CHECKED** 메뉴 항목 옆에 있는 확인 표시를 배치 합니다.  
  
- **MF_DISABLED** 되므로 선택할 수 없습니다. 그러나이 플래그는 회색 하지 않는 메뉴 항목을 사용 하지 않도록 설정 합니다.  
  
- `MF_ENABLED`선택할 수 있습니다, 회색된 상태에서 복원 되므로 메뉴 항목을 사용할 수 있습니다.  
  
- **MF_GRAYED** 선택할 수 없도록 표시 메뉴 항목을 사용 하지 않도록 설정 합니다.  
  
- **MF_MENUBARBREAK** 동일 하 게 작동는 **MF_MENUBREAK** 메뉴 모음에 대 한 플래그입니다. 드롭 다운 메뉴, 하위 메뉴 또는 바로 가기 메뉴에 대 한 새 열은 이전 행에서 세로 선 구분 됩니다.  
  
- **MF_MENUBREAK** (메뉴 모음)에 대 한 새 줄에 항목을 배치 하거나 열을 구분 하지 (드롭다운 메뉴, 하위 메뉴 또는 바로 가기 메뉴)에 새 열에 있습니다.  
  
- **MF_UNCHECKED** 항목 (기본값) 옆에 있는 확인 표시를 배치 하지 않습니다.  
  
 플래그의 다음 그룹은 함께 사용할 수 없습니다.  
  
- **MF_DISABLED**, `MF_ENABLED`, 및 **MF_GRAYED**합니다.  
  
- **MF_MENUBARBREAK** 및 **MF_MENUBREAK**합니다.  
  
- **MF_CHECKED** 및 **MF_UNCHECKED**합니다.  
  
##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton  
 스냅인 개체의 도구 모음 단추를 표시 하기 전에 수정 하려면이 함수를 호출 합니다.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>매개 변수  
 `id`  
 업데이트할 도구 모음 단추의 단추 ID를 지정 합니다.  
  
 `fsState`  
 도구 모음 단추 상태를 지정합니다. 이 상태를 설정할 경우 반환 **TRUE**합니다. 이 다음 플래그의 조합 수 있습니다.  
  
- **활성화** 단추는 사용자 입력을 허용 합니다. 이 상태를 갖지 않는 단추 사용자 입력을 받아들이지 않는 흐리게 표시 됩니다.  
  
- **확인** 단추에는 **체크** 눌렀는지 및 스타일 지정 합니다.  
  
- **HIDDEN** 단추가 표시 되지 않으며 사용자 입력을 받을 수 없습니다.  
  
- **비활성화 상태** 단추가 흐리게 표시 됩니다.  
  
- **BUTTONPRESSED** 단추를 누를 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../../atl/atl-class-overview.md)

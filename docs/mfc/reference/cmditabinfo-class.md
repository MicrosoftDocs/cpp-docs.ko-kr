---
title: CMDITabInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 30bf7726b35d762be2bbbd119e0303894879cd3d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752654"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo 클래스

클래스는 `CMDITabInfo` [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) 메서드에 매개 변수를 전달하는 데 사용됩니다. MDI 탭 그룹의 동작을 제어하려면 이 클래스의 멤버를 설정합니다.

## <a name="syntax"></a>구문

```
class CMDITabInfo
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CMDITabInfo::직렬화](#serialize)|이 개체를 보관 저장소에서 읽어오거나 보관 저장소에 씁니다.|

### <a name="data-members"></a>데이터 멤버

|속성|Description|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|활성 탭의 레이블에 **닫기** 단추를 표시할지 여부를 지정합니다.|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|MDI 탭의 색상을 지정합니다.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|탭 그룹에 열려 있는 문서 목록을 표시하거나 스크롤 단추를 표시하는 팝업 메뉴가 표시되는지 여부를 지정합니다.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|사용자가 드래그하여 탭의 위치를 바꿀 수 있는지 여부를 지정합니다.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|탭에 플랫 프레임이 있는지 여부를 지정합니다.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|각 탭 레이블에 **닫기** 버튼이 표시되는지 여부를 지정합니다.|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|사용자 지정 도구 설명이 활성화되어 있는지 여부를 지정합니다.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|MDI 탭에 아이콘을 표시할지 여부를 지정합니다.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|각 탭 창의 테두리 크기를 지정합니다.|
|[CMDITabInfo::m_style](#m_style)|탭 레이블의 스타일을 지정합니다.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|탭 레이블이 페이지의 위쪽 또는 아래쪽에 있는지 여부를 지정합니다.|

## <a name="remarks"></a>설명

이 클래스는 프레임워크가 만드는 MDI 탭 그룹의 매개 변수를 지정합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMDITabInfo` 클래스에서 다양 한 멤버 변수의 값을 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;

활성 탭의 레이블에 **닫기** 단추를 표시할지 여부를 지정합니다.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>설명

TRUE이면 활성 탭의 레이블에 **닫기** 버튼이 표시됩니다. **닫기** 버튼은 탭 영역의 오른쪽 상단 모서리에서 제거됩니다. 그렇지 않으면 활성 탭의 레이블에 **닫기** 버튼이 표시되지 않습니다. **닫기** 버튼이 탭 영역의 오른쪽 상단 모서리에 나타납니다.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor

각 MDI 탭에 고유한 색상이 있는지 여부를 지정합니다.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>설명

TRUE인 경우 각 탭에는 고유한 색상이 있습니다. 색상 집합은 MFC 라이브러리에서 관리합니다. 그렇지 않으면 탭이 흰색으로 표시됩니다. 기본값은 FALSE입니다.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu

각 탭에 탭 영역의 오른쪽 가장자리에 열려 있는 문서 목록을 표시 하는 팝업 메뉴가 표시 되는지 여부를 지정 합니다.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>설명

TRUE인 경우 각 탭 창에는 탭 영역의 오른쪽 가장자리에 열린 문서 목록이 표시되는 팝업 메뉴가 표시됩니다. 그렇지 않으면 탭 창에 탭 영역의 오른쪽 가장자리에 스크롤 단추가 표시됩니다. 기본값은 FALSE입니다.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap

사용자가 드래그하여 탭의 위치를 바꿀 수 있는지 여부를 지정합니다.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>설명

TRUE인 경우 사용자는 탭을 드래그하여 탭 위치를 변경할 수 있습니다. 그렇지 않으면 사용자는 탭 위치를 변경할 수 없습니다. 기본값은 TRUE입니다.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame

각 탭 창에 플랫 프레임이 있는지 여부를 지정합니다.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton

각 탭 창에 **닫기** 버튼이 표시되는지 여부를 지정합니다.

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>설명

TRUE이면 각 탭 창에 탭의 오른쪽 가장자리에 **닫기** **Close** 버튼이 표시됩니다. 기본값은 TRUE입니다.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips

탭이 도구 설명끝을 표시할지 여부를 지정합니다.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>설명

TRUE이면 응용 프로그램은 AFX_WM_ON_GET_TAB_TOOLTIP 메시지를 주 프레임으로 보냅니다. ON_REGISTERED_MESSAGE 매크로를 사용하여 이 메시지를 처리할 수 있습니다.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons

MDI 탭에 아이콘을 표시할지 여부를 지정합니다.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>설명

TRUE이면 각 MDI 탭에 아이콘이 표시됩니다. 기본값은 FALSE입니다.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize

각 탭 창의 테두리 크기를 픽셀 단위로 지정합니다.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>설명

[CMFC VisualManager::GetMDITabsBordersSize는](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) 기본값을 반환합니다.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo::m_style

탭 레이블의 스타일을 지정합니다.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>설명

탭 레이블에 대해 다음 스타일 중 하나를 지정합니다.

|||
|-|-|
|STYLE_3D|3D 스타일.  |
|STYLE_3D_ONENOTE|마이크로 소프트 원 노트 스타일.  |
|STYLE_3D_VS2005|마이크로 소프트 비주얼 스튜디오 2005 스타일.  |
|STYLE_3D_SCROLLED|사각형 탭 레이블이 있는 3D 스타일입니다.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|공유 가로 스크롤 막대가있는 플랫 스타일.  |
|STYLE_3D_ROUNDED_SCROLL|둥근 탭 레이블이 있는 3D 스타일입니다.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo::m_tabLocation

탭 레이블이 페이지의 위쪽 또는 아래쪽에 있는지 여부를 지정합니다.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>설명

다음 위치 플래그 중 하나 인 탭에 적용하십시오.

- LOCATION_BOTTOM: 탭 레이블은 페이지 하단에 있습니다.

- LOCATION_TOP: 탭 레이블이 페이지 상단에 있습니다.

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::직렬화

이 개체를 아카이브 또는 아카이브로 읽거나 씁니다.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
【인】 직렬화할 [CArchive 클래스](../../mfc/reference/carchive-class.md) 개체입니다.

## <a name="see-also"></a>참조

[CMDIFrameWndEx 클래스](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 탭 그룹](../../mfc/mdi-tabbed-groups.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)

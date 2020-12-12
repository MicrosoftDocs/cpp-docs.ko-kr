---
description: '자세한 정보: Cmfc리본 Mainpanel 클래스'
title: Cmfc리본 Mainpanel 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: 823a1ce8a8684ca791f838346a1fb50727096a62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321814"
---
# <a name="cmfcribbonmainpanel-class"></a>Cmfc리본 Mainpanel 클래스

[Cmfcribbon Applicationbutton 단추](../../mfc/reference/cmfcribbonapplicationbutton-class.md)를 클릭할 때 표시 되는 리본 패널을 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|기본 생성자입니다.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Mainpanel:: Add](#add)|응용 프로그램 단추 패널의 왼쪽 창에 리본 요소를 추가 합니다. [Cmfc리본 패널:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)를 재정의 합니다.|
|[Cmfc리본 Mainpanel:: AddRecentFilesList](#addrecentfileslist)|최근 파일 목록 메뉴에 텍스트 문자열을 추가 합니다.|
|[Cmfc리본 Mainpanel::가 중 하단](#addtobottom)|리본 응용 프로그램 패널의 아래쪽 창에 리본 요소를 추가 합니다.|
|[Cmfc리본 Mainpanel:: AddToRight](#addtoright)|응용 프로그램 단추 패널의 오른쪽 창에 리본 요소를 추가 합니다.|
|`CMFCRibbonMainPanel::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[Cmfc리본 Mainpanel:: GetCommandsFrame](#getcommandsframe)|리본 주 패널의 영역을 나타내는 사각형을 반환 합니다.|
|`CMFCRibbonMainPanel::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|

## <a name="remarks"></a>설명

`CMFCRibbonMainPanel`응용 프로그램 패널을 열면 프레임 워크가를 표시 합니다. 세 개의 창이 포함 되어 있습니다.

- 왼쪽 창에는 **열기**, **저장**, **인쇄** 및 **닫기** 와 같은 파일과 연결 된 명령이 있습니다. 이 창에 명령을 추가 하려면 [Cmfc리본 Mainpanel:: add](#add)를 호출 합니다.

- 오른쪽 창에는 왼쪽 창에서 클릭 하는 명령을 수정 하는 옵션이 있습니다. 예를 들어 왼쪽 창에서 다른 **이름으로 저장** 을 클릭 하면 오른쪽 창에 사용 가능한 파일 형식이 표시 될 수 있습니다. 이 창에 항목을 추가 하려면 [Cmfc리본 Mainpanel:: AddToRight](#addtoright)를 호출 합니다.

- 아래쪽 창에는 응용 프로그램의 설정을 변경 하 고 프로그램을 종료 하는 데 사용할 수 있는 단추가 있습니다. 이 창에 항목을 추가 하려면 [Cmfc리본 Mainpanel::](#addtobottom)을 (를) 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonMainPanel

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a> Cmfc리본 Mainpanel:: Add

응용 프로그램 단추 패널의 왼쪽 창에 리본 요소를 추가 합니다.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>매개 변수

*pElem*<br/>
[in, out] 주 패널에 추가할 리본 요소에 대 한 포인터입니다.

### <a name="remarks"></a>설명

패널에 리본 요소를 추가 합니다. 이 메서드를 사용 하 여 추가 된 요소는 주 패널의 왼쪽 열에 있습니다.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a> Cmfc리본 Mainpanel:: AddRecentFilesList

최근 파일 목록 메뉴에 텍스트 문자열을 추가 합니다.

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
최근 파일 목록에 추가할 문자열을 지정 합니다.

*nWidth*<br/>
최근 파일 목록 패널의 너비를 픽셀 단위로 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a> Cmfc리본 Mainpanel::가 중 하단

리본 응용 프로그램 패널의 아래쪽 창에 리본 요소를 추가 합니다.

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>매개 변수

*pElem*<br/>
[in, out] 주 패널의 아래쪽에 추가할 리본 요소에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a> Cmfc리본 Mainpanel:: AddToRight

응용 프로그램 단추 패널의 오른쪽 창에 리본 요소를 추가 합니다.

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>매개 변수

*pElem*<br/>
주 패널의 오른쪽에 추가할 리본 요소에 대 한 포인터입니다.

*nWidth*<br/>
오른쪽 패널의 너비를 픽셀 단위로 지정 합니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 오른쪽 패널에 리본 요소를 추가 합니다. 오른쪽 패널은 일반적으로 최근에 사용한 파일 목록을 표시 하지만 다른 모든 리본 요소를 여기에 추가할 수 있습니다.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a> Cmfc리본 Mainpanel:: GetCommandsFrame

리본 주 패널의 영역을 나타내는 사각형을 반환 합니다.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>반환 값

리본 주 패널의 영역을 나타내는 사각형입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 패널 클래스](../../mfc/reference/cmfcribbonpanel-class.md)

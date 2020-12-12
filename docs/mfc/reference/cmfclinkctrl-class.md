---
description: '자세한 정보: CMFCLinkCtrl 클래스'
title: CMFCLinkCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 6951f086ac99c4b8a8260a79ee08d54476694350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265222"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 클래스

`CMFCLinkCtrl`클래스는 단추를 하이퍼링크로 표시 하 고 단추를 클릭할 때 링크 대상을 호출 합니다.

## <a name="syntax"></a>구문

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCLinkCtrl:: SetURL](#seturl)|지정 된 URL을 단추 텍스트로 표시 합니다.|
|[CMFCLinkCtrl:: SetURLPrefix](#seturlprefix)|URL의 암시적 프로토콜 (예: "http:")을 설정 합니다.|
|[CMFCLinkCtrl:: System.windows.window.sizetocontent](#sizetocontent)|단추 텍스트 또는 비트맵을 포함 하도록 단추의 크기를 조정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMFCLinkCtrl:: OnDrawFocusRect](#ondrawfocusrect)|단추의 포커스 영역을 그리기 전에 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

클래스에서 파생 된 단추를 클릭 하면 `CMFCLinkCtrl` 프레임 워크에서 단추의 URL을 메서드에 매개 변수로 전달 합니다 `ShellExecute` . 그런 다음 `ShellExecute` 메서드는 URL의 대상을 엽니다.

## <a name="example"></a>예제

다음 예제에서는 개체의 크기를 설정 하는 방법과 `CMFCLinkCtrl` 개체에서 url 및 도구 설명을 설정 하는 방법을 보여 줍니다 `CMFCLinkCtrl` . 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxlinkctrl

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCLinkCtrl:: OnDrawFocusRect

단추의 포커스 영역을 그리기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectClient*<br/>
진행 링크 컨트롤의 경계를 조정 하는 사각형입니다.

### <a name="remarks"></a>설명

사용자 고유의 코드를 사용 하 여 단추의 포커스 영역을 그리도록 하려면이 메서드를 재정의 합니다.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a> CMFCLinkCtrl:: SetURL

지정 된 URL을 단추 텍스트로 표시 합니다.

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>매개 변수

*lpszURL*<br/>
진행 표시할 단추 텍스트입니다.

### <a name="remarks"></a>설명

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a> CMFCLinkCtrl:: SetURLPrefix

URL의 암시적 프로토콜 (예: "http:")을 설정 합니다.

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>매개 변수

*lpszPrefix*<br/>
진행 URL 프로토콜의 접두사입니다.

### <a name="remarks"></a>설명

URL 접두사를 설정 하려면이 메서드를 사용 합니다. 접두사는 단추의 표면에 표시 되지 않지만 URL 대상을 탐색 하는 데 사용할 수 있습니다.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a> CMFCLinkCtrl:: System.windows.window.sizetocontent

단추 텍스트 또는 비트맵을 포함 하도록 단추의 크기를 조정 합니다.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>매개 변수

*bVCenter*<br/>
진행 단추 텍스트와 비트맵을 링크 컨트롤의 위쪽과 아래쪽 사이에 세로로 맞추려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

*bHCenter*<br/>
진행 단추 텍스트와 비트맵을 링크 컨트롤의 왼쪽과 오른쪽 사이에 가로로 맞추려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 FALSE입니다.

### <a name="return-value"></a>반환 값

링크 컨트롤의 새 크기를 포함 하는 [csize](../../atl-mfc-shared/reference/csize-class.md) 개체입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl 클래스](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton 클래스](../../mfc/reference/cmfcbutton-class.md)

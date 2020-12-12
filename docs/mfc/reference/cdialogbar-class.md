---
description: '자세히 알아보기: CDialogBar 클래스'
title: CDialogBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: 7feb31cd8152309557a398f5c8d0edb8d91c340e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185221"
---
# <a name="cdialogbar-class"></a>CDialogBar 클래스

컨트롤 막대에 Windows 모덜리스 대화 상자의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDialogBar:: CDialogBar](#cdialogbar)|`CDialogBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDialogBar:: Create](#create)|Windows 대화 상자 모음을 만들고 개체에 연결 `CDialogBar` 합니다.|

## <a name="remarks"></a>설명

대화 상자 모음은 사용자가 탭 할 수 있는 표준 Windows 컨트롤을 포함 한다는 것을 대화 상자와 유사 하 게 표시 합니다. 또 다른 유사성은 대화 상자 모음을 나타내는 대화 상자 템플릿을 만드는 것입니다.

대화 상자 모음을 만들고 사용 하는 것은 개체를 만들고 사용 하는 것과 비슷합니다 `CFormView` . 먼저 [대화 상자 편집기](../../windows/dialog-editor.md) 를 사용 하 여 스타일 WS_CHILD 있는 대화 상자 템플릿을 정의 하 고 다른 스타일은 정의 하지 않습니다. 템플릿에는 WS_VISIBLE 스타일이 없어야 합니다. 응용 프로그램 코드에서 생성자를 호출 하 여 개체를 생성 `CDialogBar` 한 다음 `Create` 를 호출 하 여 대화 상자 표시줄 창을 만들고 개체에 연결 `CDialogBar` 합니다.

에 대 한 자세한 내용은 `CDialogBar` [대화 상자 표시줄](../../mfc/dialog-bars.md) 및 [기술 참고 31](../../mfc/tn031-control-bars.md), 컨트롤 막대를 참조 하세요.

> [!NOTE]
> 현재 릴리스에서 `CDialogBar` 개체는 Windows Forms 컨트롤을 호스트할 수 없습니다. Visual C++의 Windows Forms 컨트롤에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a> CDialogBar:: CDialogBar

`CDialogBar` 개체를 생성합니다.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a> CDialogBar:: Create

또는에 지정 된 대화 상자 리소스 템플릿을 로드 `lpszTemplateName` 하 고, `nIDTemplate` 대화 상자 표시줄 창을 만들고, 해당 스타일을 설정 하 고, 개체에 연결 `CDialogBar` 합니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
부모 개체에 대 한 포인터 `CWnd` 입니다.

*lpszTemplateName*<br/>
`CDialogBar`개체의 대화 상자 리소스 템플릿 이름에 대 한 포인터입니다.

*nStyle*<br/>
도구 모음 스타일입니다. 지원 되는 추가 도구 모음 스타일은 다음과 같습니다.

- CBRS_TOP 컨트롤 막대는 프레임 창의 맨 위에 있습니다.

- CBRS_BOTTOM 컨트롤 막대는 프레임 창의 맨 아래에 있습니다.

- CBRS_NOALIGN 컨트롤 막대는 부모 크기를 조정할 때 위치가 변경 되지 않습니다.

- CBRS_TOOLTIPS 컨트롤 막대는 도구 설명을 표시 합니다.

- CBRS_SIZE_DYNAMIC 컨트롤 막대는 동적입니다.

- CBRS_SIZE_FIXED 컨트롤 표시줄이 고정 되어 있습니다.

- CBRS_FLOATING 컨트롤 막대의 부동 소수점입니다.

- 상태 표시줄 CBRS_FLYBY 단추에 대 한 정보를 표시 합니다.

- CBRS_HIDE_INPLACE 컨트롤 막대는 사용자에 게 표시 되지 않습니다.

*nID*<br/>
대화 상자 표시줄의 컨트롤 ID입니다.

*nIDTemplate*<br/>
`CDialogBar`개체 대화 상자 템플릿의 리소스 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

CBRS_TOP 또는 CBRS_BOTTOM 맞춤 스타일을 지정 하는 경우 대화 상자 표시줄의 너비는 프레임 창의 너비 이며 해당 높이는 *nIDTemplate* 에서 지정한 리소스의 너비입니다. CBRS_LEFT 또는 CBRS_RIGHT 맞춤 스타일을 지정 하는 경우 대화 상자 모음의 높이는 프레임 창의 높이 이며 *nIDTemplate* 에서 지정한 리소스의 너비입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFormView 클래스](../../mfc/reference/cformview-class.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)

---
description: '자세히 알아보기: CHtmlEditCtrl 클래스'
title: CHtmlEditCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: d395f0f9f3e8b5ae10ad0ce35b2b1e410633e8d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183999"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 클래스

MFC 창에서 WebBrowser ActiveX 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|`CHtmlEditCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHtmlEditCtrl:: Create](#create)|WebBrowser ActiveX 컨트롤을 만들고 개체에 연결 `CHtmlEditCtrl` 합니다. 이 함수는 자동으로 WebBrowser ActiveX 컨트롤을 편집 모드로 전환 합니다.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|포함 된 WebBrowser 컨트롤에 현재 로드 된 문서에서 [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) 인터페이스를 검색 합니다.|
|[CHtmlEditCtrl:: GetStartDocument](#getstartdocument)|포함 된 WebBrowser 컨트롤에 로드할 기본 문서에 대 한 URL을 검색 합니다.|

## <a name="remarks"></a>설명

호스팅된 WebBrowser 컨트롤은 만들어진 후 자동으로 편집 모드로 전환 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a> CHtmlEditCtrl::CHtmlEditCtrl

`CHtmlEditCtrl` 개체를 생성합니다.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a> CHtmlEditCtrl:: Create

WebBrowser ActiveX 컨트롤을 만들고 개체에 연결 `CHtmlEditCtrl` 합니다. WebBrowser ActiveX 컨트롤은 자동으로 기본 문서를 탐색 한 다음이 함수에 의해 편집 모드로 배치 됩니다.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszWindowName*<br/>
이 매개 변수는 사용되지 않습니다.

*dwStyle*<br/>
이 매개 변수는 사용되지 않습니다.

*rect*<br/>
컨트롤의 크기와 위치를 지정 합니다.

*pParentWnd*<br/>
컨트롤의 부모 창을 지정 합니다. NULL이 아니어야 합니다.

*nID*<br/>
컨트롤의 ID를 지정 합니다.

*pContext*<br/>
이 매개 변수는 사용되지 않습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a> CHtmlEditCtrl::GetDHtmlDocument

포함 된 WebBrowser 컨트롤에 현재 로드 된 문서에서 [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) 인터페이스를 검색 합니다.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>매개 변수

*ppDocument*<br/>
문서 인터페이스입니다.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a> CHtmlEditCtrl:: GetStartDocument

포함 된 WebBrowser 컨트롤에 로드할 기본 문서에 대 한 URL을 검색 합니다.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)

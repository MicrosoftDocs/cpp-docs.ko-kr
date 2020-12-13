---
description: '자세히 알아보기: CMultiPageDHtmlDialog 클래스'
title: CMultiPageDHtmlDialog 클래스
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 1f7f8c2081687c71a98e427bb5396cfa47a73deb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331533"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog 클래스

여러 페이지로 구성된 대화 상자는 여러 HTML 페이지를 순차적으로 표시하고 각 페이지의 이벤트를 처리합니다.

## <a name="syntax"></a>구문

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMultiPageDHtmlDialog:: CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Multipage (마법사 스타일) DHTML 대화 상자 개체를 생성 합니다.|
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|다중 페이지 DHTML 대화 상자 개체를 소멸 시킵니다.|

## <a name="remarks"></a>설명

이를 수행 하는 메커니즘은 각 페이지에 대 한 포함 된 이벤트 맵을 포함 하는 [DHTML 및 URL 이벤트 맵입니다](dhtml-event-maps.md).

## <a name="example"></a>예제

이 다중 페이지 대화 상자에서는 간단한 마법사와 같은 기능을 정의 하는 세 가지 HTML 리소스를 가정 합니다. 첫 번째 페이지에는 **다음** 단추, 두 번째 단추, **이전** 및 **다음** 단추, 세 번째 **이전** 단추가 있습니다. 단추 중 하나를 누르면 처리기 함수가 [CDHtmlDialog:: LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) 를 호출 하 여 적절 한 새 페이지를 로드 합니다.

클래스 선언의 관련 부분 (CMyMultiPageDlg):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

클래스 구현의 관련 부분 (CMyMultipageDlg):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdhtml

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a> CMultiPageDHtmlDialog:: CMultiPageDHtmlDialog

Multipage (마법사 스타일) DHTML 대화 상자 개체를 생성 합니다.

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열입니다.

*szHtmlResID*<br/>
HTML 리소스의 이름인 null로 끝나는 문자열입니다.

*pParentWnd*<br/>
Dialog 개체가 속한 부모 또는 소유자 창 개체 ( [CWnd](../../mfc/reference/cwnd-class.md)형식)에 대 한 포인터입니다. NULL 인 경우에는 대화 상자 개체의 부모 창이 주 응용 프로그램 창으로 설정 됩니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

*nHtmlResID*<br/>
HTML 리소스의 ID 번호를 포함 합니다.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a> CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog

다중 페이지 DHTML 대화 상자 개체를 소멸 시킵니다.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>참고 항목

[CDHtmlDialog 클래스](../../mfc/reference/cdhtmldialog-class.md)

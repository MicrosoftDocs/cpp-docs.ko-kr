---
description: '다음에 대 한 자세한 정보: DDX_DHtml 도우미 매크로'
title: DDX_DHtml 도우미 매크로
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: ac7df82d628c943a5ba28697cf614853e7e7dddd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220242"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml 도우미 매크로

DDX_DHtml 도우미 매크로를 사용 하면 HTML 페이지에서 일반적으로 사용 되는 컨트롤 속성에 쉽게 액세스할 수 있습니다.

### <a name="data-exchange-macros"></a>데이터 교환 매크로

|Name|설명|
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|선택한 컨트롤에서 Value 속성을 설정 하거나 검색 합니다.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|현재 요소의 시작 태그와 끝 태그 사이에 있는 텍스트를 설정 하거나 검색 합니다.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|현재 요소의 시작 태그와 끝 태그 사이에 HTML을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|대상 URL 또는 앵커 지점을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|대상 창 또는 프레임을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|문서에서 이미지 또는 비디오 클립의 이름을 설정 하거나 검색 합니다.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|연결 된 프레임의 URL을 설정 하거나 검색 합니다.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|연결 된 프레임의 URL을 설정 하거나 검색 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** afxdhtml

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

대상 URL 또는 앵커 지점을 설정 하거나 검색 합니다.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLANCHORELEMENT_HREF 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a> DDX_DHtml_Anchor_Target

대상 창 또는 프레임을 설정 하거나 검색 합니다.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLANCHORELEMENT_TARGET 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a> DDX_DHtml_ElementInnerHtml

현재 요소의 시작 태그와 끝 태그 사이에 HTML을 설정 하거나 검색 합니다.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLELEMENT_INNERHTML 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a> DDX_DHtml_ElementInnerText

현재 요소의 시작 태그와 끝 태그 사이에 있는 텍스트를 설정 하거나 검색 합니다.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLELEMENT_INNERTEXT 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

선택한 컨트롤에서 Value 속성을 설정 하거나 검색 합니다.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다. [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)의 *값* 을 참조 하세요.

### <a name="remarks"></a>설명

이 매크로는 값 속성을 가진 컨트롤에서 실행 하는 경우에만 성공 합니다. 값 속성이 있는 컨트롤에는 편집 상자, 목록 상자 및 콤보 상자가 포함 됩니다.

이 매크로는 DISPID_A_VALUE 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

연결 된 프레임의 URL을 설정 하거나 검색 합니다.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLFRAMEBASE_SRC 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

연결 된 프레임의 URL을 설정 하거나 검색 합니다.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

이 매크로는 DISPID_IHTMLFRAMEBASE_SRC 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a> DDX_DHtml_Img_Src

문서에서 이미지 또는 비디오 클립의 이름을 가져오거나 검색 합니다.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>매개 변수

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md) 개체에 대 한 포인터입니다.

*name*<br/>
HTML 컨트롤의 ID 매개 변수에 대해 지정한 값입니다.

*var*<br/>
교환 되는 값입니다.

### <a name="remarks"></a>설명

DDX_DHtml_Img_Src 매크로를 사용 하 여 IMAGE 요소의 Src 속성을 검색 하는 경우 Internet Explorer 이미지 개체는 이미지 원본에 대해 완전히 이스케이프 된 URL을 반환 합니다. 예를 들어, DDX_DHtml_Img_Src 매크로를 사용 하 여 IMAGE 요소의 Src 속성을 "몇 가지 관심 있는 그림"으로 설정 하는 경우 Internet Explorer는 "res://d:\myapplication\myapp.exe/some%20interesting%20picture." 문자열을 반환 합니다.

이 매크로는 DISPID_IHTMLIMGELEMENT_SRC 디스패치 ID를 사용 하 여 [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) 함수를 호출 합니다.

## <a name="see-also"></a>참고 항목

[CDHtmlDialog 클래스](../../mfc/reference/cdhtmldialog-class.md)

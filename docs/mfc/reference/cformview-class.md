---
description: '자세한 정보: CFormView 클래스'
title: CFormView 클래스
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: ec37a3819f299830fef96bfdf93c0170b2969c66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184311"
---
# <a name="cformview-class"></a>CFormView 클래스

폼 뷰에 사용되는 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CFormView : public CScrollView
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|`CFormView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|초기화하는 동안 동기화에 사용됩니다.|

## <a name="remarks"></a>설명

폼 뷰는 기본적으로 컨트롤을 포함하는 뷰입니다. 이러한 컨트롤은 대화 상자 템플릿 리소스에 따라 배치됩니다. 애플리케이션에서 폼을 사용하려면 `CFormView`를 사용합니다. 이러한 뷰는 필요에 따라 [CScrollView](../../mfc/reference/cscrollview-class.md) 기능을 사용 하 여 스크롤을 지원 합니다.

[Forms-Based 응용 프로그램을 만드는](../../mfc/reference/creating-a-forms-based-mfc-application.md)경우 해당 뷰 클래스를 기반으로 하 여 `CFormView` 폼 기반 응용 프로그램을 만들 수 있습니다.

문서 뷰 기반 응용 프로그램에 새 [양식 항목](../../mfc/form-views-mfc.md) 을 삽입할 수도 있습니다. 애플리케이션이 초기에 폼을 지원하지 않은 경우에도 새 폼을 삽입하면 Visual C++에서 이 지원 기능을 추가합니다.

폼 기반 애플리케이션을 만들 때는 MFC 애플리케이션 마법사 및 클래스 추가 명령을 사용하는 것이 좋습니다. 이러한 메서드를 사용 하지 않고 폼 기반 응용 프로그램을 만들어야 하는 경우 [Forms-Based 응용 프로그램 만들기](../../mfc/reference/creating-a-forms-based-mfc-application.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a> CFormView:: CFormView

`CFormView` 개체를 생성합니다.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열을 포함 합니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

### <a name="remarks"></a>설명

에서 파생 된 형식의 개체를 만드는 경우 생성자 중 `CFormView` 하나를 호출 하 여 뷰 개체를 만들고 뷰의 기반이 되는 대화 상자 리소스를 식별 합니다. 이름을 기준으로 (문자열을 생성자에 인수로 전달 하거나 부호 없는 정수를 인수로 전달) 리소스를 식별할 수 있습니다.

폼 보기 창과 자식 컨트롤은가 호출 될 때까지 생성 되지 않습니다 `CWnd::Create` . `CWnd::Create` 는 문서 템플릿에 의해 구동 되는 문서 및 뷰 만들기 프로세스의 일부로 프레임 워크에서 호출 됩니다.

> [!NOTE]
> 파생 클래스는 자체 생성자를 제공 *해야 합니다* . 생성자에서 `CFormView::CFormView` 위의 클래스 개요와 같이 리소스 이름 또는 ID를 인수로 사용 하 여 생성자를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a> CFormView:: IsInitDlgCompleted

MFC에서 다른 작업을 수행하기 전에 초기화가 완료되었는지 확인하는 데 사용됩니다.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>반환 값

이 대화 상자에 대한 초기화 함수가 완료된 경우 true입니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView 클래스](../../mfc/reference/cscrollview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView 클래스](../../mfc/reference/cscrollview-class.md)

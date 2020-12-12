---
description: '자세한 정보: CSingleDocTemplate 클래스'
title: CSingleDocTemplate 클래스
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 611cada1c90fa776bafb78f0856658cd1bd0a8e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264624"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate 클래스

SDI(단일 문서 인터페이스)를 구현하는 문서 템플릿을 정의합니다.

## <a name="syntax"></a>구문

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSingleDocTemplate:: CSingleDocTemplate](#csingledoctemplate)|`CSingleDocTemplate` 개체를 생성합니다.|

## <a name="remarks"></a>설명

SDI 응용 프로그램은 주 프레임 창을 사용 하 여 문서를 표시 합니다. 한 번에 하나의 문서만 열 수 있습니다.

문서 템플릿은 세 가지 클래스 유형 간의 관계를 정의 합니다.

- 에서 파생 되는 문서 클래스 `CDocument` 입니다.

- 위에 나열 된 문서 클래스의 데이터를 표시 하는 뷰 클래스입니다. 이 클래스는,, 또는에서 파생 시킬 수 있습니다 `CView` `CScrollView` `CFormView` `CEditView` . 직접를 사용할 수도 있습니다 `CEditView` .

- 뷰를 포함 하는 프레임 창 클래스입니다. SDI 문서 템플릿의 경우에서이 클래스를 파생 시킬 수 있습니다 `CFrameWnd` . 주 프레임 창의 동작을 사용자 지정할 필요가 없는 경우 `CFrameWnd` 직접 클래스를 파생 시 키 지 않고도를 직접 사용할 수 있습니다.

SDI 응용 프로그램은 일반적으로 하나의 문서 형식을 지원 하므로 하나의 `CSingleDocTemplate` 개체만 포함 합니다. 한 번에 하나의 문서만 열 수 있습니다.

생성자를 제외 하 고의 멤버 함수를 호출할 필요가 없습니다 `CSingleDocTemplate` . 프레임 워크는 `CSingleDocTemplate` 개체를 내부적으로 처리 합니다.

사용에 대 한 자세한 내용은 `CSingleDocTemplate` [문서 템플릿 및 문서/뷰 만들기 프로세스](../../mfc/document-templates-and-the-document-view-creation-process.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a> CSingleDocTemplate:: CSingleDocTemplate

`CSingleDocTemplate` 개체를 생성합니다.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>매개 변수

*nIDResource*<br/>
문서 유형과 함께 사용 되는 리소스의 ID를 지정 합니다. 여기에는 메뉴, 아이콘, 액셀러레이터 키 테이블 및 문자열 리소스가 포함 될 수 있습니다.

문자열 리소스는 ' \n ' 문자로 구분 된 최대 7 개의 부분 문자열로 구성 됩니다. 부분 문자열이 포함 되지 않은 경우 ' \n ' 문자는 자리 표시자로 필요 하지만 후행 ' \n ' 문자는 필요 하지 않습니다. 이러한 부분 문자열은 문서 유형을 설명 합니다. 부분 문자열에 대 한 자세한 내용은 [Cdoctemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)을 참조 하세요. 이 문자열 리소스는 응용 프로그램의 리소스 파일에 있습니다. 예를 들어:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

문자열 편집기를 사용 하 여이 문자열을 편집할 수 있습니다. 전체 문자열은 7 개의 개별 항목이 아니라 문자열 편집기에서 단일 항목으로 나타납니다.

이러한 리소스 유형에 대 한 자세한 내용은 [문자열 편집기](../../windows/string-editor.md)를 참조 하십시오.

*pDocClass*<br/>
`CRuntimeClass`문서 클래스의 개체를 가리킵니다. 이 클래스는 `CDocument` 문서를 나타내기 위해 정의 하는 파생 클래스입니다.

*pFrameClass*<br/>
는 `CRuntimeClass` 프레임 창 클래스의 개체를 가리킵니다. 이 클래스는 `CFrameWnd` 파생 클래스 이거나 `CFrameWnd` 주 프레임 창에 대 한 기본 동작을 원하는 경우 자체가 될 수 있습니다.

*pViewClass*<br/>
`CRuntimeClass`뷰 클래스의 개체를 가리킵니다. 이 클래스는 `CView` 문서를 표시 하기 위해 정의 하는 파생 클래스입니다.

### <a name="remarks"></a>설명

개체를 동적으로 할당 하 `CSingleDocTemplate` 고 `CWinApp::AddDocTemplate` `InitInstance` 응용 프로그램 클래스의 멤버 함수에서로 전달 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 클래스](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate 클래스](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CWinApp 클래스](../../mfc/reference/cwinapp-class.md)

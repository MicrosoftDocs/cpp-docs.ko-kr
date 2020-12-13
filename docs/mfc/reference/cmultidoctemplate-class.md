---
description: '자세히 알아보기: CMultiDocTemplate 클래스'
title: CMultiDocTemplate 클래스
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 70b77c04fed41da3b5f025f6a600b9ecfd4bc89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331565"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 클래스

MDI(다중 문서 인터페이스)를 구현하는 문서 템플릿을 정의합니다.

## <a name="syntax"></a>구문

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>멤버

이 클래스의 멤버 함수는 가상입니다. 설명서는 [Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 및 [cdoctemplate](../../mfc/reference/ccmdtarget-class.md) 을 참조 하세요.

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMultiDocTemplate:: CMultiDocTemplate](#cmultidoctemplate)|`CMultiDocTemplate` 개체를 생성합니다.|

## <a name="remarks"></a>설명

MDI 응용 프로그램은 주 프레임 창을 사용자가 문서를 표시 하는 0 개 이상의 문서 프레임 창을 열 수 있는 작업 영역으로 사용 합니다. MDI에 대 한 자세한 설명은 *소프트웨어 디자인을 위한 Windows 인터페이스 지침* 을 참조 하세요.

문서 템플릿은 다음과 같은 세 가지 유형의 클래스 간 관계를 정의 합니다.

- [CDocument](../../mfc/reference/cdocument-class.md)에서 파생 되는 문서 클래스입니다.

- 위에 나열 된 문서 클래스의 데이터를 표시 하는 뷰 클래스입니다. 이 클래스는 [CView](../../mfc/reference/cview-class.md),, 또는에서 파생 시킬 수 있습니다 `CScrollView` `CFormView` `CEditView` . 직접를 사용할 수도 있습니다 `CEditView` .

- 뷰를 포함 하는 프레임 창 클래스입니다. MDI 문서 템플릿의 경우에서이 클래스를 파생 `CMDIChildWnd` 시키거나, 문서 프레임 창의 동작을 사용자 지정할 필요가 없는 경우 고유한 클래스를 파생 시 키 지 않고 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 를 직접 사용할 수 있습니다.

MDI 응용 프로그램은 둘 이상의 문서 형식을 지원할 수 있으며, 다른 형식의 문서는 동시에 열 수 있습니다. 응용 프로그램에는 지 원하는 각 문서 유형에 대 한 문서 템플릿이 하나 있습니다. 예를 들어 MDI 응용 프로그램에서 스프레드시트와 텍스트 문서를 모두 지 원하는 경우 응용 프로그램에는 두 개의 `CMultiDocTemplate` 개체가 있습니다.

응용 프로그램은 사용자가 새 문서를 만들 때 문서 템플릿을 사용 합니다. 응용 프로그램에서 둘 이상의 문서 유형을 지 원하는 경우 프레임 워크는 문서 템플릿에서 지원 되는 문서 유형의 이름을 가져오고 파일 새로 만들기 대화 상자의 목록에 표시 합니다. 사용자가 문서 유형을 선택 하면 응용 프로그램은 문서 클래스 개체, 프레임 창 개체 및 뷰 개체를 만들어 서로 연결 합니다.

생성자를 제외 하 고의 멤버 함수를 호출할 필요가 없습니다 `CMultiDocTemplate` . 프레임 워크는 `CMultiDocTemplate` 개체를 내부적으로 처리 합니다.

에 대 한 자세한 내용은 `CMultiDocTemplate` [문서 템플릿 및 문서/뷰 만들기 프로세스](../../mfc/document-templates-and-the-document-view-creation-process.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a> CMultiDocTemplate:: CMultiDocTemplate

`CMultiDocTemplate` 개체를 생성합니다.

```
CMultiDocTemplate(
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
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

첫 번째 하위 문자열이 MDI 응용 프로그램에 사용 되지 않으므로 포함 되지 않기 때문에 문자열은 ' \n ' 문자로 시작 합니다. 문자열 편집기를 사용 하 여이 문자열을 편집할 수 있습니다. 전체 문자열은 7 개의 개별 항목이 아니라 문자열 편집기에서 단일 항목으로 나타납니다.

이러한 리소스 유형에 대 한 자세한 내용은 [리소스 편집기](../../windows/resource-editors.md)를 참조 하십시오.

*pDocClass*<br/>
`CRuntimeClass`문서 클래스의 개체를 가리킵니다. 이 클래스는 `CDocument` 문서를 나타내기 위해 정의 하는 파생 클래스입니다.

*pFrameClass*<br/>
는 `CRuntimeClass` 프레임 창 클래스의 개체를 가리킵니다. 이 클래스는 파생 클래스 일 수도 있고 `CMDIChildWnd` `CMDIChildWnd` 문서 프레임 창에 대 한 기본 동작을 원하는 경우 자체가 될 수도 있습니다.

*pViewClass*<br/>
`CRuntimeClass`뷰 클래스의 개체를 가리킵니다. 이 클래스는 `CView` 문서를 표시 하기 위해 정의 하는 파생 클래스입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 `CMultiDocTemplate` 지 원하는 각 문서 형식에 대해 개체를 동적으로 할당 하 고 `CWinApp::AddDocTemplate` `InitInstance` 응용 프로그램 클래스의 멤버 함수에서 각 항목을에 전달 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

다음은 두 번째 예제입니다.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate 클래스](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp 클래스](../../mfc/reference/cwinapp-class.md)

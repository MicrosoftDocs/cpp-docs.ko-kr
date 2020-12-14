---
description: '자세히 알아보기: CDocTemplate 클래스'
title: CDocTemplate 클래스
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: e97e2d00f5ad847555ae951433c327cc861917b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184896"
---
# <a name="cdoctemplate-class"></a>CDocTemplate 클래스

문서 템플릿의 기본 기능을 정의하는 추상 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CDocTemplate:: CDocTemplate](#cdoctemplate)|`CDocTemplate` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDocTemplate:: AddDocument](#adddocument)|템플릿에 문서를 추가 합니다.|
|[CDocTemplate:: CloseAllDocuments](#closealldocuments)|이 템플릿과 연결 된 모든 문서를 닫습니다.|
|[CDocTemplate:: CreateNewDocument](#createnewdocument)|새 문서를 만듭니다.|
|[CDocTemplate:: CreateNewFrame](#createnewframe)|문서와 뷰를 포함 하는 새 프레임 창을 만듭니다.|
|[CDocTemplate:: CreateOleFrame](#createoleframe)|OLE 사용 프레임 창을 만듭니다.|
|[CDocTemplate:: CreatePreviewFrame](#createpreviewframe)|Rich Preview에 사용 되는 자식 프레임을 만듭니다.|
|[CDocTemplate:: GetDocString](#getdocstring)|문서 형식과 연결 된 문자열을 검색 합니다.|
|[CDocTemplate:: GetFirstDocPosition](#getfirstdocposition)|이 템플릿과 연결 된 첫 번째 문서의 위치를 검색 합니다.|
|[CDocTemplate:: GetNextDoc](#getnextdoc)|문서와 다음 항목의 위치를 검색 합니다.|
|[CDocTemplate:: InitialUpdateFrame](#initialupdateframe)|프레임 창을 초기화 하 고 선택적으로 표시 되도록 합니다.|
|[CDocTemplate:: LoadTemplate](#loadtemplate)|지정 된 또는 파생 클래스에 대 한 리소스를 로드 `CDocTemplate` 합니다.|
|[CDocTemplate:: MatchDocType](#matchdoctype)|문서 형식과이 템플릿 간의 일치 항목에 대 한 신뢰도를 결정 합니다.|
|[CDocTemplate:: OpenDocumentFile](#opendocumentfile)|경로 이름으로 지정 된 파일을 엽니다.|
|[CDocTemplate:: RemoveDocument](#removedocument)|템플릿에서 문서를 제거 합니다.|
|[CDocTemplate:: SaveAllModified](#saveallmodified)|이 템플릿과 연결 된 모든 문서를 수정 된 상태로 저장 합니다.|
|[CDocTemplate:: SetContainerInfo](#setcontainerinfo)|내부 OLE 항목을 편집할 때 OLE 컨테이너의 리소스를 결정 합니다.|
|[CDocTemplate:: SetDefaultTitle](#setdefaulttitle)|문서 창의 제목 표시줄에 기본 제목을 표시 합니다.|
|[CDocTemplate:: SetPreviewInfo](#setpreviewinfo)|Out-of-process 미리 보기 처리기를 제공 합니다.|
|[CDocTemplate:: SetServerInfo](#setserverinfo)|서버 문서를 내부에 포함 하거나 편집 하는 경우 리소스 및 클래스를 결정 합니다.|

## <a name="remarks"></a>설명

일반적으로 응용 프로그램의 함수 구현에서 하나 이상의 문서 템플릿을 만듭니다 `InitInstance` . 문서 템플릿은 다음과 같은 세 가지 유형의 클래스 간 관계를 정의 합니다.

- 에서 파생 되는 문서 클래스 `CDocument` 입니다.

- 위에 나열 된 문서 클래스의 데이터를 표시 하는 뷰 클래스입니다. 이 클래스는,, 또는에서 파생 시킬 수 있습니다 `CView` `CScrollView` `CFormView` `CEditView` . 직접를 사용할 수도 있습니다 `CEditView` .

- 뷰를 포함 하는 프레임 창 클래스입니다. SDI (단일 문서 인터페이스) 응용 프로그램의 경우에서이 클래스를 파생 시킵니다 `CFrameWnd` . MDI (다중 문서 인터페이스) 응용 프로그램의 경우에서이 클래스를 파생 시킵니다 `CMDIChildWnd` . 프레임 창의 동작을 사용자 지정할 필요가 없는 경우 직접 `CFrameWnd` `CMDIChildWnd` 클래스를 파생 시 키 지 않고 또는를 직접 사용할 수 있습니다.

응용 프로그램에는 지 원하는 각 문서 유형에 대 한 문서 템플릿이 하나 있습니다. 예를 들어 응용 프로그램에서 스프레드시트와 텍스트 문서를 모두 지 원하는 경우 응용 프로그램에는 두 개의 문서 템플릿 개체가 있습니다. 각 문서 템플릿은 해당 형식의 모든 문서를 만들고 관리 하는 일을 담당 합니다.

문서 템플릿은 `CRuntimeClass` 문서, 뷰 및 프레임 창 클래스의 개체에 대 한 포인터를 저장 합니다. 이러한 `CRuntimeClass` 개체는 문서 템플릿을 생성할 때 지정 됩니다.

문서 템플릿에는 문서 유형과 함께 사용 되는 리소스의 ID (예: 메뉴, 아이콘 또는 액셀러레이터 키 테이블 리소스)가 포함 되어 있습니다. 문서 템플릿에는 문서 형식에 대 한 추가 정보를 포함 하는 문자열도 있습니다. 여기에는 문서 유형 (예: "워크시트")과 파일 확장명 (예: ".xls")의 이름이 포함 됩니다. 필요에 따라 응용 프로그램의 사용자 인터페이스, Windows 파일 관리자 및 OLE (개체 연결 및 포함) 지원에 사용 되는 다른 문자열을 포함할 수 있습니다.

응용 프로그램이 OLE 컨테이너 및/또는 서버 이면 문서 템플릿도 전체 활성화 중에 사용 되는 메뉴의 ID를 정의 합니다. 응용 프로그램이 OLE 서버인 경우 문서 템플릿은 전체 활성화 중에 사용 되는 도구 모음 및 메뉴의 ID를 정의 합니다. 및를 호출 하 여 이러한 추가 OLE 리소스를 지정 `SetContainerInfo` `SetServerInfo` 합니다.

`CDocTemplate`는 추상 클래스 이므로 클래스를 직접 사용할 수 없습니다. 일반적인 응용 프로그램은 MFC 라이브러리에서 제공 하는 두 파생 클래스 중 하나를 사용 합니다 `CDocTemplate` .이 클래스는 `CSingleDocTemplate` SDI를 구현 하 고는 `CMultiDocTemplate` MDI를 구현 합니다. 문서 템플릿 사용에 대 한 자세한 내용은 해당 클래스를 참조 하세요.

응용 프로그램에 기본적으로 SDI 또는 MDI와는 다른 사용자 인터페이스 패러다임이 필요한 경우에서 고유한 클래스를 파생 시킬 수 있습니다 `CDocTemplate` .

에 대 한 자세한 내용은 `CDocTemplate` [문서 템플릿 및 문서/뷰 만들기 프로세스](../../mfc/document-templates-and-the-document-view-creation-process.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a> CDocTemplate:: AddDocument

이 함수를 사용 하 여 템플릿에 문서를 추가 합니다.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
추가할 문서에 대 한 포인터입니다.

### <a name="remarks"></a>설명

파생 클래스 [Cmultidoctemplate](../../mfc/reference/cmultidoctemplate-class.md) 및 [cmultidoctemplate](../../mfc/reference/csingledoctemplate-class.md) 이이 함수를 재정의 합니다. 에서 고유한 문서 템플릿 클래스를 파생 하는 경우 `CDocTemplate` 파생 클래스는이 함수를 재정의 해야 합니다.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a> CDocTemplate:: CDocTemplate

`CDocTemplate` 개체를 생성합니다.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>매개 변수

*nIDResource*<br/>
문서 유형과 함께 사용 되는 리소스의 ID를 지정 합니다. 여기에는 메뉴, 아이콘, 액셀러레이터 키 테이블 및 문자열 리소스가 포함 될 수 있습니다.

문자열 리소스는 ' \n ' 문자로 구분 된 최대 7 개의 부분 문자열로 구성 됩니다. 부분 문자열이 포함 되지 않은 경우 ' \n ' 문자는 자리 표시자로 필요 하지만 후행 ' \n ' 문자는 필요 하지 않습니다. 이러한 부분 문자열은 문서 유형을 설명 합니다. 부분 문자열에 대 한 자세한 내용은 [Getdocstring](#getdocstring)을 참조 하십시오. 이 문자열 리소스는 응용 프로그램의 리소스 파일에 있습니다. 예를 들어:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

문자열은 ' \n ' 문자로 시작 합니다. 이는 첫 번째 부분 문자열이 MDI 응용 프로그램에 사용 되지 않으므로 포함 되지 않기 때문입니다. 문자열 편집기를 사용 하 여이 문자열을 편집할 수 있습니다. 전체 문자열은 7 개의 개별 항목이 아니라 문자열 편집기에서 단일 항목으로 나타납니다.

*pDocClass*<br/>
`CRuntimeClass`문서 클래스의 개체를 가리킵니다. 이 클래스는 `CDocument` 문서를 나타내기 위해 정의 하는 파생 클래스입니다.

*pFrameClass*<br/>
는 `CRuntimeClass` 프레임 창 클래스의 개체를 가리킵니다. 이 클래스는 `CFrameWnd` 파생 클래스 이거나 `CFrameWnd` 주 프레임 창에 대 한 기본 동작을 원하는 경우 자체가 될 수 있습니다.

*pViewClass*<br/>
`CRuntimeClass`뷰 클래스의 개체를 가리킵니다. 이 클래스는 `CView` 문서를 표시 하기 위해 정의 하는 파생 클래스입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 사용 하 여 `CDocTemplate` 개체를 생성 합니다. 개체를 동적으로 할당 `CDocTemplate` 하 고 응용 프로그램 클래스의 멤버 함수에서 [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) 에 전달 `InitInstance` 합니다.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a> CDocTemplate:: CloseAllDocuments

이 멤버 함수를 호출 하 여 열려 있는 모든 문서를 닫습니다.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>매개 변수

*bEndSession*<br/>
사용되지 않습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 일반적으로 File Exit 명령의 일부로 사용 됩니다. 이 함수의 기본 구현에서는 [CDocument::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) 멤버 함수를 호출 하 여 문서의 데이터를 삭제 하 고 문서에 연결 된 모든 뷰에 대해 프레임 창을 닫습니다.

문서를 닫기 전에 사용자가 특수 정리 처리를 수행 하도록 하려면이 함수를 재정의 합니다. 예를 들어 문서가 데이터베이스의 레코드를 나타내는 경우이 함수를 재정의 하 여 데이터베이스를 닫을 수 있습니다.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a> CDocTemplate:: CreateNewDocument

이 멤버 함수를 호출 하 여이 문서 템플릿과 연결 된 형식의 새 문서를 만듭니다.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>반환 값

새로 만든 문서에 대 한 포인터 이거나, 오류가 발생 하는 경우 NULL입니다.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a> CDocTemplate:: CreateNewFrame

문서와 뷰를 포함 하는 새 프레임 창을 만듭니다.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
새 프레임 창에서 참조할 문서입니다. NULL일 수 있습니다.

*pOther*<br/>
새 프레임 창이 기반으로 하는 프레임 창입니다. NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

새로 만든 프레임 창에 대 한 포인터 이거나, 오류가 발생 하는 경우 NULL입니다.

### <a name="remarks"></a>설명

`CreateNewFrame` 생성자에 전달 된 개체를 사용 하 여 `CRuntimeClass` 뷰와 문서가 첨부 된 새 프레임 창을 만듭니다. *Pdoc* 매개 변수가 NULL 인 경우 프레임 워크는 추적 메시지를 출력 합니다.

*Popoparameter* 는 Window New 명령을 구현 하는 데 사용 됩니다. 새 프레임 창을 모델링할 프레임 창을 제공 합니다. 새 프레임 창은 일반적으로 보이지 않게 생성 됩니다. 새 파일 및 파일 열기의 표준 프레임 워크 구현 외부에서 프레임 창을 만들려면이 함수를 호출 합니다.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a> CDocTemplate:: CreateOleFrame

OLE 프레임 창을 만듭니다.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
프레임의 부모 창에 대 한 포인터입니다.

*pDoc*<br/>
새 OLE 프레임 창에서 참조할 문서에 대 한 포인터입니다.

*bCreateView*<br/>
뷰가 프레임과 함께 생성 되는지 여부를 결정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 프레임 창에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

*Bcreateview* 가 0 이면 빈 프레임이 만들어집니다.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a> CDocTemplate:: GetDocString

문서 형식과 연결 된 문자열을 검색 합니다.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>매개 변수

*rString*<br/>
`CString`함수가 반환 될 때 문자열을 포함 하는 개체에 대 한 참조입니다.

*index*<br/>
문서 유형을 설명 하는 문자열에서 검색 되는 부분 문자열의 인덱스입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- `CDocTemplate::windowTitle` 응용 프로그램 창의 제목 표시줄에 표시 되는 이름입니다 (예: "Microsoft Excel"). SDI 응용 프로그램의 문서 템플릿에만 제공 됩니다.

- `CDocTemplate::docName` 기본 문서 이름 (예: "Sheet")의 루트입니다. 이 루트와 숫자는 사용자가 파일 메뉴에서 새 명령을 선택할 때마다이 형식의 새 문서에 대 한 기본 이름으로 사용 됩니다 (예: "Sheet1" 또는 "Sheet2"). 지정 하지 않으면 "제목 없음"이 기본값으로 사용 됩니다.

- `CDocTemplate::fileNewName` 이 문서 유형의 이름입니다. 응용 프로그램에서 둘 이상의 문서 유형을 지 원하는 경우이 문자열은 파일 새로 만들기 대화 상자에 표시 됩니다 (예: "워크시트"). 지정 하지 않으면 파일 새로 만들기 명령을 사용 하 여 문서 형식에 액세스할 수 없습니다.

- `CDocTemplate::filterName` 이 형식의 문서 유형과 일치 하는 와일드 카드 필터에 대 한 설명입니다. 이 문자열은 파일 열기 대화 상자 (예: "워크시트 (* .xls)")의 파일 형식 목록 드롭다운 목록에 표시 됩니다. 지정 하지 않으면 파일 열기 명령을 사용 하 여 문서 형식에 액세스할 수 없습니다.

- `CDocTemplate::filterExt` 이 형식 (예: ".xls")의 문서에 대 한 확장입니다. 지정 하지 않으면 파일 열기 명령을 사용 하 여 문서 형식에 액세스할 수 없습니다.

- `CDocTemplate::regFileTypeId` Windows에서 유지 관리 되는 등록 데이터베이스에 저장 될 문서 형식의 식별자입니다. 이 문자열은 내부용 으로만 사용 됩니다 (예: "Excel 워크시트"). 지정 하지 않으면 문서 유형을 Windows 파일 관리자에 등록할 수 없습니다.

- `CDocTemplate::regFileTypeName` 등록 데이터베이스에 저장 될 문서 형식의 이름입니다. 이 문자열은 등록 데이터베이스에 액세스 하는 응용 프로그램의 대화 상자 (예: "Microsoft Excel 워크시트")에 표시 될 수 있습니다.

### <a name="return-value"></a>반환 값

지정 된 부분 문자열이 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

문서 유형을 설명 하는 특정 부분 문자열을 검색 하려면이 함수를 호출 합니다. 이러한 부분 문자열을 포함 하는 문자열은 문서 템플릿에 저장 되며 응용 프로그램에 대 한 리소스 파일의 문자열에서 파생 됩니다. 프레임 워크는이 함수를 호출 하 여 응용 프로그램의 사용자 인터페이스에 필요한 문자열을 가져옵니다. 응용 프로그램의 문서에 대해 파일 이름 확장명을 지정한 경우에는 Windows 등록 데이터베이스에 항목을 추가할 때 프레임 워크 에서도이 함수를 호출 합니다. 이렇게 하면 Windows 파일 관리자에서 문서를 열 수 있습니다.

에서 고유한 클래스를 파생 하는 경우에만이 함수를 호출 `CDocTemplate` 합니다.

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a> CDocTemplate:: GetFirstDocPosition

이 템플릿과 연결 된 첫 번째 문서의 위치를 검색 합니다.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>반환 값

이 문서 템플릿과 관련 된 문서 목록을 반복 하는 데 사용할 수 있는 위치 값입니다. 목록이 비어 있으면 NULL입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여이 템플릿과 연결 된 문서 목록에서 첫 번째 문서의 위치를 가져옵니다. [Cdoctemplate:: GetNextDoc](#getnextdoc) 에 대 한 인수로 POSITION 값을 사용 하 여 템플릿과 연결 된 문서 목록을 반복 합니다.

[Csingledoctemplate](../../mfc/reference/csingledoctemplate-class.md) 및 [csingledoctemplate](../../mfc/reference/cmultidoctemplate-class.md) 은 모두이 순수 가상 함수를 재정의 합니다. 에서 파생 하는 모든 클래스는 `CDocTemplate` 이 함수도 재정의 해야 합니다.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a> CDocTemplate:: GetNextDoc

*Rpo* 로 식별 되는 목록 요소를 검색 한 다음 *rpo* 를 목록에서 다음 항목의 위치 값으로 설정 합니다.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>반환 값

이 템플릿과 연결 된 문서 목록의 다음 문서에 대 한 포인터입니다.

### <a name="parameters"></a>매개 변수

*Rpo*<br/>
[Getfirstdocposition](#getfirstdocposition) 또는에 대 한 이전 호출에서 반환 된 위치 값에 대 한 참조입니다 `GetNextDoc` .

### <a name="remarks"></a>설명

검색 된 요소가 목록에서 마지막 이면 *rpo* 의 새 값이 NULL로 설정 됩니다.

`GetNextDoc` [Getfirstdocposition](#getfirstdocposition)을 호출 하 여 초기 위치를 설정 하는 경우 전방 반복 루프에서을 사용할 수 있습니다.

위치 값이 목록에서 올바른 위치를 나타내는지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a> CDocTemplate:: InitialUpdateFrame

프레임 창을 초기화 하 고 선택적으로 표시 되도록 합니다.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>매개 변수

*pFrame*<br/>
초기 업데이트가 필요한 프레임 창입니다.

*pDoc*<br/>
프레임이 연결 된 문서입니다. NULL일 수 있습니다.

*bMakeVisible*<br/>
프레임이 표시 되 고 활성화 되어야 하는지 여부를 나타냅니다.

### <a name="remarks"></a>설명

`IntitialUpdateFrame`를 사용 하 여 새 프레임을 만든 후를 호출 `CreateNewFrame` 합니다. 이 함수를 호출 하면 해당 프레임 창의 뷰가 호출을 수신 `OnInitialUpdate` 합니다. 또한 이전에 활성 뷰가 없는 경우에는 프레임 창의 기본 뷰가 활성화 됩니다. 기본 뷰는 AFX_IDW_PANE_FIRST의 자식 ID를 사용 하는 뷰입니다. 마지막으로 *Bmakevisible* 이 0이 아닌 경우 프레임 창이 표시 됩니다. *Bmakevisible* 이 0 이면 프레임 창의 현재 포커스 및 표시 상태는 변경 되지 않고 그대로 유지 됩니다.

새 파일 및 파일 열기의 프레임 워크 구현을 사용 하는 경우에는이 함수를 호출할 필요가 없습니다.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a> CDocTemplate:: LoadTemplate

지정 된 또는 파생 클래스에 대 한 리소스를 로드 `CDocTemplate` 합니다.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>설명

이 멤버 함수는 지정 된 또는 파생 클래스에 대 한 리소스를 로드 하기 위해 프레임 워크에서 호출 됩니다 `CDocTemplate` . 일반적으로 템플릿을 전역적으로 생성 하는 경우를 제외 하 고는 생성 중에 호출 됩니다. 이 경우에 대 한 호출은 `LoadTemplate` [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) 이 호출 될 때까지 지연 됩니다.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a> CDocTemplate:: MatchDocType

문서 형식과이 템플릿 간의 일치 항목에 대 한 신뢰도를 결정 합니다.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
형식을 확인할 파일의 경로 이름입니다.

*rpDocMatch*<br/>
*LpszPathName* 로 지정 된 파일이 이미 열려 있는 경우 일치 하는 문서가 할당 된 문서에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

**신뢰도** 열거형의 값으로, 다음과 같이 정의 됩니다.

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>설명

이 함수를 사용 하 여 파일을 여는 데 사용할 문서 템플릿 형식을 결정 합니다. 예를 들어 응용 프로그램에서 여러 파일 형식을 지 원하는 경우이 함수를 사용 하 여 `MatchDocType` 각 템플릿에 대해 각 템플릿을 호출 하 고 반환 된 신뢰도 값에 따라 템플릿을 선택 하 여 지정 된 파일에 적절 한 사용 가능한 문서 템플릿이 무엇 인지 확인할 수 있습니다.

*LpszPathName* 로 지정 된 파일이 이미 열려 있으면이 함수는를 반환 `CDocTemplate::yesAlreadyOpen` 하 고 `CDocument` *rpDocMatch* 의 개체에 파일의 개체를 복사 합니다.

파일이 열려 있지 않지만 *lpszPathName* 의 확장명이에 지정 된 확장과 일치 하는 경우 `CDocTemplate::filterExt` 이 함수는를 반환 `CDocTemplate::yesAttemptNative` 하 고 *rpDocMatch* 를 NULL로 설정 합니다. 에 대 한 자세한 내용은 `CDocTemplate::filterExt` [Cdoctemplate:: GetDocString](#getdocstring)을 참조 하세요.

대/소문자가 모두 true가 아니면 함수는를 반환 `CDocTemplate::yesAttemptForeign` 합니다.

기본 구현에서는 또는을 반환 하지 않습니다 `CDocTemplate::maybeAttemptForeign` `CDocTemplate::maybeAttemptNative` . **신뢰도** 열거에서 이러한 두 값을 사용 하 여 응용 프로그램에 적합 한 형식 일치 논리를 구현 하려면이 함수를 재정의 합니다.

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a> CDocTemplate:: OpenDocumentFile

경로에 지정 된 파일을 엽니다.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
진행 열 문서를 포함 하는 파일의 경로에 대 한 포인터입니다.

*bAddToMRU*<br/>
진행 TRUE는 문서가 가장 최근 파일 중 하나 임을 나타냅니다. FALSE는 문서가 가장 최근 파일 중 하나가 아님을 나타냅니다.

### <a name="return-value"></a>반환 값

*LpszPathName* 로 이름이 지정 된 파일의 문서에 대 한 포인터입니다. 실패 한 경우 NULL입니다.

### <a name="remarks"></a>설명

*LpszPathName* 에 의해 경로가 지정 된 파일을 엽니다. *LpszPathName* 가 NULL 인 경우이 템플릿과 연결 된 형식의 문서가 포함 된 새 파일이 만들어집니다.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a> CDocTemplate:: RemoveDocument

이 템플릿과 연결 된 문서 목록에서 *Pdoc* 가 가리키는 문서를 제거 합니다.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>매개 변수

*pDoc*<br/>
제거할 문서에 대 한 포인터입니다.

### <a name="remarks"></a>설명

파생 된 클래스 `CMultiDocTemplate` 및는 `CSingleDocTemplate` 이 함수를 재정의 합니다. 에서 고유한 문서 템플릿 클래스를 파생 하는 경우 `CDocTemplate` 파생 클래스는이 함수를 재정의 해야 합니다.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a> CDocTemplate:: SaveAllModified

수정 된 모든 문서를 저장 합니다.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값을 반환 합니다. 그렇지 않으면 0입니다.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a> CDocTemplate:: SetContainerInfo

내부 OLE 항목을 편집할 때 OLE 컨테이너의 리소스를 결정 합니다.

```cpp
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>매개 변수

*nIDOleInPlaceContainer*<br/>
포함 된 개체가 활성화 될 때 사용 되는 리소스의 ID입니다.

### <a name="remarks"></a>설명

OLE 개체가 내부 활성화 되어 있을 때 사용할 리소스를 설정 하려면이 함수를 호출 합니다. 이러한 리소스에는 메뉴 및 액셀러레이터 키 테이블이 포함 될 수 있습니다. 이 함수는 일반적으로 응용 프로그램의 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 함수에서 호출 됩니다.

*NIDOleInPlaceContainer* 과 연결 된 메뉴에는 활성화 된 내부 항목의 메뉴가 컨테이너 응용 프로그램의 메뉴와 병합 될 수 있도록 하는 구분 기호가 포함 되어 있습니다. 서버 및 컨테이너 메뉴를 병합 하는 방법에 대 한 자세한 내용은 [메뉴 및 리소스 (OLE)](../../mfc/menus-and-resources-ole.md)문서를 참조 하세요.

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a> CDocTemplate:: SetDefaultTitle

문서의 기본 제목을 로드 하 고 문서 제목 표시줄에 표시 하려면이 함수를 호출 합니다.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>매개 변수

*pDocument*<br/>
제목을 설정할 문서에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 제목에 대 한 자세한 내용은 `CDocTemplate::docName` [Cdoctemplate:: GetDocString](#getdocstring)의 설명을 참조 하세요.

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a> CDocTemplate:: SetServerInfo

서버 문서를 내부에 포함 하거나 편집 하는 경우 리소스 및 클래스를 결정 합니다.

```cpp
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>매개 변수

*nIDOleEmbedding*<br/>
별도의 창에서 포함 된 개체를 열 때 사용 되는 리소스의 ID입니다.

*nIDOleInPlaceServer*<br/>
포함 된 개체가 내부에서 활성화 될 때 사용 되는 리소스의 ID입니다.

*pOleFrameClass*<br/>
내부 활성화가 발생할 때 생성 되는 프레임 창 개체에 대 한 클래스 정보를 포함 하는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터입니다.

*pOleViewClass*<br/>
`CRuntimeClass`내부 활성화가 발생할 때 생성 되는 뷰 개체에 대 한 클래스 정보를 포함 하는 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

사용자가 포함 된 개체의 활성화를 요청할 때 서버 응용 프로그램에서 사용 되는 리소스를 식별 하려면이 멤버 함수를 호출 합니다. 이러한 리소스는 메뉴 및 액셀러레이터 키 테이블로 구성 됩니다. 이 함수는 일반적으로 `InitInstance` 응용 프로그램의에서 호출 됩니다.

*NIDOleInPlaceServer* 와 연결 된 메뉴에는 서버 메뉴를 컨테이너의 메뉴와 병합 하는 데 사용할 수 있는 구분 기호가 포함 되어 있습니다. 서버 및 컨테이너 메뉴를 병합 하는 방법에 대 한 자세한 내용은 [메뉴 및 리소스 (OLE)](../../mfc/menus-and-resources-ole.md)문서를 참조 하세요.

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a> CDocTemplate:: CreatePreviewFrame

Rich Preview에 사용 되는 자식 프레임을 만듭니다.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
부모 창에 대 한 포인터입니다 (일반적으로 셸에서 제공 됨).

*pDoc*<br/>
콘텐츠를 미리 볼 수 있는 문서 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 유효한 포인터 `CFrameWnd` 이거나, 만들지 못한 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a> CDocTemplate:: SetPreviewInfo

Out of process 미리 보기 처리기를 설정 합니다.

```cpp
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>매개 변수

*nIDPreviewFrame*<br/>
미리 보기 프레임의 리소스 ID를 지정 합니다.

*pPreviewFrameClass*<br/>
미리 보기 프레임의 런타임 클래스 정보 구조에 대 한 포인터를 지정 합니다.

*pPreviewViewClass*<br/>
미리 보기 뷰의 런타임 클래스 정보 구조에 대 한 포인터를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate 클래스](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate 클래스](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument 클래스](../../mfc/reference/cdocument-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CScrollView 클래스](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView 클래스](../../mfc/reference/ceditview-class.md)<br/>
[CFormView 클래스](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd 클래스](../../mfc/reference/cmdichildwnd-class.md)

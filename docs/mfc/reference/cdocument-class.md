---
description: '자세히 알아보기: CDocument 클래스'
title: CDocument 클래스
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: e821b82e849420fe82a7e40b7515bbb78e3284d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184805"
---
# <a name="cdocument-class"></a>CDocument 클래스

사용자 정의 문서 클래스에 대한 기본 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDocument:: CDocument](#cdocument)|`CDocument` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDocument:: AddView](#addview)|문서에 뷰를 연결 합니다.|
|[CDocument:: BeginReadChunks](#beginreadchunks)|청크 읽기를 초기화 합니다.|
|[CDocument:: CanCloseFrame](#cancloseframe)|고급 재정의 가능 이 문서를 보기 위해 프레임 창을 닫기 전에 호출 됩니다.|
|[CDocument:: ClearChunkList](#clearchunklist)|청크 목록을 지웁니다.|
|[CDocument:: ClearPathName](#clearpathname)|문서 개체의 경로를 지웁니다.|
|[CDocument::D eleteContents](#deletecontents)|문서 정리를 수행 하기 위해 호출 됩니다.|
|[CDocument:: FindChunk](#findchunk)|지정 된 GUID를 사용 하 여 청크를 찾습니다.|
|[CDocument:: GetAdapter](#getadapter)|인터페이스를 구현 하는 개체에 대 한 포인터를 반환 합니다 `IDocument` .|
|[CDocument:: GetDocTemplate](#getdoctemplate)|문서 형식을 설명 하는 문서 템플릿에 대 한 포인터를 반환 합니다.|
|[CDocument:: GetFile](#getfile)|원하는 개체에 대 한 포인터를 반환 `CFile` 합니다.|
|[CDocument:: GetFirstViewPosition](#getfirstviewposition)|뷰 목록에서 첫 번째의 위치를 반환 합니다. 반복을 시작 하는 데 사용 됩니다.|
|[CDocument:: GetNextView](#getnextview)|문서와 연결 된 뷰 목록을 반복 합니다.|
|[CDocument:: GetPathName](#getpathname)|문서 데이터 파일의 경로를 반환 합니다.|
|[CDocument:: GetThumbnail](#getthumbnail)|축소판 그림을 표시 하기 위해 축소판 그림 공급자에서 사용할 비트맵을 만들기 위해 호출 됩니다.|
|[CDocument:: GetTitle](#gettitle)|문서 제목을 반환 합니다.|
|[CDocument:: InitializeSearchContent](#initializesearchcontent)|검색 처리기에 대 한 검색 콘텐츠를 초기화 하기 위해 호출 됩니다.|
|[CDocument:: IsModified](#ismodified)|문서가 마지막으로 저장 된 이후 수정 되었는지 여부를 나타냅니다.|
|[CDocument:: IsSearchAndOrganizeHandler](#issearchandorganizehandler)|이 `CDocument` 개체 인스턴스가 검색 & 구성 처리기에 대해 만들어졌는지 여부를 나타냅니다.|
|[CDocument:: LoadDocumentFromStream](#loaddocumentfromstream)|스트림에서 문서 데이터를 로드 하기 위해 호출 됩니다.|
|[CDocument:: OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Rich Preview 글꼴이 변경 되기 전에 호출 됩니다.|
|[CDocument:: OnChangedViewList](#onchangedviewlist)|뷰가 문서에 추가 되거나 문서에서 제거 된 후에 호출 됩니다.|
|[CDocument:: OnCloseDocument](#onclosedocument)|문서를 닫기 위해 호출 됩니다.|
|[CDocument:: OnCreatePreviewFrame](#oncreatepreviewframe)|Rich Preview에 대 한 미리 보기 프레임을 만들어야 할 때 프레임 워크에서 호출 됩니다.|
|[CDocument:: OnDocumentEvent](#ondocumentevent)|문서 이벤트에 대 한 응답으로 프레임 워크에서 호출 됩니다.|
|[CDocument:: OnDrawThumbnail 그림](#ondrawthumbnail)|미리 보기의 콘텐츠를 그리려면 파생 클래스에서이 메서드를 재정의 합니다.|
|[CDocument:: OnLoadDocumentFromStream](#onloaddocumentfromstream)|스트림에서 문서 데이터를 로드 해야 할 때 프레임 워크에서 호출 됩니다.|
|[CDocument:: OnNewDocument](#onnewdocument)|새 문서를 만들기 위해 호출 됩니다.|
|[CDocument:: OnOpenDocument](#onopendocument)|기존 문서를 열기 위해 호출 됩니다.|
|[CDocument:: OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|GetFocus 함수를 호출 하 여 HWND를 반환 하도록 미리 보기 처리기에 지시 합니다.|
|[CDocument:: OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|미리 보기 처리기가 실행 중인 프로세스의 메시지 펌프에서 전달 되는 키 입력을 처리 하도록 지시 합니다.|
|[CDocument:: OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Rich Preview 배경색을 변경 하면 호출 됩니다.|
|[CDocument:: OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Rich Preview 글꼴이 변경 되 면 호출 됩니다.|
|[CDocument:: OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Rich Preview 사이트가 변경 되 면 호출 됩니다.|
|[CDocument:: OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Rich Preview 텍스트 색이 변경 되 면 호출 됩니다.|
|[CDocument:: OnSaveDocument](#onsavedocument)|문서를 디스크에 저장 하기 위해 호출 됩니다.|
|[CDocument:: OnUnloadHandler](#onunloadhandler)|미리 보기 처리기가 언로드될 때 프레임 워크에서 호출 됩니다.|
|[CDocument::P](#precloseframe)|프레임 창을 닫기 전에 호출 됩니다.|
|[CDocument:: ReadNextChunkValue](#readnextchunkvalue)|다음 청크 값을 읽습니다.|
|[CDocument:: ReleaseFile](#releasefile)|다른 응용 프로그램에서 사용할 수 있도록 파일을 해제 합니다.|
|[CDocument:: RemoveChunk](#removechunk)|지정 된 GUID의 청크를 제거 합니다.|
|[CDocument:: RemoveView](#removeview)|문서에서 뷰를 분리 합니다.|
|[CDocument:: ReportSaveLoadException](#reportsaveloadexception)|고급 재정의 가능 예외로 인해 열기 또는 저장 작업을 완료할 수 없는 경우 호출 됩니다.|
|[CDocument:: SaveModified](#savemodified)|고급 재정의 가능 문서를 저장 해야 하는지 여부를 사용자에 게 요청 하기 위해 호출 됩니다.|
|[CDocument:: SetChunkValue](#setchunkvalue)|청크 값을 설정 합니다.|
|[CDocument:: SetModifiedFlag](#setmodifiedflag)|문서를 마지막으로 저장 한 이후 수정 했음을 나타내는 플래그를 설정 합니다.|
|[CDocument:: SetPathName](#setpathname)|문서에서 사용 하는 데이터 파일의 경로를 설정 합니다.|
|[CDocument:: SetTitle](#settitle)|문서 제목을 설정 합니다.|
|[CDocument:: UpdateAllViews](#updateallviews)|문서를 수정한 모든 뷰에 알립니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CDocument:: OnFileSendMail](#onfilesendmail)|첨부 된 문서가 있는 메일 메시지를 보냅니다.|
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|메일 지원이 있는 경우 메일 보내기 명령을 사용 하도록 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDocument:: m_bGetThumbnailMode](#m_bgetthumbnailmode)|`CDocument`개체가 미리 보기에 대해 dllhost로 생성 되도록 지정 합니다. 체크 인 해야 `CView::OnDraw` 합니다.|
|[CDocument:: m_bPreviewHandlerMode](#m_bpreviewhandlermode)|`CDocument`에 대해 prevhost에서 개체를 만들었음을 지정 합니다 `Rich Preview` . 체크 인 해야 `CView::OnDraw` 합니다.|
|[CDocument:: m_bSearchMode](#m_bsearchmode)|개체를 `CDocument` 인덱서가 나 다른 검색 응용 프로그램으로 만들었음을 지정 합니다.|
|[CDocument:: m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|서식 있는 미리 보기 창의 배경색을 지정 합니다. 이 색은 호스트에 의해 설정 됩니다.|
|[CDocument:: m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|서식 있는 미리 보기 창의 전경색을 지정 합니다. 이 색은 호스트에 의해 설정 됩니다.|
|[CDocument:: m_lfRichPreviewFont](#m_lfrichpreviewfont)|서식 있는 미리 보기 창의 텍스트 글꼴을 지정 합니다. 이 글꼴 정보는 호스트에 의해 설정 됩니다.|

## <a name="remarks"></a>설명

문서는 일반적으로 파일 열기 명령을 사용 하 여 사용자가 여는 데이터의 단위를 나타내며, 파일 저장 명령을 사용 하 여 저장 합니다.

`CDocument` 문서 만들기, 로드 및 저장과 같은 표준 작업을 지원 합니다. 프레임 워크는에 정의 된 인터페이스를 사용 하 여 문서를 조작 합니다 `CDocument` .

응용 프로그램은 둘 이상의 문서 유형을 지원할 수 있습니다. 예를 들어 응용 프로그램에서 스프레드시트와 텍스트 문서를 모두 지원할 수 있습니다. 각 문서 형식에는 관련 문서 템플릿이 있습니다. 문서 템플릿은 해당 문서 유형에 사용 되는 리소스 (예: 메뉴, 아이콘 또는 액셀러레이터 키 테이블)를 지정 합니다. 각 문서에는 연결 된 개체에 대 한 포인터가 포함 되어 있습니다 `CDocTemplate` .

사용자는 연결 된 [CView](../../mfc/reference/cview-class.md) 개체를 통해 문서와 상호 작용 합니다. 뷰는 프레임 창에서 문서의 이미지를 렌더링 하 고 사용자 입력을 문서에 대 한 작업으로 해석 합니다. 문서에는 여러 개의 뷰가 연결 되어 있을 수 있습니다. 사용자가 문서에서 창을 열면 프레임 워크에서 뷰를 만들어 문서에 연결 합니다. 문서 템플릿은 각 문서 유형을 표시 하는 데 사용 되는 뷰 및 프레임 창의 유형을 지정 합니다.

문서는 프레임 워크 표준 명령 라우팅의 일부 이므로 표준 사용자 인터페이스 구성 요소 (예: 파일 저장 메뉴 항목)에서 명령을 수신 합니다. 문서는 활성 뷰에서 전달 되는 명령을 수신 합니다. 문서는 지정 된 명령을 처리 하지 않는 경우 명령을 관리 하는 문서 템플릿에 명령을 전달 합니다.

문서의 데이터를 수정 하는 경우 해당 뷰는 이러한 수정 사항을 반영 해야 합니다. `CDocument` 는 이러한 변경 내용에 대 한 보기를 알리기 위해 [UpdateAllViews](#updateallviews) 멤버 함수를 제공 합니다. 따라서 뷰는 필요에 따라 자체적으로 다시 그릴 수 있습니다. 또한 프레임 워크는 사용자에 게 파일을 닫기 전에 수정한 파일을 저장 하 라는 메시지를 표시 합니다.

일반적인 응용 프로그램에서 문서를 구현 하려면 다음을 수행 해야 합니다.

- `CDocument`각 문서 형식에 대해에서 클래스를 파생 시킵니다.

- 각 문서의 데이터를 저장할 멤버 변수를 추가 합니다.

- 문서 데이터를 읽고 수정 하는 멤버 함수를 구현 합니다. 문서 뷰는 이러한 멤버 함수에서 가장 중요 한 사용자입니다.

- 문서 클래스의 [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) 멤버 함수를 재정의 하 여 문서 데이터를 디스크에 쓰고 디스크에서 읽습니다.

`CDocument` MAPI (메일 지원)가 있는 경우 메일을 통해 문서를 보내는 것을 지원 합니다. MFC의 [mapi](../../mfc/mapi.md) 및 [mapi 지원](../../mfc/mapi-support-in-mfc.md)문서를 참조 하세요.

에 대 한 자세한 내용은 `CDocument` [Serialization](../../mfc/serialization-in-mfc.md), [문서/뷰 아키텍처 항목](../../mfc/document-view-architecture.md)및 [문서/뷰 만들기](../../mfc/document-view-creation.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a> CDocument:: AddView

문서에 뷰를 연결 하려면이 함수를 호출 합니다.

```cpp
void AddView(CView* pView);
```

### <a name="parameters"></a>매개 변수

*pView*<br/>
추가 되는 뷰를 가리킵니다.

### <a name="remarks"></a>설명

이 함수는 지정 된 뷰를 문서와 연결 된 뷰 목록에 추가 합니다. 또한이 함수는이 문서에 대 한 뷰의 문서 포인터를 설정 합니다. 프레임 워크는 새로 만든 뷰 개체를 문서에 연결할 때이 함수를 호출 합니다. 이는 파일 새로 만들기, 파일 열기 또는 새 창 명령에 대 한 응답으로 발생 하거나 분할자 창이 분할 된 경우에 발생 합니다.

뷰를 수동으로 만들고 연결 하는 경우에만이 함수를 호출 합니다. 일반적으로 프레임 워크는 문서 클래스, 뷰 클래스 및 프레임 창 클래스를 연결 하는 [Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체를 정의 하 여 문서와 뷰를 연결할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a> CDocument:: BeginReadChunks

청크 읽기를 초기화 합니다.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>설명

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a> CDocument:: CanCloseFrame

문서를 표시 하는 프레임 창이 닫히므로 전에 프레임 워크에서 호출 됩니다.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>매개 변수

*pFrame*<br/>
문서에 첨부 된 뷰의 프레임 창을 가리킵니다.

### <a name="return-value"></a>반환 값

프레임 창을 닫아도 안전 하지 않은 경우에는 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현에서는 문서를 표시 하는 다른 프레임 창이 있는지 확인 합니다. 지정 된 프레임 창이 문서를 표시 하는 마지막 창인 경우 문서를 수정한 경우 사용자에 게 문서를 저장 하 라는 메시지를 표시 합니다. 프레임 창이 닫힐 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a> CDocument:: CDocument

`CDocument` 개체를 생성합니다.

```
CDocument();
```

### <a name="remarks"></a>설명

프레임 워크는 문서 만들기를 처리 합니다. 문서 별로 초기화를 수행 하도록 [Onnewdocument](#onnewdocument) 멤버 함수를 재정의 합니다. 이는 SDI (단일 문서 인터페이스) 응용 프로그램에서 특히 중요 합니다.

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a> CDocument:: ClearChunkList

청크 목록을 지웁니다.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>설명

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a> CDocument:: ClearPathName

문서 개체의 경로를 지웁니다.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>설명

개체에서 경로를 지우면 `CDocument` 문서를 다음에 저장할 때 응용 프로그램에서 사용자에 게 메시지를 표시 합니다. 이렇게 하면 **저장** 명령이 다른 **이름으로 저장** 명령 처럼 동작 합니다.

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a> CDocument::D eleteContents

개체 자체를 소멸 시 키 지 않고 문서의 데이터를 삭제 하기 위해 프레임 워크에서 호출 `CDocument` 됩니다.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>설명

문서가 제거 되기 직전에 호출 됩니다. 문서를 다시 사용 하기 전에 비어 있도록 하기 위해이 메서드를 호출 합니다. 이는 하나의 문서만 사용 하는 SDI 응용 프로그램의 경우 특히 중요 합니다. 사용자가 다른 문서를 만들거나 열 때마다 문서가 다시 사용 됩니다. 모든 문서의 데이터를 삭제 하는 "모두 지우기 모두 편집" 또는 유사한 명령을 구현 하려면이 함수를 호출 합니다. 이 함수의 기본 구현은 아무 작업도 수행하지 않습니다. 문서의 데이터를 삭제 하려면이 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a> CDocument:: FindChunk

지정 된 GUID를 사용 하 여 청크를 찾습니다.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>매개 변수

*guid*<br/>
찾을 청크의 GUID를 지정 합니다.

*pid*<br/>
찾을 청크의 PID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 내부 청크 목록에서 위치를 표시 합니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a> CDocument:: GetAdapter

인터페이스를 구현 하는 개체에 대 한 포인터를 반환 합니다 `IDocument` .

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>반환 값

인터페이스를 구현 하는 개체에 대 한 포인터 `IDocument` 입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a> CDocument:: GetDocTemplate

이 문서 형식에 대 한 문서 템플릿에 대 한 포인터를 가져오려면이 함수를 호출 합니다.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>반환 값

이 문서 형식에 대 한 문서 템플릿에 대 한 포인터 이거나 문서가 문서 템플릿에 의해 관리 되지 않는 경우 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a> CDocument:: GetFile

이 멤버 함수를 호출 하 여 개체에 대 한 포인터를 가져옵니다 `CFile` .

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
원하는 파일의 경로인 문자열입니다. 경로는 상대 경로 이거나 절대 경로일 수 있습니다.

*pError*<br/>
작업의 완료 상태를 나타내는 기존 파일-예외 개체에 대 한 포인터입니다.

*nOpenFlags*<br/>
공유 및 액세스 모드 파일을 열 때 수행할 동작을 지정 합니다. 비트 OR (&#124;) 연산자를 사용 하 여 CFile 생성자 [cfile:: CFile](../../mfc/reference/cfile-class.md#cfile) 에 나열 된 옵션을 결합할 수 있습니다. 하나의 액세스 권한 및 하나의 공유 옵션이 필요 합니다. `modeCreate` 및 `modeNoInherit` 모드는 선택 사항입니다.

### <a name="return-value"></a>반환 값

`CFile` 개체에 대한 포인터입니다.

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a> CDocument:: GetFirstViewPosition

문서와 연결 된 뷰 목록에서 첫 번째 뷰의 위치를 가져오려면이 함수를 호출 합니다.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>반환 값

[GetNextView](#getnextview) 멤버 함수를 사용 하 여 반복 하는 데 사용할 수 있는 위치 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a> CDocument:: GetNextView

이 함수를 호출 하 여 문서의 모든 뷰를 반복 합니다.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>매개 변수

*rPosition*<br/>
`GetNextView`또는 [Getfirstviewposition](#getfirstviewposition) 멤버 함수에 대 한 이전 호출에서 반환 된 위치 값에 대 한 참조입니다. 이 값은 NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

*Rposition* 으로 식별 되는 뷰에 대 한 포인터입니다.

### <a name="remarks"></a>설명

함수는 *rposition* 으로 식별 된 뷰를 반환한 다음 *rposition* 을 목록에 있는 다음 뷰의 position 값으로 설정 합니다. 검색 된 뷰가 목록에서 마지막 이면 *Rposition* 은 NULL로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a> CDocument:: GetPathName

문서 디스크 파일의 정규화 된 경로를 가져오려면이 함수를 호출 합니다.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>반환 값

문서의 정규화 된 경로입니다. 문서를 저장 하지 않았거나 문서와 연결 된 디스크 파일이 없으면이 문자열은 비어 있습니다.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a> CDocument:: GetThumbnail

축소판 그림을 표시 하기 위해 미리 보기 공급자가 사용할 비트맵을 만듭니다.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>매개 변수

*cx*<br/>
비트맵의 너비와 높이를 지정 합니다.

*phbmp*<br/>
함수가 성공적으로 반환 될 때 비트맵에 대 한 핸들을 포함 합니다.

*pdwAlpha*<br/>
함수가 성공적으로 반환 될 때 알파 채널 값을 지정 하는 DWORD를 포함 합니다.

### <a name="return-value"></a>반환 값

미리 보기에 대 한 비트맵이 성공적으로 만들어진 경우 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentgettitle"></a><a name="gettitle"></a> CDocument:: GetTitle

문서 파일 이름에서 일반적으로 파생 된 문서 제목을 가져오려면이 함수를 호출 합니다.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>반환 값

문서 제목입니다.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a> CDocument:: InitializeSearchContent

검색 처리기에 대 한 검색 콘텐츠를 초기화 하기 위해 호출 됩니다.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>설명

검색 콘텐츠를 초기화 하려면 파생 클래스에서이 메서드를 재정의 합니다. 콘텐츠는 ";"로 구분 되는 부분을 포함 하는 문자열 이어야 합니다. 예: "point; 사각형 ole 항목 ".

## <a name="cdocumentismodified"></a><a name="ismodified"></a> CDocument:: IsModified

문서가 마지막으로 저장 된 이후 수정 되었는지 여부를 확인 하려면이 함수를 호출 합니다.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>반환 값

문서가 마지막으로 저장 된 후 수정 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a> CDocument:: IsSearchAndOrganizeHandler

이 인스턴스가 `CDocument` 검색 & 구성 핸들러에 대해 만들어졌는지 여부를 나타냅니다.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>반환 값

의이 인스턴스가 `CDocument` 검색 & 구성 처리기에 대해 만들어진 경우 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

현재이 함수는 out of process 서버에서 구현 된 풍부한 미리 보기 처리기에 대해서만 TRUE를 반환 합니다. 응용 프로그램 수준에서 적절 한 플래그 (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode)를 설정 하 여이 함수가 TRUE를 반환 하도록 할 수 있습니다.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a> CDocument:: LoadDocumentFromStream

스트림에서 문서 데이터를 로드 하기 위해 호출 됩니다.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
스트림에 대 한 포인터입니다. 이 스트림은 셸에 의해 제공 됩니다.

*dwGrfMode*<br/>
스트림에 대 한 액세스 모드입니다.

### <a name="return-value"></a>반환 값

로드 작업이 성공 하면이 고, 그렇지 않으면 오류 코드가 포함 된 HRESULT입니다. S_OK

### <a name="remarks"></a>설명

파생 클래스에서이 메서드를 재정의 하 여 스트림에서 데이터를 로드 하는 방법을 사용자 지정할 수 있습니다.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a> CDocument:: m_bGetThumbnailMode

`CDocument`개체가 미리 보기에 대해 dllhost에 의해 만들어짐을 지정 합니다. 체크 인 해야 `CView::OnDraw` 합니다.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>설명

`TRUE` 문서를 미리 보기에 대해 dllhost로 만들었는지 여부를 나타냅니다.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a> CDocument:: m_bPreviewHandlerMode

`CDocument`Rich Preview에 대해 prevhost에서 만든 개체를 지정 합니다. 체크 인 해야 `CView::OnDraw` 합니다.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>설명

TRUE는 문서를 Rich Preview for prevhost에서 만들었는지 여부를 나타냅니다.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a> CDocument:: m_bSearchMode

`CDocument`개체가 인덱서가 나 다른 검색 응용 프로그램에 의해 생성 되었음을 지정 합니다.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>설명

`TRUE` 문서를 인덱서가 나 다른 검색 응용 프로그램으로 만들었음을 나타냅니다.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a> CDocument:: m_clrRichPreviewBackColor

서식 있는 미리 보기 창의 배경색을 지정 합니다. 이 색은 호스트에 의해 설정 됩니다.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>설명

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a> CDocument:: m_clrRichPreviewTextColor

서식 있는 미리 보기 창의 전경색을 지정 합니다. 이 색은 호스트에 의해 설정 됩니다.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>설명

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a> CDocument:: m_lfRichPreviewFont

서식 있는 미리 보기 창의 텍스트 글꼴을 지정 합니다. 이 글꼴 정보는 호스트에 의해 설정 됩니다.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>설명

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a> CDocument:: OnBeforeRichPreviewFontChanged

Rich Preview 글꼴이 변경 되기 전에 호출 됩니다.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a> CDocument:: OnChangedViewList

뷰가 문서에 추가 되거나 문서에서 제거 된 후 프레임 워크에서 호출 됩니다.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>설명

이 함수의 기본 구현은 마지막 뷰를 제거 하 고 있는지 여부를 확인 하 고, 그럴 경우 문서를 삭제 합니다. 프레임 워크가 뷰를 추가 하거나 제거할 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다. 예를 들어, 연결 된 뷰가 없는 경우에도 문서를 열어 두고 싶으면이 함수를 재정의 합니다.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a> CDocument:: OnCloseDocument

일반적으로 파일 닫기 명령의 일부로 문서를 닫을 때 프레임 워크에서 호출 됩니다.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>설명

이 함수의 기본 구현은 문서를 보는 데 사용 되는 모든 프레임을 제거 하 고 뷰를 닫은 다음 문서 내용을 정리 하 고 [DeleteContents](#deletecontents) 멤버 함수를 호출 하 여 문서의 데이터를 삭제 합니다.

프레임 워크가 문서를 닫을 때 특수 정리 처리를 수행 하려면이 함수를 재정의 합니다. 예를 들어 문서가 데이터베이스의 레코드를 나타내는 경우이 함수를 재정의 하 여 데이터베이스를 닫을 수 있습니다. 재정의에서이 함수의 기본 클래스 버전을 호출 해야 합니다.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a> CDocument:: OnCreatePreviewFrame

Rich Preview에 대 한 미리 보기 프레임을 만들어야 할 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>반환 값

프레임이 성공적으로 생성 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a> CDocument:: OnDocumentEvent

문서 이벤트에 대 한 응답으로 프레임 워크에서 호출 됩니다.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>매개 변수

*deEvent*<br/>
진행 이벤트 유형을 설명 하는 열거 데이터 형식입니다.

### <a name="remarks"></a>설명

문서 이벤트는 여러 클래스에 영향을 줄 수 있습니다. 이 메서드는 [CDocument 클래스](../../mfc/reference/cdocument-class.md)이외의 클래스에 영향을 주는 문서 이벤트 처리를 담당 합니다. 현재 문서 이벤트에 응답 해야 하는 클래스는 [CDataRecoveryHandler 클래스](../../mfc/reference/cdatarecoveryhandler-class.md)뿐입니다. `CDocument`클래스에는에 대 한 효과를 처리 하는 다른 재정의 가능 메서드가 있습니다 `CDocument` .

다음 표에서는 *Deevent* 에 사용할 수 있는 값과 해당 값에 해당 하는 이벤트를 보여 줍니다.

|값|해당 이벤트|
|-----------|-------------------------|
|`onAfterNewDocument`|새 문서를 만들었습니다.|
|`onAfterOpenDocument`|새 문서가 열렸습니다.|
|`onAfterSaveDocument`|문서가 저장 되었습니다.|
|`onAfterCloseDocument`|문서가 닫혔습니다.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a> CDocument:: OnDrawThumbnail 그림

미리 보기를 그리려면 파생 클래스에서이 메서드를 재정의 합니다.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
장치 컨텍스트에 대 한 참조입니다.

*lprcBounds*<br/>
축소판 그림을 그릴 영역의 경계 사각형을 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a> CDocument:: OnFileSendMail

문서를 첨부 파일로 사용 하 여 상주 메일 호스트 (있는 경우)를 통해 메시지를 보냅니다.

```cpp
void OnFileSendMail();
```

### <a name="remarks"></a>설명

`OnFileSendMail`[Onsavedocument](#onsavedocument) 를 호출 하 여 제목 없는 문서와 수정 된 문서를 임시 파일에 serialize (저장) 한 다음 전자 메일을 통해 보냅니다. 문서가 수정 되지 않은 경우에는 임시 파일이 필요 하지 않습니다. 원본이 전송 됩니다. `OnFileSendMail` 아직 로드 되지 않은 경우 MAPI32.DLL을 로드 합니다.

`OnFileSendMail` [Coledocument](../../mfc/reference/coledocument-class.md) 에 대 한 특별 한 구현은 복합 파일을 올바르게 처리 합니다.

`CDocument` MAPI (메일 지원)가 있는 경우 메일을 통해 문서를 보내는 것을 지원 합니다. MFC의 [Mapi 항목](../../mfc/mapi.md) 및 [mapi 지원](../../mfc/mapi-support-in-mfc.md)문서를 참조 하세요.

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a> CDocument:: OnLoadDocumentFromStream

스트림에서 문서 데이터를 로드 해야 할 때 프레임 워크에서 호출 됩니다.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
들어오는 스트림에 대 한 포인터입니다.

*grfMode*<br/>
스트림에 대 한 액세스 모드입니다.

### <a name="return-value"></a>반환 값

로드가 성공 하면 S_OK 하 고, 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a> CDocument:: OnNewDocument

File New 명령의 일부로 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>반환 값

문서가 성공적으로 초기화 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 [DeleteContents](#deletecontents) 멤버 함수를 호출 하 여 문서가 비어 있는지 확인 한 다음 새 문서를 clean으로 표시 합니다. 새 문서에 대 한 데이터 구조를 초기화 하려면이 함수를 재정의 합니다. 재정의에서이 함수의 기본 클래스 버전을 호출 해야 합니다.

사용자가 SDI 응용 프로그램에서 파일 새로 만들기 명령을 선택 하는 경우 프레임 워크는 새 문서를 만드는 대신이 함수를 사용 하 여 기존 문서를 다시 초기화 합니다. 사용자가 MDI (다중 문서 인터페이스) 응용 프로그램에서 파일 새로 만들기를 선택 하는 경우 프레임 워크는 매번 새 문서를 만든 다음이 함수를 호출 하 여 초기화 합니다. SDI 응용 프로그램에서 효과적으로 파일 새로 만들기 명령의 생성자 대신이 함수에 초기화 코드를 넣어야 합니다.

`OnNewDocument`가 두 번 호출 되는 경우도 있습니다. 이는 문서가 ActiveX 문서 서버로 포함 될 때 발생 합니다. 함수는 `CreateInstance` 메서드 (파생 클래스에 의해 노출 됨 `COleObjectFactory` ) 및 `InitNew` 메서드 (파생 클래스에 의해 노출 됨)에 의해 두 번째로 호출 됩니다 `COleServerDoc` .

### <a name="example"></a>예제

다음 예에서는 문서 개체를 초기화 하는 다른 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a> CDocument:: OnOpenDocument

파일 열기 명령의 일부로 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
열 문서 경로를 가리킵니다.

### <a name="return-value"></a>반환 값

문서가 성공적으로 로드 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 지정 된 파일을 열고, [DeleteContents](#deletecontents) 멤버 함수를 호출 하 여 문서가 비어 있는지 확인 하 고, [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) 를 호출 하 여 파일의 내용을 읽은 다음 문서를 clean으로 표시 합니다. 보관 메커니즘 또는 파일 메커니즘과 다른 항목을 사용 하려면이 함수를 재정의 합니다. 예를 들어 문서가 개별 파일이 아닌 데이터베이스의 레코드를 나타내는 응용 프로그램을 작성할 수 있습니다.

사용자가 SDI 응용 프로그램에서 파일 열기 명령을 선택 하면 프레임 워크에서이 함수를 사용 하 여 `CDocument` 새 개체를 만들지 않고 기존 개체를 다시 초기화 합니다. 사용자가 MDI 응용 프로그램에서 파일 열기를 선택 하는 경우 프레임 워크는 매번 새 개체를 생성 한 `CDocument` 다음이 함수를 호출 하 여 초기화 합니다. SDI 응용 프로그램에서 효과적으로 파일 열기 명령의 생성자 대신이 함수에 초기화 코드를 넣어야 합니다.

### <a name="example"></a>예제

다음 예에서는 문서 개체를 초기화 하는 다른 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a> CDocument:: OnPreviewHandlerQueryFocus

함수를 호출 하 여 검색 된 HWND를 반환 하도록 미리 보기 처리기에 지시 `GetFocus` 합니다.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>매개 변수

*phwnd*<br/>
제한이 이 메서드가 반환 될 때 `GetFocus` 미리 보기 처리기의 포그라운드 스레드에서 함수를 호출 하 여 반환 된 HWND에 대 한 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 반환 합니다. 그렇지 않으면 오류 값입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a> CDocument:: OnPreviewHandlerTranslateAccelerator

미리 보기 처리기가 실행 중인 프로세스의 메시지 펌프에서 전달 되는 키 입력을 처리 하도록 지시 합니다.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>매개 변수

*pmsg*<br/>
진행 창 메시지에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

키 입력 메시지를 미리 보기 처리기에서 처리할 수 있는 경우 처리기는 해당 메시지를 처리 하 고 S_OK 반환 합니다. 미리 보기 처리기가 키 입력 메시지를 처리할 수 없는 경우를 통해 호스트에 제공 `IPreviewHandlerFrame::TranslateAccelerator` 합니다. 호스트에서 메시지를 처리 하는 경우이 메서드는 S_OK 반환 합니다. 호스트에서 메시지를 처리 하지 않는 경우이 메서드는 S_FALSE 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a> CDocument:: OnRichPreviewBackColorChanged

Rich Preview 배경색을 변경 하면 호출 됩니다.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a> CDocument:: OnRichPreviewFontChanged

Rich Preview 글꼴이 변경 되 면 호출 됩니다.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a> CDocument:: OnRichPreviewSiteChanged

Rich Preview 사이트가 변경 될 때 호출 됩니다.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a> CDocument:: OnRichPreviewTextColorChanged

Rich Preview 텍스트 색이 변경 되 면 호출 됩니다.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a> CDocument:: OnSaveDocument

파일 저장 또는 파일 다른 이름으로 저장 명령의 일부로 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
파일을 저장 해야 하는 정규화 된 경로를 가리킵니다.

### <a name="return-value"></a>반환 값

문서가 성공적으로 저장 되 면 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 지정 된 파일을 열고 [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) 를 호출 하 여 문서 데이터를 파일에 쓴 다음 문서를 clean으로 표시 합니다. 프레임 워크가 문서를 저장할 때 특수 한 처리를 수행 하려면이 함수를 재정의 합니다. 예를 들어 문서가 개별 파일이 아닌 데이터베이스의 레코드를 나타내는 응용 프로그램을 작성할 수 있습니다.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a> CDocument:: OnUnloadHandler

미리 보기 처리기가 언로드될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>설명

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a> CDocument:: OnUpdateFileSendMail

MAPI (메일 지원)가 있는 경우 ID_FILE_SEND_MAIL 명령을 사용 하도록 설정 합니다.

```cpp
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>매개 변수

*pCmdUI*<br/>
ID_FILE_SEND_MAIL 명령과 연결 된 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

그렇지 않으면 함수는 메뉴 항목의 위 또는 아래에 있는 구분 기호를 포함 하 여 메뉴의 ID_FILE_SEND_MAIL 명령을 적절 하 게 제거 합니다. MAPI는 경로에 MAPI32.DLL 있고 WIN.INI 파일의 [Mail] 섹션 (MAPI = 1)에 있는 경우에 사용할 수 있습니다. 대부분의 응용 프로그램은 파일 메뉴에이 명령을 배치 합니다.

`CDocument` MAPI (메일 지원)가 있는 경우 메일을 통해 문서를 보내는 것을 지원 합니다. MFC의 [Mapi 항목](../../mfc/mapi.md) 및 [mapi 지원](../../mfc/mapi-support-in-mfc.md)문서를 참조 하세요.

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a> CDocument::P

이 멤버 함수는 프레임 창이 제거 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>매개 변수

*pFrame*<br/>
연결 된 개체를 보유 하는 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 에 대 한 포인터 `CDocument` 입니다.

### <a name="remarks"></a>설명

사용자 지정 정리를 제공 하도록 재정의 될 수 있지만 기본 클래스도 호출 해야 합니다.

의 기본값은 `PreCloseFrame` 에서 아무 작업도 수행 하지 않습니다 `CDocument` . `CDocument`파생 클래스 [Coledocument](../../mfc/reference/coledocument-class.md) 및 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 는이 멤버 함수를 사용 합니다.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a> CDocument:: ReadNextChunkValue

다음 청크 값을 읽습니다.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>매개 변수

*ppValue*<br/>
제한이 함수가 반환 될 때 *Ppvalue* 는 읽은 값을 포함 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a> CDocument:: ReleaseFile

이 멤버 함수는 파일을 해제 하 고 다른 응용 프로그램에서 사용할 수 있도록 프레임 워크에서 호출 됩니다.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>매개 변수

*.Pfile*<br/>
해제할 CFile 개체에 대 한 포인터입니다.

*bAbort*<br/>
또는 중 하나를 사용 하 여 파일을 해제할지 여부를 지정 합니다 `CFile::Close` `CFile::Abort` . [CFile:: Close](../../mfc/reference/cfile-class.md#close)를 사용 하 여 파일을 해제 하려면 false이 고, [CFile:: Abort](../../mfc/reference/cfile-class.md#abort)를 사용 하 여 파일을 해제 하려면 TRUE입니다.

### <a name="remarks"></a>설명

*Babort* 가 TRUE 이면를 `ReleaseFile` 호출 하 `CFile::Abort` 고 파일을 해제 합니다. `CFile::Abort` 에서 예외를 throw 하지 않습니다.

*Babort* 가 FALSE 이면를 `ReleaseFile` 호출 `CFile::Close` 하 고 파일을 해제 합니다.

파일이 해제 되기 전에 사용자가 작업을 수행 하도록 하려면이 멤버 함수를 재정의 합니다.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a> CDocument:: RemoveChunk

지정 된 GUID를 사용 하 여 청크를 제거 합니다.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>매개 변수

*Eid*<br/>
제거할 청크의 GUID를 지정 합니다.

*P&id*<br/>
제거할 청크의 PID를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="cdocumentremoveview"></a><a name="removeview"></a> CDocument:: RemoveView

문서에서 뷰를 분리 하려면이 함수를 호출 합니다.

```cpp
void RemoveView(CView* pView);
```

### <a name="parameters"></a>매개 변수

*pView*<br/>
제거할 뷰를 가리킵니다.

### <a name="remarks"></a>설명

이 함수는 문서와 연결 된 뷰 목록에서 지정 된 뷰를 제거 합니다. 또한 뷰의 문서 포인터를 NULL로 설정 합니다. 이 함수는 프레임 창이 닫히거나 분할자 창의 창이 닫힐 때 프레임 워크에서 호출 됩니다.

뷰를 수동으로 분리 하는 경우에만이 함수를 호출 합니다. 일반적으로 프레임 워크는 문서 클래스, 뷰 클래스 및 프레임 창 클래스를 연결 하는 [Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체를 정의 하 여 문서와 뷰를 분리할 수 있습니다.

샘플 구현은 [Addview](#addview) 에서 예제를 참조 하세요.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a> CDocument:: ReportSaveLoadException

문서를 저장 하거나 로드 하는 동안 예외가 throw 되는 경우 (일반적으로 [Cfileexception](../../mfc/reference/cfileexception-class.md) 또는 [CArchiveException](../../mfc/reference/carchiveexception-class.md)) 호출 됩니다.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
저장 되거나 로드 된 문서의 이름을 가리킵니다.

*e*<br/>
Throw 된 예외를 가리킵니다. NULL일 수 있습니다.

*bSaving*<br/>
진행 중인 작업을 나타내는 플래그입니다. 문서를 저장 하는 경우 0이 아니고 문서를 로드 하 고 있는 경우 0입니다.

*nIDPDefault*<br/>
함수에서 더 구체적인 항목을 지정 하지 않은 경우 표시할 오류 메시지의 식별자입니다.

### <a name="remarks"></a>설명

기본 구현에서는 예외 개체를 검사 하 고 원인을 구체적으로 설명 하는 오류 메시지를 찾습니다. 특정 메시지를 찾을 수 없거나 *e* 가 NULL 인 경우 *nIDPDefault* 매개 변수로 지정 된 일반 메시지가 사용 됩니다. 그러면 함수는 오류 메시지를 포함 하는 메시지 상자를 표시 합니다. 사용자 지정 된 추가 오류 메시지를 제공 하려는 경우이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a> CDocument:: SaveModified

수정 된 문서를 닫기 전에 프레임 워크에서 호출 됩니다.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>반환 값

계속 하 고 문서를 닫는 것이 안전 하면 0이 아닌 것입니다. 문서를 닫지 않아야 하는 경우 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 변경 내용을 문서에 저장할지 여부를 사용자에 게 묻는 메시지 상자를 표시 합니다 (변경 된 경우). 프로그램에서 다른 프롬프트 프로시저를 필요로 하는 경우이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a> CDocument:: SetChunkValue

청크 값을 설정 합니다.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>매개 변수

*pValue*<br/>
설정할 청크 값을 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a> CDocument:: SetModifiedFlag

문서를 수정한 후이 함수를 호출 합니다.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>매개 변수

*bModified*<br/>
문서를 수정 했는지 여부를 나타내는 플래그입니다.

### <a name="remarks"></a>설명

이 함수를 일관 되 게 호출 하면 문서를 닫기 전에 프레임 워크에서 사용자에 게 변경 내용을 저장 하 라는 메시지를 표시 합니다. 일반적으로 *Bmodified* 매개 변수에는 기본값인 TRUE를 사용 해야 합니다. 문서를 정리 (수정 되지 않음)로 표시 하려면 FALSE 값을 사용 하 여이 함수를 호출 합니다.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a> CDocument:: SetPathName

문서 디스크 파일의 정규화 된 경로를 지정 하려면이 함수를 호출 합니다.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
문서에 대 한 경로로 사용할 문자열을 가리킵니다.

*bAddToMRU*<br/>
파일 이름이 가장 최근에 사용한 (MRU) 파일 목록에 추가 되는지 여부를 결정 합니다. TRUE 이면 파일 이름이 추가 됩니다. FALSE 이면 추가 되지 않습니다.

### <a name="remarks"></a>설명

*BAddToMRU* 의 값에 따라 경로가 응용 프로그램에 의해 유지 관리 되는 MRU 목록에 추가 되거나 추가 되지 않습니다. 일부 문서는 디스크 파일에 연결 되지 않습니다. 프레임 워크에서 사용 하는 파일을 열고 저장 하기 위한 기본 구현을 재정의 하는 경우에만이 함수를 호출 합니다.

## <a name="cdocumentsettitle"></a><a name="settitle"></a> CDocument:: SetTitle

문서 제목 (프레임 창의 제목 표시줄에 표시 되는 문자열)을 지정 하려면이 함수를 호출 합니다.

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>매개 변수

*lpszTitle*<br/>
문서 제목으로 사용 되는 문자열을 가리킵니다.

### <a name="remarks"></a>설명

이 함수를 호출 하면 문서를 표시 하는 모든 프레임 창의 제목이 업데이트 됩니다.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a> CDocument:: UpdateAllViews

문서가 수정 된 후이 함수를 호출 합니다.

```cpp
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>매개 변수

*pSender*<br/>
문서를 수정한 뷰를 가리키거나 모든 뷰를 업데이트할 경우 NULL입니다.

*lHint*<br/>
수정에 대 한 정보를 포함 합니다.

*pHint*<br/>
수정에 대 한 정보를 저장 하는 개체를 가리킵니다.

### <a name="remarks"></a>설명

[SetModifiedFlag](#setmodifiedflag) 멤버 함수를 호출한 후이 함수를 호출 해야 합니다. 이 함수는 문서가 수정 된 *Psender* 로 지정 된 뷰를 제외 하 고 문서에 연결 된 각 뷰를 알려 줍니다. 일반적으로 사용자가 뷰를 통해 문서를 변경한 후 뷰 클래스에서이 함수를 호출 합니다.

이 함수는 송신 뷰를 제외한 각 문서 뷰에 대해 [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) 멤버 함수를 호출 하 여 *Phint* 및 *lhint* 를 전달 합니다. 이러한 매개 변수를 사용 하 여 문서에 대 한 수정 내용에 대 한 정보를 뷰에 전달 합니다. *Lhint* 및/를 사용 하 여 정보를 인코딩하고, [CObject](../../mfc/reference/cobject-class.md)파생 클래스를 정의 하 여 수정에 대 한 정보를 저장 하 고 *phint* 를 사용 하 여 해당 클래스의 개체를 전달할 수 있습니다. 전달 된 `CView::OnUpdate` 정보에 따라 뷰의 표시 업데이트를 최적화 하려면 [CView](../../mfc/reference/cview-class.md)파생 클래스에서 멤버 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)

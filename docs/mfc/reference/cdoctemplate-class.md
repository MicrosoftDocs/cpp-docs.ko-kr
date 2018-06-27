---
title: CDocTemplate 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a1ee27994a83206b576452d30b108f01c794353
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957511"
---
# <a name="cdoctemplate-class"></a>CDocTemplate 클래스
문서 템플릿의 기본 기능을 정의하는 추상 기본 클래스입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>멤버  
  
### <a name="protected-constructors"></a>Protected 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|`CDocTemplate` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|문서 서식 파일에 추가합니다.|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|이 템플릿에 연결 된 모든 문서를 닫습니다.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|새 문서를 만듭니다.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|문서 및 보기를 포함 하는 새로운 프레임 창을 만듭니다.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|OLE 활성화 프레임 창을 만듭니다.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|서식 있는 미리 보기에 사용 되는 자식 프레임을 만듭니다.|  
|[CDocTemplate::GetDocString](#getdocstring)|문서 종류와 관련 된 문자열을 검색 합니다.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|이 템플릿에 연결 된 첫 번째 문서 위치를 검색 합니다.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|다음의 위치와 문서를 검색합니다.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|프레임 창을 초기화 하 고 필요에 따라 표시 되도록 합니다.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|에 대 한 리소스 로드는 지정 된 `CDocTemplate` 또는 파생 클래스입니다.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|문서 종류와이 서식 파일 간의 일치에 대 한 신뢰도의 정도 결정합니다.|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|경로 이름으로 지정 된 파일을 엽니다.|  
|[CDocTemplate::RemoveDocument](#removedocument)|서식 파일에서 문서를 제거합니다.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|수정 된는이 템플릿에 연결 된 모든 문서를 저장 합니다.|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|내부 OLE 항목을 편집 하는 경우 OLE 컨테이너에 대 한 리소스를 결정 합니다.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|기본 제목을 문서 창의 제목 표시줄에 표시 됩니다.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|프로세스 미리 보기 처리기에서 설치 합니다.|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|서버 문서는 포함 되어 있거나 현재 위치를 편집할 때 리소스 및 클래스를 결정 합니다.|  
  
## <a name="remarks"></a>설명  
 일반적으로 응용 프로그램의 구현에서 하나 이상의 문서 서식 파일을 만들면 `InitInstance` 함수입니다. 문서 서식 파일을 3 가지 유형의 클래스 간의 관계를 정의합니다.  
  
-   문서 클래스에서 파생 되는 `CDocument`합니다.  
  
-   위에 나열 된 문서 클래스에서 데이터를 표시 하는 뷰 클래스 이 클래스를 파생 시켜 `CView`, `CScrollView`, `CFormView`, 또는 `CEditView`합니다. (사용할 수 있습니다 `CEditView` 직접.)  
  
-   프레임 창 클래스-보기가 포함 합니다. 이 클래스를 파생 하는 단일 문서 SDI (인터페이스) 응용 프로그램에 대 한 `CFrameWnd`합니다. 이 클래스에서 파생 하는 여러 문서 MDI (인터페이스) 응용 프로그램의 경우 `CMDIChildWnd`합니다. 프레임 창 동작을 사용자 지정할 필요가 없습니다 경우 사용할 수 있습니다 `CFrameWnd` 또는 `CMDIChildWnd` 직접 하지 않고 사용자 고유의 클래스를 파생 합니다.  
  
 응용 프로그램에 각 유형의 지원 되는 문서에 대해 하나의 문서 서식 파일을 있습니다. 예를 들어 응용 프로그램 모두 스프레드시트 및 텍스트 문서를 지 원하는 경우 응용 프로그램에 두 문서 템플릿 개체에 있습니다. 각 문서 서식 파일은 해당 형식의 모든 문서 만들기 및 관리 하는 일을 담당 합니다.  
  
 문서 서식 파일에 대 한 포인터를 저장 된 `CRuntimeClass` 문서, 뷰 및 프레임 창 클래스에 대 한 개체입니다. 이러한 `CRuntimeClass` 문서 서식 파일을 생성할 때 개체를 지정 합니다.  
  
 문서 서식 파일 문서 형식 (예: 메뉴, 아이콘 또는 액셀러레이터 키 테이블 리소스)를 사용 하는 리소스의 ID를 포함 합니다. 문서 서식 파일에는 해당 문서 유형에 대 한 추가 정보를 포함 하는 문자열에 있습니다. 여기에 문서 유형 (예: "워크시트") 및 파일 확장명 (예: ".xls")의 이름을 포함 합니다. 필요에 따라 응용 프로그램의 사용자 인터페이스, Windows 파일 관리자 및 개체 연결 및 OLE 지원에서 사용 하는 다른 문자열을 포함할 수 있습니다.  
  
 OLE 컨테이너 및/또는 서버 응용 프로그램이 경우 문서 서식 파일에는 내부 활성화 동안 사용 되는 메뉴의 ID를도 정의 합니다. OLE 서버 응용 프로그램을 사용 하는 경우 문서 서식 파일의 위치에서 활성화 중에 사용 되는 메뉴 및 도구 모음 ID를 정의 합니다. 호출 하 여 이러한 추가 OLE 리소스 지정 `SetContainerInfo` 및 `SetServerInfo`합니다.  
  
 때문에 `CDocTemplate` 클래스는 추상 클래스는 클래스를 직접 사용할 수 없습니다. 일반적인 응용 프로그램 둘 중 하나를 사용 합니다. `CDocTemplate`-Microsoft Foundation Class 라이브러리에서 제공 하는 클래스를 파생: `CSingleDocTemplate`, SDI를 구현 하는 및 `CMultiDocTemplate`, MDI를 구현 하는 합니다. 문서 서식 파일을 사용 하 여에 이러한 클래스에 대 한 자세한 내용은 참조 하십시오.  
  
 응용 프로그램에서 기본적으로 다른 SDI 또는 MDI 사용자 인터페이스 패러다임을 필요한 경우에서 고유한 클래스를 파생 시켜 `CDocTemplate`합니다.  
  
 대 한 자세한 내용은 `CDocTemplate`, 참조 [문서 템플릿 및 문서/뷰 만들기 프로세스](../../mfc/document-templates-and-the-document-view-creation-process.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 이 함수를 사용 하 여 문서 서식 파일에 추가 합니다.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>매개 변수  
 *pDoc*  
 추가 될 문서에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 파생된 클래스 [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) 및 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) 이 함수를 재정의 합니다. 고유한 문서 템플릿 클래스를 파생 하는 경우 `CDocTemplate`, 파생된 클래스에서이 함수를 재정의 해야 합니다.  
  
##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate  
 `CDocTemplate` 개체를 생성합니다.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>매개 변수  
 *nIDResource*  
 문서 종류를 사용 하는 리소스의 ID를 지정 합니다. 이 메뉴, 아이콘, 액셀러레이터 키 테이블 및 문자열 리소스 포함 될 수 있습니다.  
  
 '\N' 문자로 구분 되는 최대 7 개의 부분 문자열로 이루어진 문자열 리소스 구성 (부분 문자열에 포함 되지 않은 경우 '\n' 문자 자리 표시자 변수로 필요; 그러나 후행 '\n' 문자가 필요 하지 않은); 이러한 부분 문자열에는 문서 유형에 대해 설명합니다. 부분 문자열 대 한 자세한 내용은 참조 [GetDocString](#getdocstring)합니다. 이 문자열 리소스를 응용 프로그램의 리소스 파일에서 찾을 수 있습니다. 예를 들어:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 '\N' 문자로 시작 하는 첫 번째 하위 문자열이 MDI 응용 프로그램에 대 한 사용 되지 않으며 있으므로 포함 되지 않은 때문입니다. 문자열 편집기;를 사용 하 여이 문자열을 편집할 수 있습니다. 전체 문자열 7 개 항목을 구분이 아니라 문자열 편집기에서 단일 항목으로 표시 됩니다.  
  
 *pDocClass*  
 가리키는 `CRuntimeClass` 문서 클래스의 개체입니다. 이 클래스는는 `CDocument`-문서를 나타내기 위해 정의한 클래스를 파생 합니다.  
  
 *pFrameClass*  
 가리키는 `CRuntimeClass` 프레임 창 클래스의 개체입니다. 될 수 있는이 클래스는 `CFrameWnd`-파생 클래스가 될 수 있습니다 또는 `CFrameWnd` 자체 주 프레임 창에 대 한 기본 동작을 수행 합니다.  
  
 *pViewClass*  
 가리키는 `CRuntimeClass` 뷰 클래스의 개체입니다. 이 클래스는는 `CView`-문서를 표시 하기 위해 정의 하는 클래스를 파생 합니다.  
  
### <a name="remarks"></a>설명  
 이 멤버 함수를 사용 하 여 생성 하는 `CDocTemplate` 개체입니다. 동적으로 할당 한 `CDocTemplate` 개체를 전달 [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) 에서 `InitInstance` 응용 프로그램 클래스의 멤버 함수입니다.  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 이 열린 문서 모두 닫기에 함수를 호출 합니다.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>매개 변수  
 *bEndSession*  
 사용되지 않습니다.  
  
### <a name="remarks"></a>설명  
 이 멤버 함수는 일반적으로 파일 종료 명령의 일부로 사용 됩니다. 이 함수의 기본 구현에서는 호출 하 여 [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) 멤버 함수 및 삭제 하는 문서의 데이터 다음 문서에 연결 된 모든 보기에 대 한 프레임 창을 닫습니다.  
  
 사용자가 문서를 닫기 전에 특별 한 정리 작업을 수행 하려는 경우이 함수를 재정의 합니다. 예를 들어 문서 데이터베이스의 레코드를 나타내는 경우이 함수는 데이터베이스를 재정의 하는 것이 좋습니다.  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 이 문서 템플릿에 연결 된 유형의 새 문서를이 멤버 함수를 호출 합니다.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>반환 값  
 새로 만든된 문서에 대 한 포인터 또는 **NULL** 오류가 발생 합니다.  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 문서 및 보기를 포함 하는 새로운 프레임 창을 만듭니다.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>매개 변수  
 *pDoc*  
 새 프레임 창 참조 해야 하는 문서입니다. 수 **NULL**합니다.  
  
 *광폭 한*  
 새 프레임 창을 기반으로는 프레임 창입니다. 수 **NULL**합니다.  
  
### <a name="return-value"></a>반환 값  
 새로 만든된 프레임 창에 대 한 포인터 또는 **NULL** 오류가 발생 합니다.  
  
### <a name="remarks"></a>설명  
 `CreateNewFrame` 사용 하 여는 `CRuntimeClass` 뷰와 연결 된 문서를 사용 하 여 새 프레임 창 개체를 만들려면 생성자에 전달 된 개체입니다. 경우는 *pDoc* 매개 변수는 **NULL**, 프레임 워크는 추적 메시지를 출력 합니다.  
  
 *광폭 한* 매개 변수를 사용 하는 새 창 명령을 구현 합니다. 프레임 창을 새로운 프레임 창을 모델링을 제공 합니다. 새 프레임 창은 대개 보이지 않는 만들어집니다. 새 파일 및 파일 열기 표준 프레임 워크 구현 외부 프레임 창을 만들려면이 함수를 호출 합니다.  
  
##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame  
 OLE 프레임 창을 만듭니다.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>매개 변수  
 *pParentWnd*  
 프레임의 부모 창에 대 한 포인터입니다.  
  
 *pDoc*  
 새 OLE 프레임 창이 문서에 대 한 포인터를 참조 해야 합니다.  
  
 *bCreateView*  
 보기 프레임 함께 만들 것인지를 결정 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 프레임 창에 대 한 포인터 그렇지 않으면 **NULL**합니다.  
  
### <a name="remarks"></a>설명  
 경우 *bCreateView* 0 이면 빈 프레임 만들어집니다.  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 문서 종류와 관련 된 문자열을 검색 합니다.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 *rString*  
 에 대 한 참조는 `CString` 함수에서 반환 된 문자열을 포함 하는 개체입니다.  
  
 *index*  
 문서 종류를 설명 하는 문자열에서 검색 하 고 부분 문자열의 인덱스입니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.  
  
- **CDocTemplate::windowTitle** 응용 프로그램 창의 제목 표시줄 (예: "Microsoft Excel")에 나타나는 이름입니다. SDI 응용 프로그램에 대 한 문서 서식 파일에만 제공 합니다.  
  
- **CDocTemplate::docName** 기본 문서 이름 (예: "시트")에 대 한 루트입니다. 사용자 (예: "Sheet1" 또는 "Sheet2")의 파일 메뉴에서 새로 만들기 명령을 선택 때마다이 루트는 수를 더한 날이 형식의 새 문서의 기본 이름에 사용 됩니다. 지정 하지 않으면 "제목 없음"은 기본적으로 사용 됩니다.  
  
- **CDocTemplate::fileNewName** 이 문서 종류 이름입니다. 응용 프로그램이 둘 이상의 형식의 문서를 지 원하는 경우이 문자열은 새 파일 대화 상자 (예: "워크시트")에 표시 됩니다. 지정 하지 않으면 문서 유형에 액세스할 수 없는 경우 새 파일 명령을 사용 하 여  
  
- **CDocTemplate::filterName** 은 문서 유형과이 유형의 문서를 일치 하는 와일드 카드 필터를 설명 합니다. 이 문자열은 파일 열기 대화 상자 (예를 들어 "워크시트 (*.xls)")의 파일 형식 드롭다운 목록에 표시 됩니다. 지정 하지 않으면 문서 유형에 액세스할 수 없는 경우 파일 열기 명령을 사용 하 여  
  
- **CDocTemplate::filterExt** (예: ".xls")이 형식의 문서에 대 한 확장입니다. 지정 하지 않으면 문서 유형에 액세스할 수 없는 경우 파일 열기 명령을 사용 하 여  
  
- **CDocTemplate::regFileTypeId** Windows에서 유지 관리 하는 등록 데이터베이스에 저장 될 문서 유형에 대 한 식별자입니다. 이 문자열은 내부 전용입니다 (예: "ExcelWorksheet"). 지정 하지 않으면 문서 종류는 Windows 파일 관리자에 등록할 수 없습니다.  
  
- **CDocTemplate::regFileTypeName** 등록 데이터베이스에 저장 될 문서 형식의 이름입니다. 이 문자열 (예를 들어 "Microsoft Excel 워크시트") 등록 데이터베이스에 액세스 하는 응용 프로그램의 대화 상자에 표시 될 수 있습니다.  
  
### <a name="return-value"></a>반환 값  
 지정된 된 부분 문자열 발견 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 문서 종류를 설명 하는 특정 부분 문자열을 검색 하려면이 함수를 호출 합니다. 이러한 부분 문자열이 포함 된 문자열 문서 서식 파일에 저장 되 고 응용 프로그램에 대 한 리소스 파일에는 문자열에서 파생 됩니다. 프레임 워크에는 응용 프로그램의 사용자 인터페이스에 필요한 문자열을 가져오려면이 함수를 호출 합니다. 프레임 워크는 Windows 등록 데이터베이스에 항목을 추가할 때 또한이 함수를 호출 응용 프로그램의 문서에 대 한 파일 이름 확장명을 지정한 경우 이렇게 하면 문서에 Windows 파일 관리자에서 열 수 있습니다.  
  
 고유한 클래스를 파생 하는 경우에이 함수를 호출 `CDocTemplate`합니다.  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 이 템플릿에 연결 된 첫 번째 문서 위치를 검색 합니다.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>반환 값  
 A **위치** ;이 문서 템플릿에 연결 된 문서 목록에서 반복 하는 데 사용할 수 있는 값 또는 **NULL** 목록이 비어 있는 경우.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하 여이 템플릿에 연결 된 문서 목록에서 첫 번째 문서 위치를 가져옵니다. 사용 하 여는 **위치** 값에 대 한 인수로 [CDocTemplate::GetNextDoc](#getnextdoc) 문서 템플릿과 연결 된 목록에서 반복 하 합니다.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) 및 [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) 둘 다이 순수 가상 함수를 재정의 합니다. 모든 클래스에서 파생 `CDocTemplate` 이 함수를 재정의 해야 합니다.  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 로 식별 되는 목록 요소 검색 *Rpo*, 다음 설정 *Rpo* 에 **위치** 목록에서 다음 항목의 값입니다.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>반환 값  
 이 템플릿에 연결 된 문서 목록에서 다음 문서에 대 한 포인터입니다.  
  
### <a name="parameters"></a>매개 변수  
 *Rpo*  
 에 대 한 참조는 **위치** 대 한 이전 호출에서 반환 된 값 [GetFirstDocPosition](#getfirstdocposition) 또는 `GetNextDoc`합니다.  
  
### <a name="remarks"></a>설명  
 검색된 된 요소는 목록에서 마지막 다음 새 값의 경우 *Rpo* 로 설정 된 **NULL**합니다.  
  
 사용할 수 있습니다 `GetNextDoc` 정방향으로 반복 루프를 호출 하 여 초기 위치를 설정 하는 경우에 [GetFirstDocPosition](#getfirstdocposition)합니다.  
  
 확인 해야 하면 **위치** 값 목록에서 올바른 위치를 나타냅니다. 유효 하지 않으면 Microsoft Foundation Class 라이브러리의 디버그 버전 어설션 합니다.  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 프레임 창을 초기화 하 고 필요에 따라 표시 되도록 합니다.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 *pFrame*  
 프레임 창-초기 업데이트가 필요한입니다.  
  
 *pDoc*  
 프레임이 연결 되는 문서입니다. 수 **NULL**합니다.  
  
 *bMakeVisible*  
 표시 되 고 활성 프레임 수 있는지 여부를 나타냅니다.  
  
### <a name="remarks"></a>설명  
 호출 **IntitialUpdateFrame** 새 프레임을 만든 후 `CreateNewFrame`합니다. 수신 하도록 해당 프레임 창에는 뷰에이 함수를 호출 하면 해당 `OnInitialUpdate` 호출 합니다. 또한 발생 한 경우 하지 이전에 활성 뷰, 프레임 창의 기본 보기 활성화 될; 기본 뷰는 자식 id가 **AFX_IDW_PANE_FIRST**합니다. 마지막으로, 프레임 창이 표시 되기 경우 `bMakeVisible` 0이 아닙니다. 경우 *bMakeVisible* 가 0 인 현재 포커스 및 프레임 창의 표시 상태 변경 되지 것입니다.  
  
 새 파일 및 파일 열기의 프레임 워크의 구현을 사용 하는 경우이 함수를 호출할 필요는 없습니다.  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 에 대 한 리소스 로드는 지정 된 `CDocTemplate` 또는 파생 클래스입니다.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>설명  
 이 멤버 함수에 대 한 리소스를 로드 하는 프레임 워크에서 호출 됩니다는 주어진 `CDocTemplate` 또는 클래스를 파생 합니다. 일반적으로 이라고 생성 되는 동안 제외 하 고 템플릿을 전체적으로 생성 되는 경우. 경우에 대 한 호출 `LoadTemplate` 까지 연기 [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) 호출 됩니다.  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 문서 종류와이 서식 파일 간의 일치에 대 한 신뢰도의 정도 결정합니다.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>매개 변수  
 *lpszPathName*  
 결정 해야 하는 형식이 파일의 경로 이름입니다.  
  
 *rpDocMatch*  
 일치 하는 문서에서 지정한 파일이 있으면이 할당 된 문서에 대 한 포인터 *lpszPathName* 가 이미 열려 있습니다.  
  
### <a name="return-value"></a>반환 값  
 값은 **신뢰도** 다음과 같이 정의 된 열거:  
  
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
 이 함수를 사용 하 여 사용할 파일을 열기 위한 문서 서식 파일의 형식을 결정 합니다. 응용 프로그램에서 여러 파일 형식의 지 원하는 경우 예를 들어 하는 데이 함수는 사용할 수 있는 문서 템플릿의 호출 하 여 지정된 된 파일에 적합 한지 결정 `MatchDocType` 차례로에 따라 템플릿을 선택 하 고에서 각 서식 파일 반환 되는 신뢰성 값입니다.  
  
 으로 지정한 파일이 있으면 *lpszPathName* 가 이미 열려이 함수는 반환 **CDocTemplate::yesAlreadyOpen** 파일의 복사 **CDocument** 개체는 개체에 *rpDocMatch*합니다.  
  
 파일에서 확장 되지만 열려 있지 않으면 *lpszPathName* 로 지정 된 확장명과 일치 **CDocTemplate::filterExt**,이 함수는 반환 **CDocTemplate::yesAttemptNative** 설정 *rpDocMatch* 를 **NULL**합니다. 대 한 자세한 내용은 **CDocTemplate::filterExt**, 참조 [CDocTemplate::GetDocString](#getdocstring)합니다.  
  
 함수가 반환 하는 경우에 두 경우 모두이 true 이면 **CDocTemplate::yesAttemptForeign**합니다.  
  
 기본 구현은 반환 하지 않는 **CDocTemplate::maybeAttemptForeign** 또는 **CDocTemplate::maybeAttemptNative**합니다. 이 두 값에서 사용 하 여 응용 프로그램에 적절 한 형식 일치 논리를 구현 하려면이 함수를 재정의 하는 **신뢰도** 열거 합니다.  
  
##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile  
 경로 의해 지정 된 파일을 엽니다.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *lpszPathName*  
 문서를 열 수를 포함 하는 파일의 경로에 대 한 포인터입니다.  
  
 [in] *bAddToMRU*  
 `TRUE` 문서가; 가장 최근에 사용한 파일 중 하나를 나타냅니다. `FALSE` 문서가 아닌 가장 최근에 사용한 파일 중 하나를 나타냅니다.  
  
### <a name="return-value"></a>반환 값  
 해당 파일에서 명명 된 문서에 대 한 포인터 *lpszPathName*; `NULL` 실패 합니다.  
  
### <a name="remarks"></a>설명  
 해당 경로 지정 하 여 파일을 열고 *lpszPathName*합니다. 경우 *lpszPathName* 은 `NULL`,이 템플릿에 연결 된 형식의 문서를 포함 하는 새 파일이 생성 됩니다.  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 가 가리키는 문서를 제거 *pDoc* 이 템플릿에 연결 된 문서 목록에서 합니다.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>매개 변수  
 *pDoc*  
 제거할 문서에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 파생된 클래스 `CMultiDocTemplate` 및 `CSingleDocTemplate` 이 함수를 재정의 합니다. 고유한 문서 템플릿 클래스를 파생 하는 경우 `CDocTemplate`, 파생된 클래스에서이 함수를 재정의 해야 합니다.  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 수정 된 모든 문서를 저장 합니다.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>반환 값  
 비-성공 시 0; 그렇지 않으면 0입니다.  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo  
 내부 OLE 항목을 편집 하는 경우 OLE 컨테이너에 대 한 리소스를 결정 합니다.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>매개 변수  
 *nIDOleInPlaceContainer*  
 포함된 된 개체가 활성화 될 때 사용 하는 리소스의 ID입니다.  
  
### <a name="remarks"></a>설명  
 OLE 개체를 활성화 될 때 사용 되는 리소스를 설정 하려면이 함수를 호출 합니다. 이러한 리소스는 메뉴 및 액셀러레이터 키 테이블에 포함 될 수 있습니다. 이 함수는 일반적으로 호출 됩니다는 [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 응용 프로그램의 기능입니다.  
  
 연결 된 메뉴 *nIDOleInPlaceContainer* 컨테이너 응용 프로그램의 메뉴를 사용 하 여 병합 활성화 된 전체 항목의 메뉴를 사용할 수 있는 구분 기호를 포함 합니다. 서버 및 컨테이너 메뉴 병합 하는 방법에 대 한 자세한 내용은 문서 참조 [메뉴 및 리소스 (OLE)](../../mfc/menus-and-resources-ole.md)합니다.  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 문서의 기본 제목을 로드 하 고 문서의 제목 표시줄에 표시 하려면이 함수를 호출 합니다.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>매개 변수  
 *pDocument*  
 설정할 제목은 문서에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 기본 제목에 대 한 자세한 내용은 참조에 대 한 설명을 **CDocTemplate::docName** 에 [CDocTemplate::GetDocString](#getdocstring)합니다.  
  
##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo  
 서버 문서는 포함 되어 있거나 현재 위치를 편집할 때 리소스 및 클래스를 결정 합니다.  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 *nIDOleEmbedding*  
 별도 창에서 포함된 된 개체를 열 때 사용 하는 리소스의 ID입니다.  
  
 *nIDOleInPlaceServer*  
 내부 활성화 하는 경우 포함된 된 개체를 사용 하는 리소스의 ID입니다.  
  
 *pOleFrameClass*  
 에 대 한 포인터는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 내부 활성화를 수행할지 때 만든 프레임 창 개체에 대 한 클래스 정보를 포함 하는 구조입니다.  
  
 *pOleViewClass*  
 에 대 한 포인터는 `CRuntimeClass` 내부 활성화의 발생 될 때 만들어지는 보기 개체에 대 한 클래스 정보를 포함 하는 구조입니다.  
  
### <a name="remarks"></a>설명  
 사용자는 포함된 된 개체의 정품 인증을 요청 하면 서버 응용 프로그램에서 사용할 수 있는 리소스를 식별 하려면이 멤버 함수를 호출 합니다. 메뉴 및 액셀러레이터 키 테이블의 다음이 리소스 구성 됩니다. 이 함수는 일반적으로 호출 됩니다는 `InitInstance` 응용 프로그램의 합니다.  
  
 연결 된 메뉴 *nIDOleInPlaceServer* 컨테이너 메뉴와 병합 하는 서버 메뉴를 사용할 수 있는 구분 기호를 포함 합니다. 서버 및 컨테이너 메뉴 병합 하는 방법에 대 한 자세한 내용은 문서 참조 [메뉴 및 리소스 (OLE)](../../mfc/menus-and-resources-ole.md)합니다.  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 서식 있는 미리 보기에 사용 되는 자식 프레임을 만듭니다.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>매개 변수  
 *pParentWnd*  
 부모 창 (일반적으로 셸에서 제공)에 대 한 포인터입니다.  
  
 *pDoc*  
 문서 개체에 해당 내용이 미리 보기 됩니다에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 유효한 포인터는 `CFrameWnd` 개체 또는 `NULL` 만들기에 실패 합니다.  
  
### <a name="remarks"></a>설명  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 프로세스 미리 보기 처리기의 부재를 설정합니다.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 *nIDPreviewFrame*  
 미리 보기 프레임의 리소스 ID를 지정합니다.  
  
 *pPreviewFrameClass*  
 미리 보기 프레임의 런타임 클래스 정보 구조에 대 한 포인터를 지정합니다.  
  
 *pPreviewViewClass*  
 미리 보기의 런타임 클래스 정보 구조에 대 한 포인터를 지정합니다.  
  
### <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate 클래스](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate 클래스](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument 클래스](../../mfc/reference/cdocument-class.md)   
 [CView 클래스](../../mfc/reference/cview-class.md)   
 [CScrollView 클래스](../../mfc/reference/cscrollview-class.md)   
 [CEditView 클래스](../../mfc/reference/ceditview-class.md)   
 [CFormView 클래스](../../mfc/reference/cformview-class.md)   
 [CFrameWnd 클래스](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd 클래스](../../mfc/reference/cmdichildwnd-class.md)

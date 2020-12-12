---
description: '자세히 알아보기: COleDocObjectItem 클래스'
title: COleDocObjectItem 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: e483c614f8bc7558a827c51889bbffa7da7419b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227223"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 클래스

액티브 문서 포함을 구현합니다.

## <a name="syntax"></a>구문

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDocObjectItem:: COleDocObjectItem](#coledocobjectitem)|항목을 생성 `COleDocObject` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDocObjectItem::D oDefaultPrinting](#dodefaultprinting)|기본 프린터 설정을 사용 하 여 컨테이너 응용 프로그램의 문서를 인쇄 합니다.|
|[COleDocObjectItem:: ExecCommand](#execcommand)|사용자가 지정한 명령을 실행 합니다.|
|[COleDocObjectItem:: GetActiveView](#getactiveview)|문서의 활성 뷰를 검색 합니다.|
|[COleDocObjectItem:: GetPageCount](#getpagecount)|컨테이너 응용 프로그램의 문서에 있는 페이지 수를 검색 합니다.|
|[COleDocObjectItem:: OnPreparePrinting](#onprepareprinting)|인쇄를 위해 컨테이너 응용 프로그램의 문서를 준비 합니다.|
|[COleDocObjectItem:: OnPrint](#onprint)|컨테이너 응용 프로그램의 문서를 인쇄 합니다.|
|[COleDocObjectItem:: QueryCommand](#querycommand)|사용자 인터페이스 이벤트에 의해 생성되는 하나 이상 명령의 상태를 쿼리합니다.|
|[COleDocObjectItem:: Release](#release)|OLE 연결 된 항목에 대 한 연결을 해제 하 고 열린 경우 닫습니다. 클라이언트 항목을 제거 하지 않습니다.|

## <a name="remarks"></a>설명

MFC에서 활성 문서는 다음과 같은 차이를 포함 하는 일반적인 내부 편집 가능 포함과 유사 하 게 처리 됩니다.

- `COleDocument`파생 클래스는 현재 포함 된 항목의 목록을 계속 유지 관리 하지만 이러한 항목은 파생 항목 일 수 있습니다 `COleDocObjectItem` .

- 활성 문서는 활성 상태인 경우 활성 상태인 경우 뷰의 전체 클라이언트 영역을 차지 합니다.

- 액티브 문서 컨테이너에는 **도움말** 메뉴에 대 한 모든 권한이 있습니다.

- **도움말** 메뉴에는 액티브 문서 컨테이너와 서버 모두에 대 한 메뉴 항목이 포함 되어 있습니다.

액티브 문서 컨테이너는 **도움말** 메뉴를 소유 하기 때문에 서버에 서버 **도움말** 메뉴 메시지를 전달 하는 역할을 담당 합니다. 이 통합은에 의해 처리 됩니다 `COleDocObjectItem` .

메뉴 병합 및 활성 문서 활성화에 대 한 자세한 내용은 [액티브 문서 포함](../../mfc/active-document-containment.md)개요를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a> COleDocObjectItem:: COleDocObjectItem

이 멤버 함수를 호출 하 여 `COleDocObjectItem` 개체를 초기화 합니다.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>매개 변수

*pContainerDoc*<br/>
활성 문서 컨테이너 역할을 하는 개체에 대 한 포인터 `COleDocument` 입니다. IMPLEMENT_SERIALIZE를 사용 하려면이 매개 변수가 NULL 이어야 합니다. 일반적으로 OLE 항목은 NULL이 아닌 문서 포인터를 사용 하 여 생성 됩니다.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a> COleDocObjectItem::D oDefaultPrinting

기본 설정을 사용 하 여 프레임 워크에서 문서에 대해 호출 됩니다.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>매개 변수

*pCaller*<br/>
인쇄 명령을 보내는 [CView](../../mfc/reference/cview-class.md) 개체에 대 한 포인터입니다.

*pInfo*<br/>
인쇄할 작업을 설명 하는 [Cprintinfo](../../mfc/reference/cprintinfo-structure.md) 개체에 대 한 포인터입니다.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a> COleDocObjectItem:: ExecCommand

이 멤버 함수를 호출 하 여 사용자가 지정한 명령을 실행 합니다.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>매개 변수

*nCmdID*<br/>
실행할 명령의 식별자입니다. *PguidCmdGroup* 로 식별 되는 그룹에 있어야 합니다.

*nCmdExecOpt*<br/>
명령 실행 옵션을 지정 합니다. 기본적으로는 사용자에 게 메시지를 표시 하지 않고 명령을 실행 하도록 설정 합니다. 값 목록은 [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) 을 참조 하십시오.

*pguidCmdGroup*<br/>
명령 그룹의 고유 식별자입니다. 기본적으로 표준 그룹을 지정 하는 NULL입니다. *Ncmdid* 에 전달 된 명령은 그룹에 속해야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 반환 합니다. 그렇지 않으면 다음 오류 코드 중 하나를 반환 합니다.

|값|설명|
|-----------|-----------------|
|E_UNEXPECTED|예기치 않은 오류가 발생했습니다.|
|E_FAIL|오류가 발생했습니다.|
|E_NOTIMPL|MFC 자체가 명령을 변환 하 고 디스패치할 수 있음을 나타냅니다.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* 가 NULL이 아닌 경우 인식할 수 있는 명령 그룹을 지정 하지 않습니다.|
|OLECMDERR_E_NOTSUPPORTED|*Ncmdid* 는 그룹 pgroup에서 올바른 명령으로 인식 되지 않습니다.|
|OLECMDERR_DISABLED|*Ncmdid* 로 식별 된 명령은 사용 하지 않도록 설정 되어 있으며 실행할 수 없습니다.|
|OLECMDERR_NOHELP|호출자가 *Ncmdid* 로 식별 된 명령에 대 한 도움말을 요청 했지만 사용할 수 있는 도움말이 없습니다.|
|OLECMDERR_CANCELLED|사용자가 실행을 취소 했습니다.|

### <a name="remarks"></a>설명

*PguidCmdGroup* 와 *ncmdid* 매개 변수는 함께 호출할 명령을 고유 하 게 식별 합니다. *NCmdExecOpt* 매개 변수는 수행할 정확한 동작을 지정 합니다.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a> COleDocObjectItem:: GetActiveView

이 멤버 함수를 호출 하 여 `IOleDocumentView` 현재 활성 뷰의 인터페이스에 대 한 포인터를 가져옵니다.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>반환 값

현재 활성 뷰의 [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) 인터페이스에 대 한 포인터입니다. 현재 보기가 없으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

반환 된 포인터의 참조 횟수는 `IOleDocumentView` 이 함수에서 반환 되기 전에 증가 하지 않습니다.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a> COleDocObjectItem:: GetPageCount

문서의 페이지 수를 검색 하려면이 멤버 함수를 호출 합니다.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>매개 변수

*pnFirstPage*<br/>
문서의 첫 페이지 번호에 대 한 포인터입니다. 호출자에 게이 숫자가 필요 하지 않음을 나타내는 NULL 일 수 있습니다.

*pcPages*<br/>
문서의 총 페이지 수에 대 한 포인터입니다. 호출자에 게이 숫자가 필요 하지 않음을 나타내는 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a> COleDocObjectItem:: OnPreparePrinting

이 멤버 함수는 문서 인쇄를 준비 하기 위해 프레임 워크에서 호출 됩니다.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>매개 변수

*pCaller*<br/>
인쇄 명령을 보내는 [CView](../../mfc/reference/cview-class.md) 개체에 대 한 포인터입니다.

*pInfo*<br/>
인쇄할 작업을 설명 하는 [Cprintinfo](../../mfc/reference/cprintinfo-structure.md) 개체에 대 한 포인터입니다.

*bPrintAll*<br/>
전체 문서를 인쇄할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a> COleDocObjectItem:: OnPrint

이 멤버 함수는 문서를 인쇄 하기 위해 프레임 워크에서 호출 됩니다.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>매개 변수

*pCaller*<br/>
인쇄 명령을 보내는 CView 개체에 대 한 포인터입니다.

*pInfo*<br/>
인쇄할 작업을 설명 하는 [Cprintinfo](../../mfc/reference/cprintinfo-structure.md) 개체에 대 한 포인터입니다.

*bPrintAll*<br/>
전체 문서를 인쇄할지 여부를 지정 합니다.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a> COleDocObjectItem:: QueryCommand

사용자 인터페이스 이벤트에 의해 생성되는 하나 이상 명령의 상태를 쿼리합니다.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>매개 변수

*nCmdID*<br/>
쿼리 중인 명령의 식별자입니다.

*pdwStatus*<br/>
쿼리 결과로 반환 되는 플래그에 대 한 포인터입니다. 가능한 값 목록은 [Olecmdf](/windows/win32/api/docobj/ne-docobj-olecmdf)를 참조 하세요.

*pCmdText*<br/>
단일 명령에 대 한 이름 및 상태 정보를 반환할 [Olecmdtext](/windows/win32/api/docobj/ns-docobj-olecmdtext) 구조체에 대 한 포인터입니다. 호출자에 게이 정보가 필요 하지 않음을 나타내는 NULL 일 수 있습니다.

*pguidCmdGroup*<br/>
명령 그룹의 고유 식별자입니다. 표준 그룹을 지정 하는 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

반환 값의 전체 목록은 Windows SDK의 [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) 를 참조 하세요.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) 메서드의 기능을 에뮬레이트합니다.

## <a name="coledocobjectitemrelease"></a><a name="release"></a> COleDocObjectItem:: Release

OLE 연결 된 항목에 대 한 연결을 해제 하 고 열린 경우 닫습니다. 클라이언트 항목을 제거 하지 않습니다.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>매개 변수

*dwCloseOption*<br/>
OLE 항목이 로드 된 상태로 반환 될 때 저장 되는 상황을 지정 하는 플래그입니다. 가능한 값 목록은 [COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close)를 참조 하세요.

### <a name="remarks"></a>설명

클라이언트 항목을 제거 하지 않습니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 클래스](../../mfc/reference/coleclientitem-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 클래스](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem 클래스](../../mfc/reference/cdocobjectserveritem-class.md)

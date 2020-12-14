---
description: '자세히 알아보기: CDataRecoveryHandler 클래스'
title: CDataRecoveryHandler 클래스
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: 72189916f4555152ccc8997600d8426e188bb65c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222140"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 클래스

`CDataRecoveryHandler`응용 프로그램이 예기치 않게 종료 되 면 자동으로 저장 문서를 저장 하 고 복원 합니다.

## <a name="syntax"></a>구문

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|`CDataRecoveryHandler` 개체를 생성합니다.|

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[CDataRecoveryHandler:: AutosaveAllDocumentInfo](#autosavealldocumentinfo)|클래스에 등록 된 각 파일을 자동으로 저장 `CDataRecoveryHandler` 합니다.|
|[CDataRecoveryHandler:: AutosaveDocumentInfo](#autosavedocumentinfo)|지정 된 문서를 자동으로 저장 합니다.|
|[CDataRecoveryHandler:: CreateDocumentInfo](#createdocumentinfo)|열린 문서 목록에 문서를 추가 합니다.|
|[CDataRecoveryHandler::D eleteAllAutosavedFiles](#deleteallautosavedfiles)|현재 자동 저장 된 파일을 모두 삭제 합니다.|
|[CDataRecoveryHandler::D eleteAutosavedFile](#deleteautosavedfile)|지정 된 자동 저장 된 파일을 삭제 합니다.|
|[CDataRecoveryHandler:: GenerateAutosaveFileName](#generateautosavefilename)|제공 된 문서 파일 이름과 연결 된 자동 저장 파일의 이름을 생성 합니다.|
|[CDataRecoveryHandler:: GetAutosaveInterval](#getautosaveinterval)|자동 저장 시도 간격을 반환 합니다.|
|[CDataRecoveryHandler:: GetAutosavePath](#getautosavepath)|자동 저장 된 파일의 경로를 반환 합니다.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|개체에서 문서 이름을 검색 `CDocument` 합니다.|
|[CDataRecoveryHandler:: GetNormalDocumentTitle](#getnormaldocumenttitle)|지정 된 문서에 대 한 일반 제목을 검색 합니다.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|복구 된 문서의 제목을 만들고 반환 합니다.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|응용 프로그램에 대 한 고유 다시 시작 식별자를 검색 합니다.|
|[CDataRecoveryHandler:: GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|가 `CDataRecoveryHandler` 현재 유휴 루프에서 자동 저장을 수행 하는지 여부를 나타냅니다.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|다시 시작 관리자가 응용 프로그램을 종료할지 여부를 나타냅니다.|
|[CDataRecoveryHandler:: Initialize](#initialize)|`CDataRecoveryHandler`을 초기화합니다.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|자동으로 저장 된 각 문서에 대 한 대화 상자를 사용자에 게 표시 합니다 `CDataRecoveryHandler` . 이 대화 상자에는 사용자가 자동으로 저장 된 문서를 복원할지 여부를 결정 합니다.|
|[CDataRecoveryHandler:: ReadOpenDocumentList](#readopendocumentlist)|레지스트리에서 열린 문서 목록을 로드 합니다.|
|[CDataRecoveryHandler:: RemoveDocumentInfo](#removedocumentinfo)|열린 문서 목록에서 제공 된 문서를 제거 합니다.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|이전에 열린 문서를 엽니다.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|사용자 입력에 따라 자동 저장 된 문서를 복원 합니다.|
|[CDataRecoveryHandler:: SaveOpenDocumentList](#saveopendocumentlist)|열려 있는 문서의 현재 목록을 Windows 레지스트리에 저장 합니다.|
|[CDataRecoveryHandler:: SetAutosaveInterval](#setautosaveinterval)|자동 저장 주기 시간 (밀리초)을 설정 합니다.|
|[CDataRecoveryHandler:: SetAutosavePath](#setautosavepath)|자동 저장 된 파일이 저장 되는 디렉터리를 설정 합니다.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|의이 인스턴스에 대 한 고유 다시 시작 식별자를 설정 합니다 `CDataRecoveryHandler` .|
|[CDataRecoveryHandler:: SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|에서 `CDataRecoveryHandler` 현재 유휴 주기 동안 열려 있는 문서 정보를 Windows 레지스트리에 저장할지 여부를 설정 합니다.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|응용 프로그램의 이전 종료를 다시 시작 관리자에 의해 발생 했는지 여부를 설정 합니다.|
|[CDataRecoveryHandler:: UpdateDocumentInfo](#updatedocumentinfo)|사용자가 문서를 저장 했으므로 문서에 대 한 정보를 업데이트 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|m_bRestoringPreviousOpenDocs|데이터 복구 핸들러가 이전에 열린 문서를 다시 열 지 여부를 나타냅니다.|
|m_bSaveDocumentInfoOnIdle|데이터 복구 처리기가 다음 유휴 루프에서 문서를 자동으로 저장할지 여부를 나타냅니다.|
|m_bShutdownByRestartManager|다시 시작 관리자에서 응용 프로그램을 종료할지 여부를 나타냅니다.|
|m_dwRestartManagerSupportFlags|다시 시작 관리자에서 응용 프로그램에 대해 제공 하는 지원을 나타내는 플래그입니다.|
|m_lstAutosavesToDelete|원본 문서를 닫을 때 삭제 되지 않은 자동 저장 된 파일의 목록입니다. 응용 프로그램이 종료 되 면 다시 시작 관리자가 파일 삭제를 다시 시도 합니다.|
|m_mapDocNameToAutosaveName|자동 저장 된 파일 이름에 대 한 문서 이름 맵|
|m_mapDocNameToDocumentPtr|[CDocument](../../mfc/reference/cdocument-class.md) 포인터에 대 한 문서 이름의 맵입니다.|
|m_mapDocNameToRestoreBool|자동 저장 된 문서를 복원할지 여부를 나타내는 부울 매개 변수에 대 한 문서 이름 맵|
|m_mapDocumentPtrToDocName|`CDocument`문서 이름에 대 한 포인터의 맵입니다.|
|m_mapDocumentPtrToDocTitle|`CDocument`문서 제목에 대 한 포인터의 맵입니다. 이러한 제목은 파일을 저장 하는 데 사용 됩니다.|
|m_nAutosaveInterval|Autosaves 사이의 시간 (밀리초)입니다.|
|m_nTimerID|자동 저장 타이머의 식별자입니다.|
|m_strAutosavePath|자동 저장 된 문서를 저장 하는 위치입니다.|
|m_strRestartIdentifier|다시 시작 관리자에 대 한 GUID의 문자열 표현입니다.|

## <a name="remarks"></a>설명

다시 시작 관리자는 클래스를 사용 하 여 `CDataRecoveryHandler` 열려 있는 모든 문서를 추적 하 고 필요한 경우이를 자동으로 저장 합니다. 자동 저장을 사용 하려면 [CDataRecoveryHandler:: SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) 메서드를 사용 합니다. 이 메서드는 `CDataRecoveryHandler` 다음 유휴 루프에서 자동 저장을 수행 하도록에 지시 합니다. `SetSaveDocumentInfoOnIdle`에서 `CDataRecoveryHandler` 자동 저장을 수행 해야 하는 경우 다시 시작 관리자가를 호출 합니다.

클래스의 모든 메서드는 `CDataRecoveryHandler` 가상입니다. 이 클래스의 메서드를 재정의 하 여 사용자 지정 데이터 복구 처리기를 만듭니다. 사용자 고유의 데이터 복구 처리기 또는 다시 시작 관리자를 만들지 않는 한 CDataRecoveryHandler를 인스턴스화하지 않습니다. [CWinApp 클래스](../../mfc/reference/cwinapp-class.md) 는 필요에 `CDataRecoveryHandler` 따라 개체를 만듭니다.

개체를 사용 하려면 먼저 `CDataRecoveryHandler` [CDataRecoveryHandler:: Initialize](#initialize)를 호출 해야 합니다.

`CDataRecoveryHandler`클래스가 다시 시작 관리자와 밀접 하 게 연결 되어 있기 때문에는 `CDataRecoveryHandler` global 매개 변수에 따라 달라 집니다 `m_dwRestartManagerSupportFlags` . 이 매개 변수는 다시 시작 관리자의 사용 권한과 응용 프로그램과 상호 작용 하는 방법을 결정 합니다. 다시 시작 관리자를 기존 응용 프로그램에 통합 하려면 `m_dwRestartManagerSupportFlags` 주 응용 프로그램의 생성자에 적절 한 값을 할당 해야 합니다. 다시 시작 관리자를 사용 하는 방법에 대 한 자세한 내용은 [방법: 다시 시작 관리자 지원 추가](../../mfc/how-to-add-restart-manager-support.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxdatarecovery

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a> CDataRecoveryHandler:: AutosaveAllDocumentInfo

클래스에 등록 된 각 파일을 자동으로 저장 `CDataRecoveryHandler` 합니다.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>반환 값

에서 `CDataRecoveryHandler` 모든 문서를 저장 했으면 TRUE입니다. 문서를 저장 하지 않은 경우 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 저장 해야 하는 문서가 없는 경우 TRUE를 반환 합니다. 또한를 검색 `CWinApp` 하거나 `CDocManager` 응용 프로그램에 대해 오류를 생성 하는 경우 문서를 저장 하지 않고 TRUE를 반환 합니다.

이 메서드를 사용 하려면 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 또는 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL을에서 설정 해야 합니다 `m_dwRestartManagerSupportFlags` . 자세한 내용은 [방법: 다시 시작 관리자 지원 추가](../../mfc/how-to-add-restart-manager-support.md)를 참조 하세요.

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a> CDataRecoveryHandler:: AutosaveDocumentInfo

지정 된 문서를 자동으로 저장 합니다.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 저장할에 대 한 포인터 `CDocument` 입니다.

*bResetModifiedFlag*\
진행 TRUE 이면에서 `CDataRecoveryHandler` *pdocument* 를 수정 하도록 고려 합니다. FALSE는 프레임 워크에서 *Pdocument* 가 수정 되지 않은 것으로 간주 함을 나타냅니다. 이 플래그의 효과에 대 한 자세한 내용은 설명 부분을 참조 하세요.

### <a name="return-value"></a>반환 값

적절 한 플래그가 설정 되 고 *Pdocument* 가 유효한 개체 이면 TRUE `CDocument` 입니다.

### <a name="remarks"></a>설명

각 `CDocument` 개체에는 마지막 저장 이후 변경 되었는지 여부를 나타내는 플래그가 있습니다. [CDocument:: IsModified](../../mfc/reference/cdocument-class.md#ismodified) 를 사용 하 여이 플래그의 상태를 확인 합니다. `CDocument`마지막 저장 이후이 변경 되지 않은 경우 `AutosaveDocumentInfo` 는 해당 문서에 대해 자동으로 저장 된 파일을 삭제 합니다. 문서가 마지막으로 저장 된 후에 변경 된 경우 닫기 전에 문서를 저장 하 라는 메시지가 표시 됩니다.

> [!NOTE]
> *BResetModifiedFlag* 를 사용 하 여 문서 상태를 수정 되지 않은 상태로 변경 하면 저장 되지 않은 데이터가 손실 될 수 있습니다. 프레임 워크가 문서를 수정 되지 않은 것으로 간주 하는 경우 닫을 때 사용자에 게 저장 하 라는 메시지가 표시 되지 않습니다.

*Pdocument* 가 유효한 개체가 아닌 경우이 메서드는 [ASSERT](diagnostic-services.md#assert) 매크로를 사용 하 여 예외를 throw `CDocument` 합니다.

이 메서드를 사용 하려면 *m_dwRestartManagerSupportFlags* 에서 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 또는 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL를 설정 해야 합니다.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a> CDataRecoveryHandler::CDataRecoveryHandler

`CDataRecoveryHandler` 개체를 생성합니다.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>매개 변수

*dwRestartManagerSupportFlags*\
진행 지원 되는 다시 시작 관리자의 옵션을 나타냅니다.

*nAutosaveInterval*\
진행 Autosaves 간의 시간입니다. 이 매개 변수는 밀리초 단위입니다.

### <a name="remarks"></a>설명

새 프로젝트 마법사를 사용 하면 MFC 프레임 워크에서 `CDataRecoveryHandler` 응용 프로그램에 대  한 개체를 자동으로 만듭니다. 데이터 복구 동작 또는 다시 시작 관리자를 사용자 지정 하지 않는 한 개체를 만들지 않아야 합니다 `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a> CDataRecoveryHandler:: CreateDocumentInfo

열린 문서 목록에 문서를 추가 합니다.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 에 대 한 포인터 `CDocument` 입니다. 이 메서드는이에 대 한 문서 정보를 만듭니다 `CDocument` .

### <a name="return-value"></a>반환 값

기본 구현에서는 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 문서를 추가 하기 전에 *Pdocument* 가 문서 목록에 이미 있는지 여부를 확인 합니다. *Pdocument* 가 목록에 이미 있는 경우이 메서드는 *pdocument* 와 연결 된 자동 저장 된 파일을 삭제 합니다.

이 메서드를 사용 하려면 *m_dwRestartManagerSupportFlags* 에서 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 또는 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL를 설정 해야 합니다.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a> CDataRecoveryHandler::D eleteAllAutosavedFiles

현재 자동 저장 된 파일을 모두 삭제 합니다.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 항상 TRUE를 반환 합니다.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a> CDataRecoveryHandler::D eleteAutosavedFile

지정 된 자동 저장 된 파일을 삭제 합니다.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>매개 변수

*strAutosavedFile*\
진행 자동 저장 된 파일 이름을 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드가 자동 저장 된 파일을 삭제할 수 없는 경우 파일의 이름을 목록에 저장 합니다. 의 소멸자는 해당 `CDataRecoveryHandler` 목록에 지정 된 각 자동 저장 된 파일을 삭제 하려고 합니다.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a> CDataRecoveryHandler:: GenerateAutosaveFileName

제공 된 문서 파일 이름과 연결 된 자동 저장 파일의 이름을 생성 합니다.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>매개 변수

*strDocumentName*<br/>
진행 문서 이름을 포함 하는 문자열입니다. `GenerateAutosaveFileName` 에서는이 문서 이름을 사용 하 여 해당 하는 자동 저장 파일 이름을 생성 합니다.

### <a name="return-value"></a>반환 값

*StrDocumentName* 에서 생성 된 자동 저장 파일 이름입니다.

### <a name="remarks"></a>설명

각 문서 이름에는 자동 저장 파일 이름을 사용 하는 일 대 일 매핑이 있습니다.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a> CDataRecoveryHandler:: GetAutosaveInterval

자동 저장 시도 간격을 반환 합니다.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>반환 값

자동 저장 시도 사이의 시간 (밀리초)입니다.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a> CDataRecoveryHandler:: GetAutosavePath

자동 저장 된 파일의 경로를 반환 합니다.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>반환 값

자동 저장 된 문서를 저장 하는 위치입니다.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a> CDataRecoveryHandler::GetDocumentListName

개체에서 문서 이름을 검색 `CDocument` 합니다.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 에 대 한 포인터 `CDocument` 입니다. `GetDocumentListName` 이에서 문서 이름을 검색 `CDocument` 합니다.

### <a name="return-value"></a>반환 값

*Pdocument* 의 문서 이름입니다.

### <a name="remarks"></a>설명

는 `CDataRecoveryHandler` *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr* 및 *m_mapDocNameToRestoreBool* 에서 문서 이름을 키로 사용 합니다. 이러한 매개 변수를 통해에서 `CDataRecoveryHandler` `CDocument` 개체, 자동 저장 파일 이름 및 자동 저장 설정을 모니터링할 수 있습니다.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a> CDataRecoveryHandler:: GetNormalDocumentTitle

지정 된 문서에 대 한 일반 제목을 검색 합니다.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 에 대 한 포인터 `CDocument` 입니다.

### <a name="return-value"></a>반환 값

지정 된 문서의 일반 제목입니다.

### <a name="remarks"></a>설명

문서의 일반 제목은 일반적으로 경로 없는 문서의 파일 이름입니다. 다른 이름 **으로 저장** 대화 상자의 **파일 이름** 필드에 있는 제목입니다.

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a> CDataRecoveryHandler::GetRecoveredDocumentTitle

복구 된 문서의 제목을 만들고 반환 합니다.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>매개 변수

*strDocumentTitle*<br/>
진행 문서의 일반 제목입니다.

### <a name="return-value"></a>반환 값

복구 된 문서 제목입니다.

### <a name="remarks"></a>설명

기본적으로 문서의 복구 된 제목은 **[복구 됨]** 이 추가 된 일반 제목입니다. 에서 `CDataRecoveryHandler` 사용자가 자동으로 저장 된 문서를 복원 하도록 쿼리하면 복구 된 제목이 사용자에 게 표시 됩니다.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a> CDataRecoveryHandler::GetRestartIdentifier

응용 프로그램에 대 한 고유 다시 시작 식별자를 검색 합니다.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>반환 값

고유한 다시 시작 식별자입니다.

### <a name="remarks"></a>설명

Restart 식별자는 응용 프로그램의 각 실행에 대해 고유 합니다.

는 `CDataRecoveryHandler` 현재 열려 있는 문서에 대 한 정보를 레지스트리에 저장 합니다. 다시 시작 관리자는 응용 프로그램을 종료 하 고 다시 시작 하는 경우에 다시 시작 식별자를 제공 합니다 `CDataRecoveryHandler` . 는 `CDataRecoveryHandler` 다시 시작 식별자를 사용 하 여 이전에 열린 문서의 목록을 검색 합니다. 이렇게 하면에서 자동으로 `CDataRecoveryHandler` 저장 된 파일을 찾아 복원할 수 있습니다.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a> CDataRecoveryHandler:: GetSaveDocumentInfoOnIdle

가 `CDataRecoveryHandler` 현재 유휴 루프에서 자동 저장을 수행 하는지 여부를 나타냅니다.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>반환 값

TRUE는 `CDataRecoveryHandler` 현재 유휴 루프의 자동으로 저장을 나타냅니다. FALSE는 그렇지 않음을 나타냅니다.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a> CDataRecoveryHandler::GetShutdownByRestartManager

다시 시작 관리자가 응용 프로그램을 종료할지 여부를 나타냅니다.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>반환 값

TRUE로 설정 하면 다시 시작 관리자가 응용 프로그램을 종료 했음을 나타냅니다. FALSE는 그렇지 않음을 나타냅니다.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a> CDataRecoveryHandler:: Initialize

`CDataRecoveryHandler`을 초기화합니다.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>반환 값

초기화에 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

초기화 프로세스는 레지스트리의 자동 저장 파일 저장 경로를 로드 합니다. `Initialize`메서드가이 디렉터리를 찾을 수 없거나 경로가 NULL 이면가 `Initialize` 실패 하 고가 반환 `FALSE` 됩니다.

응용 프로그램이를 초기화 한 후 [CDataRecoveryHandler:: SetAutosavePath](#setautosavepath) 를 사용 하 여 자동 저장 경로를 변경 합니다 `CDataRecoveryHandler` .

`Initialize`또한 메서드는 다음 자동 저장이 발생 하는 시간을 모니터링 하는 타이머를 시작 합니다. [CDataRecoveryHandler:: SetAutosaveInterval](#setautosaveinterval) 을 사용 하 여 응용 프로그램이을 (를) 초기화 한 후 자동 저장 간격을 변경 합니다 `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a> CDataRecoveryHandler::QueryRestoreAutosavedDocuments

자동으로 저장 된 각 문서에 대 한 대화 상자를 사용자에 게 표시 합니다 `CDataRecoveryHandler` . 이 대화 상자에는 사용자가 자동으로 저장 된 문서를 복원할지 여부를 결정 합니다.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>설명

응용 프로그램이 Unicode 인 경우이 메서드는 사용자에 게 [Ctaskdialog](../../mfc/reference/ctaskdialog-class.md) 를 표시 합니다. 그렇지 않으면 프레임 워크는 [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) 을 사용 하 여 사용자를 쿼리 합니다.

는 `QueryRestoreAutosavedDocuments` 사용자의 모든 응답을 수집한 후 *m_mapDocNameToRestoreBool* 멤버 변수에 정보를 저장 합니다. 이 메서드는 자동 저장 된 문서를 복원 하지 않습니다.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a> CDataRecoveryHandler:: ReadOpenDocumentList

레지스트리에서 열린 문서 목록을 로드 합니다.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>반환 값

TRUE 이면 `ReadOpenDocumentList` 레지스트리에서 하나 이상의 문서에 대 한 정보를 로드 했음을 나타냅니다. FALSE는 문서 정보를 로드 하지 않았음을 나타냅니다.

### <a name="remarks"></a>설명

이 함수는 레지스트리에서 열린 문서 정보를 로드 하 고 *m_mapDocNameToAutosaveName* 멤버 변수에 저장 합니다.

`ReadOpenDocumentList`는 모든 데이터를 로드 한 후 레지스트리에서 문서 정보를 삭제 합니다.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a> CDataRecoveryHandler:: RemoveDocumentInfo

열린 문서 목록에서 제공 된 문서를 제거 합니다.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 제거할 문서에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

*Pdocument* 가 목록에서 제거 되 면 TRUE이 고, 오류가 발생 한 경우 FALSE입니다.

### <a name="remarks"></a>설명

사용자가 문서를 닫으면 프레임 워크에서이 메서드를 사용 하 여 열린 문서 목록에서 문서를 제거 합니다.

`RemoveDocumentInfo`에서 열린 문서 목록에 *pdocument* 를 찾을 수 없는 경우 아무 작업도 수행 하지 않고 TRUE를 반환 합니다.

이 메서드를 사용 하려면 *m_dwRestartManagerSupportFlags* 에서 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 설정 해야 합니다.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a> CDataRecoveryHandler::ReopenPreviousDocuments

이전에 열린 문서를 엽니다.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>반환 값

하나 이상의 문서가 열려 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 이전에 열린 문서를 가장 최근에 저장 한 것을 엽니다. 문서가 저장 되지 않았거나 자동으로 저장 되지 않은 경우 `ReopenPreviousDocuments` 는 해당 파일 형식에 대 한 템플릿을 기반으로 하는 빈 문서를 엽니다.

이 메서드를 사용 하려면 *m_dwRestartManagerSupportFlags* 에서 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 설정 해야 합니다. 이 매개 변수가 설정 되지 않은 경우는 `ReopenPreviousDocuments` 아무 작업도 수행 하지 않고 FALSE를 반환 합니다.

이전에 연 문서 목록에 문서를 저장 하지 않은 경우는 `ReopenPreviousDocuments` 아무 작업도 수행 하지 않고 FALSE를 반환 합니다.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a> CDataRecoveryHandler::RestoreAutosavedDocuments

사용자 입력에 따라 자동 저장 된 문서를 복원 합니다.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>반환 값

이 메서드가 문서를 성공적으로 복원 하면 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 [CDataRecoveryHandler:: QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) 를 호출 하 여 사용자가 복원 하려는 문서를 결정 합니다. 사용자가 자동 저장 된 문서를 복원 하지 않기로 결정 한 경우에서 `RestoreAutosavedDocuments` 자동 저장 파일을 삭제 합니다. 그렇지 않으면 `RestoreAutosavedDocuments` 열려 있는 문서를 자동으로 저장 된 버전으로 바꿉니다.

이 메서드를 사용 하려면 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 또는 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES을에서 설정 해야 합니다 `m_dwRestartManagerSupportFlags` .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a> CDataRecoveryHandler:: SaveOpenDocumentList

열려 있는 문서의 현재 목록을 Windows 레지스트리에 저장 합니다.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>반환 값

저장할 열린 문서가 없거나 성공적으로 저장 된 경우 TRUE입니다. 레지스트리에 저장할 문서가 있지만 오류가 발생 하 여 저장 되지 않은 경우 FALSE입니다.

### <a name="remarks"></a>설명

다시 시작 관리자는 `SaveOpenDocumentList` 응용 프로그램이 예기치 않게 종료 되거나 업그레이드를 종료할 때를 호출 합니다. 응용 프로그램이 다시 시작 되 면 [CDataRecoveryHandler:: ReadOpenDocumentList](#readopendocumentlist) 를 사용 하 여 열린 문서 목록을 검색 합니다.

이 메서드는 열린 문서 목록만 저장 합니다. [CDataRecoveryHandler:: AutosaveDocumentInfo](#autosavedocumentinfo) 메서드는 문서 자체를 저장 합니다.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a> CDataRecoveryHandler:: SetAutosaveInterval

자동 저장 주기 시간 (밀리초)을 설정 합니다.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>매개 변수

*nAutosaveInterval*<br/>
진행 새 자동 저장 간격 (밀리초)입니다.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a> CDataRecoveryHandler:: SetAutosavePath

자동 저장 된 파일이 저장 되는 디렉터리를 설정 합니다.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>매개 변수

*strAutosavePath*\
진행 자동 저장 파일이 저장 되는 경로입니다.

### <a name="remarks"></a>설명

자동 저장 디렉터리를 변경 해도 현재 저장 된 파일은 이동 하지 않습니다.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a> CDataRecoveryHandler::SetRestartIdentifier

의이 인스턴스에 대 한 고유 다시 시작 식별자를 설정 합니다 `CDataRecoveryHandler` .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>매개 변수

*strRestartIdentifier*\
진행 다시 시작 관리자의 고유 식별자입니다.

### <a name="remarks"></a>설명

다시 시작 관리자는 레지스트리의 열린 문서에 대 한 정보를 기록 합니다. 이 정보는 고유한 다시 시작 식별자를 키로 사용 하 여 저장 됩니다. Restart 식별자는 응용 프로그램의 각 인스턴스에 대해 고유 하므로 응용 프로그램의 여러 인스턴스가 예기치 않게 종료 되 고 다시 시작 관리자가 각 인스턴스를 복구할 수 있습니다.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a> CDataRecoveryHandler:: SetSaveDocumentInfoOnIdle

에서 `CDataRecoveryHandler` 현재 유휴 주기 동안 열려 있는 문서 정보를 Windows 레지스트리에 저장할지 여부를 설정 합니다.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>매개 변수

*bSaveOnIdle*\
진행 현재 유휴 주기 동안 문서 정보를 저장 하려면 TRUE이 고, 그렇지 않으면입니다. 저장을 수행 하지 않으려면 FALSE로 설정 합니다.

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a> CDataRecoveryHandler::SetShutdownByRestartManager

응용 프로그램의 이전 종료를 다시 시작 관리자에 의해 발생 했는지 여부를 설정 합니다.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>매개 변수

*bShutdownByRestartManager*\
진행 다시 시작 관리자가 응용 프로그램을 종료 했음을 나타내려면 TRUE로 설정 합니다. 다른 이유로 응용 프로그램이 종료 되었음을 나타내려면 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

프레임 워크는 이전 종료가 예기치 않은 것인지 아니면 다시 시작 관리자에 의해 시작 되었는지 여부에 따라 다르게 동작 합니다.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a> CDataRecoveryHandler:: UpdateDocumentInfo

사용자가 문서를 저장 했으므로 문서에 대 한 정보를 업데이트 합니다.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>매개 변수

*pDocument*\
진행 저장 된 문서에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

이 메서드가 자동으로 저장 된 문서를 삭제 하 고 문서 정보를 업데이트 한 경우 TRUE입니다. 오류가 발생 한 경우 FALSE입니다.

### <a name="remarks"></a>설명

사용자가 문서를 저장 하면 응용 프로그램은 더 이상 필요 하지 않으므로 자동으로 저장 된 파일을 제거 합니다. `UpdateDocumentInfo`[CDataRecoveryHandler:: RemoveDocumentInfo](#removedocumentinfo)를 호출 하 여 자동 저장 된 파일을 삭제 합니다. `UpdateDocumentInfo` 그런 다음은 해당 정보를 삭제 하지만 저장 된 문서는 계속 열려 있기 때문에 현재 열려 있는 문서 목록에 *Pdocument* 의 정보를 추가 `RemoveDocumentInfo` 합니다.

이 메서드를 사용 하려면 *m_dwRestartManagerSupportFlags* 에서 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[방법: 다시 시작 관리자 지원 추가](../../mfc/how-to-add-restart-manager-support.md)

---
description: '자세한 정보: CWinApp 클래스'
title: CWinApp 클래스
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: 60ea2ea2ef1545a814406da047d1aef42b49a7a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344941"
---
# <a name="cwinapp-class"></a>CWinApp 클래스

Windows 애플리케이션 개체를 파생하는 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CWinApp : public CWinThread
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWinApp:: CWinApp](#cwinapp)|`CWinApp` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinApp:: AddDocTemplate](#adddoctemplate)|응용 프로그램의 사용 가능한 문서 템플릿 목록에 문서 템플릿을 추가 합니다.|
|[CWinApp:: AddToRecentFileList](#addtorecentfilelist)|가장 최근에 사용한 (MRU) 파일 목록에 파일 이름을 추가 합니다.|
|[CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)|응용 프로그램이 예기치 않게 종료 될 때 프레임 워크에서 호출 됩니다.|
|[CWinApp:: CloseAllDocuments](#closealldocuments)|열려 있는 모든 문서를 닫습니다.|
|[CWinApp:: Create프린터 Dc](#createprinterdc)|프린터 장치 컨텍스트를 만듭니다.|
|[CWinApp::D elRegTree](#delregtree)|지정 된 키와 모든 하위 키를 삭제 합니다.|
|[CWinApp::D oMessageBox](#domessagebox)|응용 프로그램에 대 한 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) 을 구현 합니다.|
|[CWinApp::D oWaitCursor](#dowaitcursor)|대기 커서를 켜고 끕니다.|
|[CWinApp:: EnableD2DSupport](#enabled2dsupport)|응용 프로그램 D2D 지원을 사용 하도록 설정 합니다. 주 창이 초기화되기 전에 이 메서드를 호출합니다.|
|[CWinApp:: EnableHtmlHelp](#enablehtmlhelp)|WinHelp가 아닌 응용 프로그램에 대 한 HTMLHelp을 구현 합니다.|
|[CWinApp:: Enabletask바 상호 작용](#enabletaskbarinteraction)|작업 표시줄 상호 작용을 사용 합니다.|
|[CWinApp:: ExitInstance](#exitinstance)|응용 프로그램이 종료 될 때 정리 하도록 재정의 합니다.|
|[CWinApp:: GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|응용 프로그램 복구 방법에 대 한 입력 매개 변수를 검색 합니다.|
|[CWinApp:: GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|복구 콜백 함수가 반환 될 때까지 다시 시작 관리자가 대기 하는 시간을 반환 합니다.|
|[CWinApp:: GetApplicationRestartFlags](#getapplicationrestartflags)|다시 시작 관리자에 대 한 플래그를 반환 합니다.|
|[CWinApp:: GetAppRegistryKey](#getappregistrykey)|HKEY_CURRENT_USER "Software"의 키를 반환 \\ \RegistryKey\ProfileName.|
|[CWinApp:: GetDataRecoveryHandler](#getdatarecoveryhandler)|이 응용 프로그램 인스턴스에 대 한 데이터 복구 처리기를 가져옵니다.|
|[CWinApp:: Getfirstdoc서식 위치](#getfirstdoctemplateposition)|첫 번째 문서 템플릿의 위치를 검색 합니다.|
|[CWinApp:: GetHelpMode](#gethelpmode)|응용 프로그램에서 사용 하는 도움말의 형식을 검색 합니다.|
|[CWinApp:: GetNextDocTemplate](#getnextdoctemplate)|문서 템플릿의 위치를 검색 합니다. 재귀적으로 사용할 수 있습니다.|
|[CWinApp:: Get프린터 Devicedefaults](#getprinterdevicedefaults)|프린터 장치 기본값을 검색 합니다.|
|[CWinApp:: GetProfileBinary](#getprofilebinary)|응용 프로그램의 항목에서 이진 데이터를 검색 합니다. INI 파일.|
|[CWinApp:: GetProfileInt](#getprofileint)|응용 프로그램의 항목에서 정수를 검색 합니다. INI 파일.|
|[CWinApp:: GetProfileString](#getprofilestring)|응용 프로그램의 항목에서 문자열을 검색 합니다. INI 파일.|
|[CWinApp:: Get섹션 키](#getsectionkey)|HKEY_CURRENT_USER "Software"의 키를 반환 \\ \RegistryKey\AppName\lpszSection.|
|[CWinApp:: HideApplication](#hideapplication)|모든 문서를 닫기 전에 응용 프로그램을 숨깁니다.|
|[CWinApp:: HtmlHelp](#htmlhelp)|`HTMLHelp`Windows 함수를 호출 합니다.|
|[CWinApp:: InitInstance](#initinstance)|창 개체 만들기와 같은 Windows 인스턴스 초기화를 수행 하도록를 재정의 합니다.|
|[CWinApp:: IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Windows 7 작업 표시줄 상호 작용이 사용 되는지 여부를 나타냅니다.|
|[CWinApp:: LoadCursor](#loadcursor)|커서 리소스를 로드 합니다.|
|[CWinApp:: LoadIcon](#loadicon)|아이콘 리소스를 로드 합니다.|
|[CWinApp:: LoadOEMCursor](#loadoemcursor)|**OCR_** 상수가 windows에서 지정 하는 windows OEM 미리 정의 된 커서를 로드 합니다.|
|[CWinApp:: LoadOEMIcon](#loadoemicon)|**OIC_** 상수가 windows에서 지정 하는 windows OEM 미리 정의 된 아이콘을 로드 합니다.|
|[CWinApp:: LoadStandardCursor](#loadstandardcursor)|**IDC_** 상수가 windows에서 지정 하는 미리 정의 된 windows 커서를 로드 합니다.|
|[CWinApp:: LoadStandardIcon](#loadstandardicon)|**IDI_** 상수가 windows에서 지정 하는 미리 정의 된 windows 아이콘을 로드 합니다.|
|[CWinApp:: OnDDECommand](#onddecommand)|DDE (동적 데이터 교환) 실행 명령에 대 한 응답으로 프레임 워크에서 호출 됩니다.|
|[CWinApp:: OnIdle](#onidle)|응용 프로그램별 유휴 시간 처리를 수행 하려면를 재정의 합니다.|
|[CWinApp:: OpenDocumentFile](#opendocumentfile)|파일에서 문서를 열기 위해 프레임 워크에서 호출 됩니다.|
|[CWinApp::P arseCommandLine](#parsecommandline)|명령줄에서 개별 매개 변수 및 플래그를 구문 분석 합니다.|
|[CWinApp::P reTranslateMessage](#pretranslatemessage)|Windows 함수 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)에 디스패치 되기 전에 메시지를 필터링 합니다.|
|[CWinApp::P rocessMessageFilter](#processmessagefilter)|응용 프로그램에 도달 하기 전에 특정 메시지를 가로챕니다.|
|[CWinApp::P rocessShellCommand](#processshellcommand)|명령줄 인수 및 플래그를 처리 합니다.|
|[CWinApp::P rocessWndProcException](#processwndprocexception)|응용 프로그램의 메시지 및 명령 처리기가 throw 한 처리 되지 않은 모든 예외를 가로챕니다.|
|[CWinApp:: Register](#register)|사용자 지정 된 등록을 수행 합니다.|
|[CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)|다시 시작 관리자를 사용 하 여 응용 프로그램을 등록 합니다.|
|[CWinApp:: ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|응용 프로그램이 예기치 않게 종료 될 때 열려 있던 파일을 다시 시작 관리자가 다시 열 지 여부를 결정 합니다.|
|[CWinApp:: RestartInstance](#restartinstance)|다시 시작 관리자에 의해 시작 된 응용 프로그램 다시 시작을 처리 합니다.|
|[CWinApp:: RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|다시 시작 관리자가 응용 프로그램을 다시 시작할 때 자동으로 저장 된 파일을 복원할지 여부를 결정 합니다.|
|[CWinApp:: Run](#run)|기본 메시지 루프를 실행 합니다. 메시지 루프를 사용자 지정 하려면를 재정의 합니다.|
|[CWinApp:: RunAutomated](#runautomated)|응용 프로그램의 명령줄에서 **/Automation** 옵션을 테스트 합니다. 사용되지 않습니다. 대신 [ParseCommandLine](#parsecommandline)를 호출한 후 [CCommandLineInfo:: m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) 의 값을 사용 합니다.|
|[CWinApp:: RunEmbedded](#runembedded)|응용 프로그램의 명령줄에서 **프로그램이/embedding** 옵션을 테스트 합니다. 사용되지 않습니다. 대신 [ParseCommandLine](#parsecommandline)를 호출한 후 [CCommandLineInfo:: m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) 의 값을 사용 합니다.|
|[CWinApp:: SaveAllModified](#saveallmodified)|사용자에 게 모든 수정 된 문서를 저장 하 라는 메시지를 표시 합니다.|
|[CWinApp:: SelectPrinter](#selectprinter)|사용자가 인쇄 대화 상자를 통해 이전에 표시 한 프린터를 선택 합니다.|
|[CWinApp:: SetHelpMode](#sethelpmode)|응용 프로그램에서 사용 하는 도움말의 형식을 설정 하 고 초기화 합니다.|
|[CWinApp:: SupportsApplicationRecovery](#supportsapplicationrecovery)|다시 시작 관리자가 예기치 않게 종료 된 응용 프로그램을 복구할 지 여부를 결정 합니다.|
|[CWinApp:: SupportsAutosaveAtInterval](#supportsautosaveatinterval)|다시 시작 관리자가 열려 있는 문서를 일정 한 간격으로 자동 저장 하는지 여부를 결정 합니다.|
|[CWinApp:: SupportsAutosaveAtRestart](#supportsautosaveatrestart)|응용 프로그램이 다시 시작 될 때 다시 시작 관리자가 열려 있는 모든 문서를 자동으로 저장할지 여부를 결정 합니다.|
|[CWinApp:: SupportsRestartManager](#supportsrestartmanager)|응용 프로그램에서 다시 시작 관리자를 지원 하는지 여부를 확인 합니다.|
|[CWinApp:: 등록 취소](#unregister)|개체에서 등록 된 것으로 알려진 모든 항목의 등록을 취소 `CWinApp` 합니다.|
|[CWinApp:: WinHelp](#winhelp)|`WinHelp`Windows 함수를 호출 합니다.|
|[CWinApp:: WriteProfileBinary](#writeprofilebinary)|응용 프로그램의 항목에 이진 데이터를 씁니다. INI 파일.|
|[CWinApp:: WriteProfileInt](#writeprofileint)|응용 프로그램의에 있는 항목에 정수를 씁니다. INI 파일.|
|[CWinApp:: WriteProfileString](#writeprofilestring)|응용 프로그램의에 있는 항목에 문자열을 씁니다. INI 파일.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CWinApp:: EnableShellOpen](#enableshellopen)|사용자가 Windows 파일 관리자에서 데이터 파일을 열 수 있도록 허용 합니다.|
|[CWinApp:: LoadStdProfileSettings](#loadstdprofilesettings)|표준을 로드 합니다. INI 파일을 설정 하 고 MRU 파일 목록 기능을 사용 하도록 설정 합니다.|
|[CWinApp:: OnContextHelp](#oncontexthelp)|응용 프로그램 내에서 SHIFT + F1 도움말을 처리 합니다.|
|[CWinApp:: OnFileNew](#onfilenew)|ID_FILE_NEW 명령을 구현 합니다.|
|[CWinApp:: OnFileOpen](#onfileopen)|ID_FILE_OPEN 명령을 구현 합니다.|
|[CWinApp:: OnFilePrintSetup](#onfileprintsetup)|ID_FILE_PRINT_SETUP 명령을 구현 합니다.|
|[CWinApp:: OnHelp](#onhelp)|현재 컨텍스트를 사용하여 애플리케이션 내에서 F1 도움말을 처리합니다.|
|[CWinApp:: OnHelpFinder](#onhelpfinder)|ID_HELP_FINDER 및 ID_DEFAULT_HELP 명령을 처리 합니다.|
|[CWinApp:: OnHelpIndex](#onhelpindex)|ID_HELP_INDEX 명령을 처리 하 고 기본 도움말 항목을 제공 합니다.|
|[CWinApp:: OnHelpUsing](#onhelpusing)|ID_HELP_USING 명령을 처리 합니다.|
|[CWinApp:: RegisterShellFileTypes](#registershellfiletypes)|응용 프로그램의 모든 문서 형식을 Windows 파일 관리자에 등록 합니다.|
|[CWinApp:: SetAppID](#setappid)|응용 프로그램의 응용 프로그램 사용자 모델 ID를 명시적으로 설정 합니다. 사용자 인터페이스가 사용자에 게 표시 되기 전에이 메서드를 호출 해야 합니다. 가장 좋은 장소는 응용 프로그램 생성자입니다.|
|[CWinApp:: SetRegistryKey](#setregistrykey)|응용 프로그램 설정이 대신 레지스트리에 저장 되도록 합니다. INI 파일.|
|[CWinApp:: UnregisterShellFileTypes](#unregistershellfiletypes)|Windows 파일 관리자를 사용 하 여 모든 응용 프로그램의 문서 유형을 등록 취소 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CWinApp:: m_bHelpMode](#m_bhelpmode)|사용자가 도움말 컨텍스트 모드 (일반적으로 SHIFT + f 1을 사용 하 여 호출 됨)에 있는지 여부를 나타냅니다.|
|[CWinApp:: m_eHelpType](#m_ehelptype)|응용 프로그램에서 사용 하는 도움말의 유형을 지정 합니다.|
|[CWinApp:: m_hInstance](#m_hinstance)|응용 프로그램의 현재 인스턴스를 식별 합니다.|
|[CWinApp:: m_lpCmdLine](#m_lpcmdline)|응용 프로그램에 대 한 명령줄을 지정 하는 null로 끝나는 문자열을 가리킵니다.|
|[CWinApp:: m_nCmdShow](#m_ncmdshow)|창을 처음에 표시 하는 방법을 지정 합니다.|
|[CWinApp:: m_pActiveWnd](#m_pactivewnd)|OLE 서버가 활성 상태인 경우 컨테이너 응용 프로그램의 주 창에 대 한 포인터입니다.|
|[CWinApp:: m_pszAppID](#m_pszappid)|응용 프로그램 사용자 모델 ID입니다.|
|[CWinApp:: m_pszAppName](#m_pszappname)|애플리케이션의 이름을 지정합니다.|
|[CWinApp:: m_pszExeName](#m_pszexename)|응용 프로그램의 모듈 이름입니다.|
|[CWinApp:: m_pszHelpFilePath](#m_pszhelpfilepath)|응용 프로그램 도움말 파일의 경로입니다.|
|[CWinApp:: m_pszProfileName](#m_pszprofilename)|응용 프로그램의입니다. INI 파일 이름입니다.|
|[CWinApp:: m_pszRegistryKey](#m_pszregistrykey)|응용 프로그램 프로필 설정을 저장 하기 위한 전체 레지스트리 키를 결정 하는 데 사용 됩니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CWinApp:: m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|다시 시작 관리자의 동작을 결정 하는 플래그입니다.|
|[CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)|Autosaves 사이의 시간 (밀리초)입니다.|
|[CWinApp:: m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|응용 프로그램의 데이터 복구 처리기에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

응용 프로그램 개체는 응용 프로그램을 초기화 하 고 응용 프로그램을 실행 하는 데 사용할 수 있는 멤버 함수를 제공 합니다.

Microsoft Foundation 클래스를 사용 하는 각 응용 프로그램은에서 파생 된 개체를 하나만 포함할 수 있습니다 `CWinApp` . 이 개체는 다른 c + + 전역 개체가 생성 될 때 생성 되며, Windows에서 MFC 라이브러리 제공 하는 함수를 호출할 때 이미 사용할 수 있습니다 `WinMain` . `CWinApp`전역 수준에서 파생 개체를 선언 합니다.

에서 응용 프로그램 클래스를 파생 하 `CWinApp` 는 경우 [InitInstance](#initinstance) 멤버 함수를 재정의 하 여 응용 프로그램의 주 창 개체를 만듭니다.

멤버 함수 외에도 `CWinApp` MFC 라이브러리는 `CWinApp` 개체 및 기타 전역 정보에 액세스 하는 다음과 같은 전역 함수를 제공 합니다.

- [AfxGetApp](application-information-and-management.md#afxgetapp) 개체에 대 한 포인터를 가져옵니다 `CWinApp` .

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) 현재 응용 프로그램 인스턴스에 대 한 핸들을 가져옵니다.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) 응용 프로그램의 리소스에 대 한 핸들을 가져옵니다.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) 응용 프로그램의 이름을 포함 하는 문자열에 대 한 포인터를 가져옵니다. 또는 개체에 대 한 포인터가 있는 경우를 `CWinApp` 사용 하 여 `m_pszExeName` 응용 프로그램의 이름을 가져옵니다.

다음에 대 한 개요를 비롯 하 여 클래스에 대 한 자세한 내용은 [CWinApp: 응용 프로그램 클래스](../../mfc/cwinapp-the-application-class.md) 를 참조 하세요 `CWinApp` .

- `CWinApp`-응용 프로그램 마법사에서 작성 한 파생 코드입니다.

- `CWinApp`응용 프로그램의 실행 순서에서의 역할입니다.

- `CWinApp`의 기본 멤버 함수 구현입니다.

- `CWinApp`키 재정의 가능.

`m_hPrevInstance`데이터 멤버가 더 이상 존재 하지 않습니다. 응용 프로그램의 다른 인스턴스가 실행 되 고 있는지 확인 하려면 명명 된 뮤텍스를 사용 합니다. 뮤텍스를 열 수 없으면 실행 중인 응용 프로그램의 다른 인스턴스가 없습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a> CWinApp:: AddDocTemplate

이 멤버 함수를 호출 하 여 응용 프로그램에서 유지 관리 하는 사용 가능한 문서 템플릿 목록에 문서 템플릿을 추가 합니다.

```cpp
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>매개 변수

*pTemplate*<br/>
추가할에 대 한 포인터 `CDocTemplate` 입니다.

### <a name="remarks"></a>설명

[RegisterShellFileTypes](#registershellfiletypes)를 호출 하기 전에 모든 문서 템플릿을 응용 프로그램에 추가 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a> CWinApp:: AddToRecentFileList

*LpszPathName* 를 MRU 파일 목록에 추가 하려면이 멤버 함수를 호출 합니다.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>매개 변수

*lpszPathName*<br/>
파일의 경로입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 사용 하기 전에 [Loadstdprofilesettings](#loadstdprofilesettings) 멤버 함수를 호출 하 여 현재 MRU 파일 목록을 로드 해야 합니다.

프레임 워크는 파일을 열 때이 멤버 함수를 호출 하거나 다른 이름으로 저장 명령을 실행 하 여 새 이름으로 파일을 저장 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a> CWinApp:: ApplicationRecoveryCallback

응용 프로그램이 예기치 않게 종료 될 때 프레임 워크에서 호출 됩니다.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>매개 변수

*lpvParam*<br/>
진행 나중에 사용 하도록 예약 되어 있습니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 0이 고, 그렇지 않으면 0입니다. 오류가 발생 하는 경우 0이 아닙니다.

### <a name="remarks"></a>설명

응용 프로그램에서 다시 시작 관리자를 지 원하는 경우 응용 프로그램이 예기치 않게 종료 될 때 프레임 워크에서이 함수를 호출 합니다.

의 기본 구현에서는 `ApplicationRecoveryCallback` 를 사용 하 여 `CDataRecoveryHandler` 현재 열려 있는 문서의 목록을 레지스트리에 저장 합니다. 이 메서드는 파일을 자동으로 저장 하지 않습니다.

동작을 사용자 지정 하려면 파생 된 [CWinApp 클래스](../../mfc/reference/cwinapp-class.md) 에서이 함수를 재정의 하거나 사용자 고유의 응용 프로그램 복구 메서드를 [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)에 대 한 매개 변수로 전달 합니다.

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a> CWinApp:: CloseAllDocuments

종료 하기 전에이 멤버 함수를 호출 하 여 열려 있는 모든 문서를 닫습니다.

```cpp
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>매개 변수

*bEndSession*<br/>
Windows 세션의 종료 여부를 지정 합니다. 세션이 종료 되는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

를 호출 하기 전에 [HideApplication](#hideapplication) `CloseAllDocuments` 를 호출 합니다.

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a> CWinApp:: Create프린터 Dc

이 멤버 함수를 호출 하 여 선택한 프린터에서 프린터 DC (장치 컨텍스트)를 만듭니다.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
프린터 장치 컨텍스트에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

프린터 장치 컨텍스트가 성공적으로 생성 되 면 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreatePrinterDC` 참조로 전달 하는 장치 컨텍스트를 초기화 하므로 인쇄 하는 데 사용할 수 있습니다.

함수가 성공적으로 실행 되 면 인쇄를 마치면 장치 컨텍스트를 제거 해야 합니다. [Cdc](../../mfc/reference/cdc-class.md) 개체의 소멸자가이를 수행 하도록 하거나 [Cdc::D eletedc](../../mfc/reference/cdc-class.md#deletedc)를 호출 하 여 명시적으로 수행할 수 있습니다.

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a> CWinApp:: CWinApp

개체를 생성 하 `CWinApp` 고 응용 프로그램 이름으로 저장 될 *lpszAppName* 를 전달 합니다.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszAppName*<br/>
Windows에서 사용 하는 응용 프로그램 이름을 포함 하는 null로 끝나는 문자열입니다. 이 인수를 제공 하지 않거나 NULL 인 경우는 `CWinApp` 리소스 문자열 AFX_IDS_APP_TITLE 또는 실행 파일의 파일 이름을 사용 합니다.

### <a name="remarks"></a>설명

파생 클래스의 전역 개체 하나를 구성 해야 `CWinApp` 합니다. 응용 프로그램에 개체를 하나만 포함할 수 있습니다 `CWinApp` . 생성자는 개체 `CWinApp` `WinMain` 의 멤버 함수를 호출 하 여 응용 프로그램을 초기화 하 고 실행할 수 있도록 개체에 대 한 포인터를 저장 합니다.

## <a name="cwinappdelregtree"></a><a name="delregtree"></a> CWinApp::D elRegTree

특정 레지스트리 키와 모든 하위 키를 삭제 합니다.

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*hParentKey*<br/>
레지스트리 키에 대 한 핸들입니다.

*strKeyName*<br/>
삭제할 레지스트리 키의 이름입니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

지정 된 키와 하위 키를 삭제 하려면이 함수를 호출 합니다.

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a> CWinApp::D oMessageBox

프레임 워크는이 멤버 함수를 호출 하 여 전역 함수 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)에 대 한 메시지 상자를 구현 합니다.

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>매개 변수

*lpszPrompt*<br/>
메시지 상자의 텍스트 주소입니다.

*nType*<br/>
메시지 상자 [스타일](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)입니다.

*nIDPrompt*<br/>
도움말 컨텍스트 문자열의 인덱스입니다.

### <a name="return-value"></a>반환 값

와 동일한 값을 반환 합니다 `AfxMessageBox` .

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 메시지 상자를 열 수 없습니다. `AfxMessageBox` 대신를 사용 합니다.

응용 프로그램 전체 호출 처리를 사용자 지정 하려면이 멤버 함수를 재정의 `AfxMessageBox` 합니다.

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a> CWinApp::D oWaitCursor

이 멤버 함수는 [Cwaitcursor](../../mfc/reference/cwaitcursor-class.md), [Cwaitcursor:: beginwaitcursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [Cwaitcursor:: endwaitcursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)및 [cwaitcursor:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)을 구현 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>매개 변수

*nCode*<br/>
이 매개 변수가 1 이면 대기 커서가 표시 됩니다. 0 인 경우 참조 횟수를 증가 시 키 지 않고 대기 커서가 복원 됩니다. -1 인 경우 대기 커서가 종료 됩니다.

### <a name="remarks"></a>설명

기본값은 모래 시계 커서를 구현 합니다. `DoWaitCursor` 참조 횟수를 유지 관리 합니다. 양수 이면 모래 시계 커서가 표시 됩니다.

일반적으로를 직접 호출 하지는 않지만 대기 `DoWaitCursor` 커서를 표시 하는 동안 대기 커서를 변경 하거나 추가 처리를 수행 하도록이 멤버 함수를 재정의할 수 있습니다.

대기 커서를 구현 하는 보다 간단 하 고 간소화 된 방법을 사용 하려면을 사용 `CWaitCursor` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a> CWinApp:: EnableD2DSupport

Visual Studio 2010 SP1이 필요합니다.

응용 프로그램 D2D 지원을 사용 하도록 설정 합니다. 주 창이 초기화되기 전에 이 메서드를 호출합니다.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>매개 변수

*d2dFactoryType*<br/>
D2D 팩터리의 스레딩 모델 및이 모델에서 만드는 리소스입니다.

*writeFactoryType*<br/>
쓰기 팩터리 개체를 공유할지 아니면 격리할 지를 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

D2D 지원을 사용 하도록 설정한 경우 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a> CWinApp:: EnableHtmlHelp

`CWinApp`응용 프로그램 도움말에 HTMLHelp를 사용 하려면 파생 클래스의 생성자 내에서이 멤버 함수를 호출 합니다.

```cpp
void EnableHtmlHelp();
```

### <a name="remarks"></a>설명

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a> CWinApp:: EnableShellOpen

일반적으로 재정의에서이 함수를 호출 `InitInstance` 하 여 응용 프로그램의 사용자가 Windows 파일 관리자 내에서 파일을 두 번 클릭할 때 데이터 파일을 열 수 있도록 합니다.

```cpp
void EnableShellOpen();
```

### <a name="remarks"></a>설명

`RegisterShellFileTypes`이 함수와 함께 멤버 함수를 호출 하거나를 제공 합니다. 문서 유형 수동 등록을 위한 응용 프로그램의 REG 파일입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a> CWinApp:: Enabletask바 상호 작용

작업 표시줄 상호 작용을 사용 합니다.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
Windows 7 작업 표시줄과의 상호 작용을 사용 (TRUE) 하거나 사용 하지 않도록 (FALSE) 할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

작업 표시줄 상호 작용을 사용 하거나 사용 하지 않도록 설정할 수 있으면 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

주 창을 만들기 전에이 메서드를 호출 해야 합니다. 그렇지 않으면 어설션 하 고 FALSE를 반환 합니다.

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a> CWinApp:: ExitInstance

`Run`응용 프로그램의이 인스턴스를 종료 하기 위해 멤버 함수 내에서 프레임 워크에 의해 호출 됩니다.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>반환 값

응용 프로그램의 종료 코드입니다. 0은 오류가 없음을 나타내고 0 보다 큰 값은 오류를 나타냅니다. 이 값은의 반환 값으로 사용 됩니다 `WinMain` .

### <a name="remarks"></a>설명

멤버 함수 내에서는 어디에서 나이 멤버 함수를 호출 하지 마세요 `Run` .

이 함수의 기본 구현은 응용 프로그램의에 프레임 워크 옵션을 씁니다. INI 파일. 응용 프로그램이 종료 될 때 정리 하려면이 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a> CWinApp:: GetApplicationRecoveryParameter

응용 프로그램 복구 방법에 대 한 입력 매개 변수를 검색 합니다.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>반환 값

응용 프로그램 복구 방법에 대 한 기본 입력 매개 변수입니다.

### <a name="remarks"></a>설명

이 함수의 기본 동작은 NULL을 반환 합니다.

자세한 내용은 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)을 참조 하세요.

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a> CWinApp:: GetApplicationRecoveryPingInterval

복구 콜백 함수가 반환 될 때까지 다시 시작 관리자가 대기 하는 시간을 반환 합니다.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>반환 값

시간 길이 (밀리초)입니다.

### <a name="remarks"></a>설명

다시 시작 관리자에 등록 된 응용 프로그램이 예기치 않게 종료 되 면 응용 프로그램은 열려 있는 문서를 저장 하 고 복구 콜백 함수를 호출 합니다. 기본 복구 콜백 함수는 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)입니다.

프레임 워크에서 복구 콜백 함수가 반환 될 때까지 대기 하는 시간은 ping 간격입니다. `CWinApp::GetApplicationRecoveryPingInterval`를 재정의 하거나에 사용자 지정 값을 제공 하 여 ping 간격을 사용자 지정할 수 있습니다 `RegisterWithRestartManager` .

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a> CWinApp:: GetApplicationRestartFlags

다시 시작 관리자에 대 한 플래그를 반환 합니다.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>반환 값

다시 시작 관리자에 대 한 플래그입니다. 기본 구현에서는 0을 반환 합니다.

### <a name="remarks"></a>설명

다시 시작 관리자에 대 한 플래그는 기본 구현에 영향을 주지 않습니다. 나중에 사용 하기 위해 제공 됩니다.

사용자는 [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)를 사용 하 여 다시 시작 관리자에 응용 프로그램을 등록할 때 플래그를 설정 합니다.

다시 시작 관리자 플래그에 사용할 수 있는 값은 다음과 같습니다.

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a> CWinApp:: GetAppRegistryKey

HKEY_CURRENT_USER "Software"의 키를 반환 합니다. \\ \RegistryKey\ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 응용 프로그램 키 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a> CWinApp:: GetDataRecoveryHandler

이 응용 프로그램 인스턴스에 대 한 데이터 복구 처리기를 가져옵니다.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>반환 값

이 응용 프로그램 인스턴스에 대 한 데이터 복구 처리기입니다.

### <a name="remarks"></a>설명

다시 시작 관리자를 사용 하는 각 응용 프로그램에는 [CDataRecoveryHandler 클래스](../../mfc/reference/cdatarecoveryhandler-class.md)의 인스턴스가 하나 있어야 합니다. 이 클래스는 open documents 및 작업 파일을 모니터링 하는 일을 담당 합니다. 의 동작은 `CDataRecoveryHandler` 다시 시작 관리자의 구성에 따라 달라 집니다. 자세한 내용은 [CDataRecoveryHandler 클래스](../../mfc/reference/cdatarecoveryhandler-class.md)를 참조 하세요.

이 메서드는 Windows Vista 이전 운영 체제에서 NULL을 반환 합니다. 다시 시작 관리자는 Windows Vista 이전 운영 체제에서 지원 되지 않습니다.

응용 프로그램에 현재 데이터 복구 처리기가 없는 경우이 메서드는 데이터 복구 처리기를 만들어 해당 처리기에 대 한 포인터를 반환 합니다.

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a> CWinApp:: Getfirstdoc서식 위치

응용 프로그램에서 첫 번째 문서 템플릿의 위치를 가져옵니다.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>반환 값

반복 또는 개체 포인터 검색에 사용할 수 있는 위치 값입니다. 목록이 비어 있으면 NULL입니다.

### <a name="remarks"></a>설명

[GetNextDocTemplate](#getnextdoctemplate) 에 대 한 호출에서 반환 된 POSITION 값을 사용 하 여 첫 번째 [cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체를 가져옵니다.

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a> CWinApp:: GetHelpMode

응용 프로그램에서 사용 하는 도움말의 형식을 검색 합니다.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>반환 값

응용 프로그램에서 사용 하는 도움말 유형입니다. 자세한 내용은 [CWinApp:: m_eHelpType](#m_ehelptype) 를 참조 하세요.

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a> CWinApp:: GetNextDocTemplate

*Pos* 로 식별 된 문서 템플릿을 가져온 다음 *pos* 를 POSITION 값으로 설정 합니다.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>매개 변수

*pos*<br/>
`GetNextDocTemplate`또는 [Getfirstdoc템플릿 위치](#getfirstdoctemplateposition)에 대 한 이전 호출에서 반환 된 위치 값에 대 한 참조입니다. 이 호출을 통해 값이 다음 위치로 업데이트 됩니다.

### <a name="return-value"></a>반환 값

[Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`GetNextDocTemplate`를 호출 하 여 초기 위치를 설정 하는 경우 전방 반복 루프에서을 사용할 수 있습니다 `GetFirstDocTemplatePosition` .

위치 값이 유효한 지 확인 해야 합니다. 잘못 된 경우 MFC 라이브러리의 디버그 버전에서 어설션 합니다.

검색 된 문서 템플릿을 마지막으로 사용할 수 있는 경우에는 *pos* 의 새 값이 NULL로 설정 됩니다.

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a> CWinApp:: Get프린터 Devicedefaults

인쇄를 위해 프린터 장치 컨텍스트를 준비 하려면이 멤버 함수를 호출 합니다.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>매개 변수

*pPrintDlg*<br/>
[Printdlg](/windows/win32/api/commdlg/ns-commdlg-printdlga) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

창에서 현재 프린터 기본값을 검색 합니다. 필요에 따라 INI 파일을 사용 하거나 인쇄 설정에서 사용자가 설정한 마지막 프린터 구성을 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a> CWinApp:: GetProfileBinary

응용 프로그램 레지스트리 또는의 지정 된 섹션 내에서 항목에서 이진 데이터를 검색 하려면이 멤버 함수를 호출 합니다. INI 파일.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다.

*lpszEntry*<br/>
값을 검색할 항목이 포함된 null로 끝나는 문자열을 가리킵니다.

*ppData*<br/>
데이터의 주소를 수신 하는 포인터를 가리킵니다.

*pBytes*<br/>
데이터의 크기 (바이트)를 받을 UINT를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 대/소문자를 구분 하지 않으므로 *lpszSection* 및 *lpszEntry* 매개 변수의 문자열은 대/소문자가 다를 수 있습니다.

> [!NOTE]
> `GetProfileBinary` 버퍼를 할당 하 고 해당 주소를 \* *ppdata* 로 반환 합니다. 호출자는 **delete []** 를 사용 하 여 버퍼를 해제 해야 합니다.

> [!IMPORTANT]
> 이 함수에서 반환된 데이터는 NULL로 끝나지 않아도 되며 호출자는 유효성 검사를 수행해야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

추가 예제를 보려면 [CWinApp:: WriteProfileBinary](#writeprofilebinary)를 참조 하십시오.

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a> CWinApp:: GetProfileInt

.INI 파일 또는 애플리케이션 레지스트리의 지정된 섹션 내에 있는 항목으로 정수 값을 검색하려면 이 멤버 함수를 호출합니다.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다.

*lpszEntry*<br/>
값을 검색할 항목이 포함된 null로 끝나는 문자열을 가리킵니다.

*nDefault*<br/>
프레임워크에서 항목을 찾을 수 없는 경우 반환할 기본값을 지정합니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 문자열의 정수 값은 지정된 항목 다음에 오게 됩니다. 반환 값은 함수가 항목을 찾지 못하는 경우 *Ndefault* 매개 변수의 값입니다. 지정한 항목에 해당하는 값이 정수가 아닌 경우 반환 값은 0입니다.

이 멤버 함수는 .INI 파일에서 값에 대한 16 진수 표기법을 지원합니다. 부호 있는 정수를 검색 하는 경우 값을로 캐스팅 해야 합니다 **`int`** .

### <a name="remarks"></a>설명

이 멤버 함수는 대/소문자를 구분 하지 않으므로 *lpszSection* 및 *lpszEntry* 매개 변수의 문자열은 대/소문자가 다를 수 있습니다.

> [!IMPORTANT]
> 이 함수에서 반환된 데이터는 NULL로 끝나지 않아도 되며 호출자는 유효성 검사를 수행해야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

추가 예제를 보려면 [CWinApp:: WriteProfileInt](#writeprofileint)를 참조 하십시오.

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a> CWinApp:: GetProfileString

이 멤버 함수를 호출 하 여 응용 프로그램의 레지스트리 또는의 지정 된 섹션 내에서 항목과 관련 된 문자열을 검색 합니다. INI 파일.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다.

*lpszEntry*<br/>
는 문자열을 검색할 엔트리가 포함 된 null로 끝나는 문자열을 가리킵니다. 이 값은 NULL이 아니어야 합니다.

*lpszDefault*<br/>
초기화 파일에서 항목을 찾을 수 없는 경우 지정 된 항목의 기본 문자열 값을 가리킵니다.

### <a name="return-value"></a>반환 값

반환 값은 응용 프로그램의에 있는 문자열입니다. 문자열을 찾을 수 없는 경우 INI 파일 또는 *lpszDefault* 입니다. 프레임 워크에서 지 원하는 최대 문자열 길이는 _MAX_PATH입니다. *LpszDefault* 가 NULL 이면 반환 값은 빈 문자열입니다.

### <a name="remarks"></a>설명

> [!IMPORTANT]
> 이 함수에서 반환된 데이터는 NULL로 끝나지 않아도 되며 호출자는 유효성 검사를 수행해야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

다른 예제를 보려면 [CWinApp:: GetProfileInt](#getprofileint)의 예제를 참조 하세요.

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a> CWinApp:: Get섹션 키

HKEY_CURRENT_USER "Software"의 키를 반환 합니다. \\ \RegistryKey\AppName\lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
가져올 키의 이름입니다.

*pTM*<br/>
`CAtlTransactionManager` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 섹션 키 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a> CWinApp:: HideApplication

열려 있는 문서를 닫기 전에 응용 프로그램을 숨기려면이 멤버 함수를 호출 합니다.

```cpp
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a> CWinApp:: HtmlHelp

이 멤버 함수를 호출 하 여 HTMLHelp 응용 프로그램을 호출 합니다.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>매개 변수

*dwData*<br/>
추가 데이터를 지정 합니다. 사용 되는 값은 *Ncmd* 매개 변수의 값에 따라 달라 집니다. 기본값은 `0x000F` [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command)입니다.

*nCmd*<br/>
요청한 도움말의 형식을 지정합니다. 사용할 수 있는 값 목록과 이러한 값이 *Dwdata* 매개 변수에 영향을 주는 방법에 대 한 자세한 내용은이 항목에서 설명 [하는](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) *ucommand* 매개 변수를 참조 하십시오. Windows SDK의 API 함수 [를](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) 참조 하십시오.

### <a name="remarks"></a>설명

또한 프레임 워크는이 함수를 호출 하 여 HTMLHelp 응용 프로그램을 호출 합니다.

응용 프로그램이 종료 되 면 프레임 워크가 자동으로 HTMLHelp 응용 프로그램을 닫습니다.

## <a name="cwinappinitinstance"></a><a name="initinstance"></a> CWinApp:: InitInstance

Windows에서는 동일한 프로그램의 여러 복사본을 동시에 실행할 수 있습니다.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

응용 프로그램 초기화는 개념적으로 프로그램을 처음 실행할 때 수행 되는 일회성 응용 프로그램 초기화와 프로그램 복사본이 실행 될 때마다 처음으로 실행 되는 인스턴스 초기화 라는 두 개의 섹션으로 구분 됩니다. 프레임 워크의 구현에서 `WinMain` 이 함수를 호출 합니다.

`InitInstance`를 재정의 하 여 Windows에서 실행 되는 응용 프로그램의 새 인스턴스를 초기화 합니다. 일반적으로를 재정의 `InitInstance` 하 여 주 창 개체를 생성 하 고 `CWinThread::m_pMainWnd` 해당 창을 가리키도록 데이터 멤버를 설정 합니다. 이 멤버 함수를 재정의 하는 방법에 대 한 자세한 내용은 [CWinApp: 응용 프로그램 클래스](../../mfc/cwinapp-the-application-class.md)를 참조 하세요.

> [!NOTE]
> MFC 응용 프로그램을 STA (단일 스레드 아파트)로 초기화 해야 합니다. 재정의에서 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) 를 호출 하 `InitInstance` 는 경우 COINIT_MULTITHREADED 대신 COINIT_APARTMENTTHREADED를 지정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a> CWinApp:: IsTaskbarInteractionEnabled

Windows 7 작업 표시줄 상호 작용이 사용 되는지 여부를 나타냅니다.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>반환 값

`EnableTaskbarInteraction`가 호출 되 고 운영 체제가 Windows 7 이상인 경우 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

작업 표시줄 상호 작용 이란 MDI 응용 프로그램이 마우스 포인터가 응용 프로그램 작업 표시줄 단추 위에 있을 때 표시 되는 별도의 탭 미리 보기에 MDI 자식의 내용을 표시 한다는 것을 의미 합니다.

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a> CWinApp:: LoadCursor

*LpszResourceName* 에 의해 이름이 지정 된 커서 리소스를 로드 하거나 현재 실행 파일에서 *nIDResource* 에 의해 지정 된 커서 리소스를 로드 합니다.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
커서 리소스의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. 이 인수에는를 사용할 수 있습니다 `CString` .

*nIDResource*<br/>
커서 리소스의 ID입니다. 리소스 목록은 Windows SDK의 [Loadcursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) 를 참조 하십시오.

### <a name="return-value"></a>반환 값

성공 하면 커서에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadCursor` 이전에 로드 되지 않은 경우에만 커서를 메모리로 로드 합니다. 그렇지 않으면 기존 리소스의 핸들을 검색 합니다.

미리 정의 된 Windows 커서에 액세스 하려면 [Loadstandardcursor](#loadstandardcursor) 또는 [loadstandardcursor](#loadoemcursor) 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a> CWinApp:: LoadIcon

*LpszResourceName* 또는 실행 파일에서 *nIDResource* 로 지정 된 아이콘 리소스를 로드 합니다.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
아이콘 리소스의 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다. 이 인수에를 사용할 수도 있습니다 `CString` .

*nIDResource*<br/>
아이콘 리소스의 ID 번호입니다.

### <a name="return-value"></a>반환 값

성공 하면 아이콘에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadIcon` 이전에 로드 되지 않은 경우에만 아이콘을 로드 합니다. 그렇지 않으면 기존 리소스의 핸들을 검색 합니다.

[LoadStandardIcon](#loadstandardicon) 또는 [loadoemicon](#loadoemicon) 멤버 함수를 사용 하 여 미리 정의 된 Windows 아이콘에 액세스할 수 있습니다.

> [!NOTE]
> 이 멤버 함수는 Win32 API 함수 [Loadicon](/windows/win32/api/winuser/nf-winuser-loadiconw)을 호출 하며, 크기가 SM_CXICON 및 SM_CYICON 시스템 메트릭 값을 준수 하는 아이콘만 로드할 수 있습니다.

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a> CWinApp:: LoadOEMCursor

*NIDCursor* 로 지정 된 Windows 미리 정의 된 커서 리소스를 로드 합니다.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>매개 변수

*nIDCursor*<br/>
미리 정의 된 Windows 커서를 지정 하는 **OCR_** 매니페스트 상수 식별자입니다. `#define OEMRESOURCE` `#include \<afxwin.h>` WINDOWS의 **OCR_** 상수에 대 한 액세스 권한을 얻으려면 먼저가 있어야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 커서에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadOEMCursor`미리 정의 된 Windows 커서에 액세스 하려면 또는 [loadstandardcursor](#loadstandardcursor) 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a> CWinApp:: LoadOEMIcon

*NIDIcon* 로 지정 된 Windows 미리 정의 된 아이콘 리소스를 로드 합니다.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>매개 변수

*nIDIcon*<br/>
미리 정의 된 Windows 아이콘을 지정 하는 **OIC_** 매니페스트 상수 식별자입니다. `#define OEMRESOURCE` `#include \<afxwin.h>` WINDOWS .h의 **OIC_** 상수에 액세스 하려면 먼저가 있어야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 아이콘에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadOEMIcon`또는 [LoadStandardIcon](#loadstandardicon) 멤버 함수를 사용 하 여 미리 정의 된 Windows 아이콘에 액세스할 수 있습니다.

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a> CWinApp:: LoadStandardCursor

*LpszCursorName* 가 지정 하는 미리 정의 된 Windows 커서 리소스를 로드 합니다.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>매개 변수

*lpszCursorName*<br/>
미리 정의 된 Windows 커서를 지정 하는 **IDC_** 매니페스트 상수 식별자입니다. 이러한 식별자는 WINDOWS에 정의 되어 있습니다. 다음 목록에서는 *lpszCursorName* 에 대해 가능한 미리 정의 된 값과 의미를 보여 줍니다.

- IDC_ARROW 표준 화살표 커서

- IDC_IBEAM 표준 텍스트 삽입 커서

- Windows에서 시간이 많이 걸리는 작업을 수행할 때 사용 되는 IDC_WAIT 모래 시계 커서

- 선택 영역에 대 한 십자 커서 IDC_CROSS

- 수직 위로 가리키는 IDC_UPARROW 화살표

- IDC_SIZE 사용 되지 않으며 지원 되지 않음 IDC_SIZEALL 사용

- 4 방향 화살표를 IDC_SIZEALL 합니다. 창의 크기를 조정 하는 데 사용할 커서입니다.

- IDC_ICON 사용 되지 않으며 지원 되지 않습니다. IDC_ARROW를 사용 합니다.

- 왼쪽 위와 오른쪽 아래에 끝점이 있는 양방향 화살표 IDC_SIZENWSE

- 오른쪽 위와 왼쪽 아래에 끝점이 있는 양방향 화살표를 IDC_SIZENESW 합니다.

- IDC_SIZEWE 가로 양방향 화살표

- IDC_SIZENS 세로 양방향 화살표

### <a name="return-value"></a>반환 값

성공 하면 커서에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadStandardCursor`미리 정의 된 Windows 커서에 액세스 하려면 또는 [Loadoemcursor](#loadoemcursor) 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a> CWinApp:: LoadStandardIcon

*LpszIconName* 가 지정 하는 Windows 미리 정의 된 아이콘 리소스를 로드 합니다.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>매개 변수

*lpszIconName*<br/>
미리 정의 된 창 아이콘을 지정 하는 매니페스트 상수 식별자입니다. 이러한 식별자는 WINDOWS에 정의 되어 있습니다. 사용할 수 있는 미리 정의 된 값 및 해당 설명의 목록은 Windows SDK의 [Loadicon](/windows/win32/api/winuser/nf-winuser-loadiconw) 에서 *Lpiconname* 매개 변수를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 아이콘에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`LoadStandardIcon`미리 정의 된 Windows 아이콘에 액세스 하려면 또는 [Loadoemicon](#loadoemicon) 멤버 함수를 사용 합니다.

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a> CWinApp:: LoadStdProfileSettings

[InitInstance](#initinstance) 멤버 함수 내에서이 멤버 함수를 호출 하 여 MRU (가장 최근에 사용 됨) 파일 및 마지막 미리 보기 상태 목록을 사용 하도록 설정 하 고 로드 합니다.

```cpp
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>매개 변수

*nMaxMRU*<br/>
추적할 최근에 사용한 파일의 수입니다.

### <a name="remarks"></a>설명

*Nmaxmru* 가 0 이면 mru 목록이 유지 되지 않습니다.

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a> CWinApp:: m_bHelpMode

응용 프로그램이 도움말 컨텍스트 모드에 있으면 TRUE이 고, SHIFT + f 1을 사용 하 여 호출 되는 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>설명

도움말 컨텍스트 모드에서는 커서가 물음표가 되 고 사용자가 화면에 대 한 포인터를 이동할 수 있습니다. 도움말 모드에서 특수 처리를 구현 하려면이 플래그를 검사 합니다. `m_bHelpMode` BOOL 형식의 공용 변수입니다.

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a> CWinApp:: m_dwRestartManagerSupportFlags

다시 시작 관리자의 동작을 결정 하는 플래그입니다.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>설명

다시 시작 관리자를 사용 하도록 설정 하려면를 `m_dwRestartManagerSupportFlags` 원하는 동작으로 설정 합니다. 다음 표에서는 사용할 수 있는 플래그를 보여 줍니다.

|플래그|설명|
|-|-|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|응용 프로그램은 [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)를 사용 하 여 등록 됩니다. 다시 시작 관리자는 응용 프로그램이 예기치 않게 종료 되는 경우 응용 프로그램을 다시 시작 해야 합니다.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|응용 프로그램은 다시 시작 관리자에 등록 되 고 다시 시작 관리자는 응용 프로그램을 다시 시작할 때 복구 콜백 함수를 호출 합니다. 기본 복구 콜백 함수는 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)입니다.|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|자동 저장을 사용 하도록 설정 하 고 다시 시작 관리자는 응용 프로그램이 다시 시작 될 때 열린 모든 문서를 자동으로 저장 합니다.|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|자동 저장을 사용 하도록 설정 하 고 다시 시작 관리자가 열려 있는 모든 문서를 일정 한 간격으로 자동 저장 합니다. 이 간격은 [CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)에 의해 정의 됩니다.|
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|예기치 않은 종료에서 응용 프로그램을 다시 시작한 후 다시 시작 관리자가 이전에 열린 문서를 엽니다. [CDataRecoveryHandler 클래스](../../mfc/reference/cdatarecoveryhandler-class.md) 는 열려 있는 문서 목록을 저장 하 고 복원 하는 것을 처리 합니다.|
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|다시 시작 관리자는 응용 프로그램을 다시 시작한 후 자동으로 저장 된 파일을 복원 하 라는 메시지를 표시 합니다. `CDataRecoveryHandler`클래스는 사용자를 쿼리 합니다.|
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER 및 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES의 합집합입니다.|
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 및 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES의 합집합입니다.|
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 및 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES의 합집합입니다.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Union ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 및 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES입니다.|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a> CWinApp:: m_eHelpType

이 데이터 멤버의 형식은 클래스 내에 정의 된 AFX_HELP_TYPE 열거형 형식입니다 `CWinApp` .

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>설명

AFX_HELP_TYPE 열거형은 다음과 같이 정의 됩니다.

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- 응용 프로그램의 도움말을 HTML 도움말로 설정 하려면 [SetHelpMode](#sethelpmode) 를 호출 하 고를 지정 `afxHTMLHelp` 합니다.

- 응용 프로그램의 도움말을 WinHelp로 설정 하려면를 호출 하 `SetHelpMode` 고를 지정 `afxWinHelp` 합니다.

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a> CWinApp:: m_hInstance

Windows에서에 전달한 *Hinstance* 매개 변수에 해당 `WinMain` 합니다.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>설명

`m_hInstance`데이터 멤버는 Windows에서 실행 되는 응용 프로그램의 현재 인스턴스에 대 한 핸들입니다. 이는 전역 함수 [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)에서 반환 됩니다. `m_hInstance` 는 HINSTANCE 형식의 공용 변수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a> CWinApp:: m_lpCmdLine

Windows에서로 전달 된 *Lpcmdline* 매개 변수에 해당 합니다 `WinMain` .

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>설명

응용 프로그램에 대 한 명령줄을 지정 하는 null로 끝나는 문자열을 가리킵니다. `m_lpCmdLine`응용 프로그램이 시작 될 때 사용자가 입력 한 명령줄 인수에 액세스 하려면를 사용 합니다. `m_lpCmdLine` 는 LPTSTR 형식의 공용 변수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a> CWinApp:: m_nAutosaveInterval

Autosaves 사이의 시간 (밀리초)입니다.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>설명

설정 된 간격으로 열린 문서를 자동으로 저장 하도록 restart manager를 구성할 수 있습니다. 응용 프로그램에서 파일을 저장 하지 않는 경우이 매개 변수는 영향을 주지 않습니다.

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a> CWinApp:: m_nCmdShow

Windows에서로 전달 된 *Ncmdshow* 매개 변수에 해당 `WinMain` 합니다.

```
int m_nCmdShow;
```

### <a name="remarks"></a>설명

`m_nCmdShow`응용 프로그램의 주 창에 대해 [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) 를 호출 하는 경우를 인수로 전달 해야 합니다. `m_nCmdShow` 는 형식의 공용 변수입니다 **`int`** .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a> CWinApp:: m_pActiveWnd

이 데이터 멤버를 사용 하 여 OLE 서버 응용 프로그램 내부 활성화 된 ole 컨테이너 응용 프로그램의 주 창에 대 한 포인터를 저장할 수 있습니다.

### <a name="remarks"></a>설명

이 데이터 멤버가 NULL 이면 응용 프로그램이 활성 상태로 활성화 되지 않습니다.

프레임 워크는 프레임 창이 OLE 컨테이너 응용 프로그램에 의해 활성화 된 경우이 멤버 변수를 설정 합니다.

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a> CWinApp:: m_pDataRecoveryHandler

응용 프로그램의 데이터 복구 처리기에 대 한 포인터입니다.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>설명

응용 프로그램의 데이터 복구 처리기는 열린 문서를 모니터링 하 고 자동으로 저장 합니다. 프레임 워크는 데이터 복구 처리기를 사용 하 여 응용 프로그램이 예기치 않게 종료 된 후 다시 시작 될 때 자동으로 저장 된 파일을 복원 합니다. 자세한 내용은 [CDataRecoveryHandler 클래스](../../mfc/reference/cdatarecoveryhandler-class.md)를 참조 하세요.

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a> CWinApp:: m_pszAppName

애플리케이션의 이름을 지정합니다.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>설명

응용 프로그램 이름은 [CWinApp](#cwinapp) 생성자에 전달 된 매개 변수에서 가져올 수 있으며, 지정 되지 않은 경우 ID가 AFX_IDS_APP_TITLE 인 리소스 문자열로 가져올 수 있습니다. 리소스에서 응용 프로그램 이름을 찾을 수 없는 경우 프로그램의에서 가져옵니다. EXE 파일 이름입니다.

전역 함수 [AfxGetAppName](application-information-and-management.md#afxgetappname)에서 반환 됩니다. `m_pszAppName`는 **const char** 형식의 공용 변수입니다 <strong>\*</strong> .

> [!NOTE]
> 에 값을 할당 하는 경우 `m_pszAppName` 힙에 동적으로 할당 되어야 합니다. `CWinApp`소멸자는 this 포인터를 사용 하 여 **free**()를 호출 합니다. `_tcsdup`() 런타임 라이브러리 함수를 사용 하 여 할당을 수행 하려고 합니다. 또한 새 값을 할당 하기 전에 현재 포인터와 연결 된 메모리를 해제 합니다. 예를 들어:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a> CWinApp:: m_pszExeName

확장명이 없는 응용 프로그램 실행 파일의 이름을 포함 합니다.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>설명

[M_pszAppName](#m_pszappname)와 달리이 이름에는 공백을 사용할 수 없습니다. `m_pszExeName`는 **const char** 형식의 공용 변수입니다 <strong>\*</strong> .

> [!NOTE]
> 에 값을 할당 하는 경우 `m_pszExeName` 힙에 동적으로 할당 되어야 합니다. `CWinApp`소멸자는 this 포인터를 사용 하 여 **free**()를 호출 합니다. `_tcsdup`() 런타임 라이브러리 함수를 사용 하 여 할당을 수행 하려고 합니다. 또한 새 값을 할당 하기 전에 현재 포인터와 연결 된 메모리를 해제 합니다. 예를 들어:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a> CWinApp:: m_pszHelpFilePath

응용 프로그램의 도움말 파일에 대 한 경로를 포함 합니다.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>설명

기본적으로 프레임 워크는 `m_pszHelpFilePath` "를 사용 하 여 응용 프로그램의 이름으로 초기화 됩니다. .HLP "가 추가 되었습니다. 도움말 파일의 이름을 변경 하려면 `m_pszHelpFilePath` 원하는 도움말 파일의 전체 이름이 포함 된 문자열을 가리키도록 설정 합니다. 이 작업을 수행 하는 편리한 장소는 응용 프로그램의 [InitInstance](#initinstance) 함수입니다. `m_pszHelpFilePath`는 **const char** 형식의 공용 변수입니다 <strong>\*</strong> .

> [!NOTE]
> 에 값을 할당 하는 경우 `m_pszHelpFilePath` 힙에 동적으로 할당 되어야 합니다. `CWinApp`소멸자는 this 포인터를 사용 하 여 **free**()를 호출 합니다. `_tcsdup`() 런타임 라이브러리 함수를 사용 하 여 할당을 수행 하려고 합니다. 또한 새 값을 할당 하기 전에 현재 포인터와 연결 된 메모리를 해제 합니다. 예를 들어:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a> CWinApp:: m_pszProfileName

응용 프로그램의 이름을 포함 합니다. INI 파일.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>설명

`m_pszProfileName`는 **const char** 형식의 공용 변수입니다 <strong>\*</strong> .

> [!NOTE]
> 에 값을 할당 하는 경우 `m_pszProfileName` 힙에 동적으로 할당 되어야 합니다. `CWinApp`소멸자는 this 포인터를 사용 하 여 **free**()를 호출 합니다. `_tcsdup`() 런타임 라이브러리 함수를 사용 하 여 할당을 수행 하려고 합니다. 또한 새 값을 할당 하기 전에 현재 포인터와 연결 된 메모리를 해제 합니다. 예를 들어:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a> CWinApp:: m_pszRegistryKey

레지스트리 또는 INI 파일에서 응용 프로그램 프로필 설정이 저장 되는 위치를 확인 하는 데 사용 됩니다.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>설명

일반적으로이 데이터 멤버는 읽기 전용으로 취급 됩니다.

- 값은 레지스트리 키에 저장 됩니다. 응용 프로그램 프로필 설정의 이름이 다음 레지스트리 키에 추가 됩니다. HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

에 값을 할당 하는 경우 `m_pszRegistryKey` 힙에 동적으로 할당 되어야 합니다. `CWinApp`소멸자는 this 포인터를 사용 하 여 **free**()를 호출 합니다. `_tcsdup`() 런타임 라이브러리 함수를 사용 하 여 할당을 수행 하려고 합니다. 또한 새 값을 할당 하기 전에 현재 포인터와 연결 된 메모리를 해제 합니다. 예를 들어:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a> CWinApp:: m_pszAppID

응용 프로그램 사용자 모델 ID입니다.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>설명

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a> CWinApp:: OnContextHelp

응용 프로그램 내에서 SHIFT + F1 도움말을 처리 합니다.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` `CWinApp` 클래스 메시지 맵에 문을 추가 하 고 액셀러레이터 키 테이블 항목 (일반적으로 SHIFT + F1)을 추가 하 여이 멤버 함수를 사용 하도록 설정 해야 합니다.

`OnContextHelp` 응용 프로그램을 도움말 모드로 전환 합니다. 커서가 화살표와 물음표로 바뀌고 사용자는 마우스 포인터를 이동 하 고 마우스 왼쪽 단추를 눌러 대화 상자, 창, 메뉴 또는 명령 단추를 선택할 수 있습니다. 이 멤버 함수는 커서 아래에 있는 개체의 도움말 컨텍스트를 검색 하 고 해당 도움말 컨텍스트를 사용 하 여 Windows 함수 WinHelp를 호출 합니다.

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a> CWinApp:: OnDDECommand

주 프레임 창에 DDE 실행 메시지가 수신 될 때 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>매개 변수

*lpszCommand*<br/>
응용 프로그램에서 받은 DDE 명령 문자열을 가리킵니다.

### <a name="return-value"></a>반환 값

명령이 처리 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 구현에서는 명령이 문서를 열기 위한 요청 인지 여부를 확인 하 고, 지정 된 경우 지정 된 문서를 엽니다. Windows 파일 관리자는 일반적으로 사용자가 데이터 파일을 두 번 클릭할 때 이러한 DDE 명령 문자열을 보냅니다. 인쇄할 명령과 같은 다른 DDE 실행 명령을 처리 하려면이 함수를 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a> CWinApp:: OnFileNew

ID_FILE_NEW 명령을 구현 합니다.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_FILE_NEW, OnFileNew )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 된 경우이 함수는 File New 명령의 실행을 처리 합니다.

기본 동작에 대 한 자세한 내용과이 멤버 함수를 재정의 하는 방법에 대 한 지침은 [Technical Note 22](../../mfc/tn022-standard-commands-implementation.md) 를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a> CWinApp:: OnFileOpen

ID_FILE_OPEN 명령을 구현 합니다.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 된 경우이 함수는 File Open 명령의 실행을 처리 합니다.

이 멤버 함수를 재정의 하는 방법에 대 한 기본 동작 및 지침에 대 한 자세한 내용은 [Technical Note 22](../../mfc/tn022-standard-commands-implementation.md)를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a> CWinApp:: OnFilePrintSetup

ID_FILE_PRINT_SETUP 명령을 구현 합니다.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 된 경우이 함수는 파일 인쇄 명령의 실행을 처리 합니다.

이 멤버 함수를 재정의 하는 방법에 대 한 기본 동작 및 지침에 대 한 자세한 내용은 [Technical Note 22](../../mfc/tn022-standard-commands-implementation.md)를 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a> CWinApp:: OnHelp

현재 컨텍스트를 사용하여 애플리케이션 내에서 F1 도움말을 처리합니다.

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>설명

일반적으로 F1 키에 대 한 액셀러레이터 키 항목을 추가 합니다. F1 키를 사용 하도록 설정 하는 것은 요구 사항이 아니라 유일한 규칙입니다.

`ON_COMMAND( ID_HELP, OnHelp )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 하면 사용자가 F1 키를 누를 때 프레임 워크에서 호출 됩니다.

이 메시지 처리기 함수의 기본 구현에서는 현재 창, 대화 상자 또는 메뉴 항목에 해당 하는 도움말 컨텍스트를 결정 한 다음 WINHELP.EXE를 호출 합니다. 현재 컨텍스트를 사용할 수 없는 경우 함수는 기본 컨텍스트를 사용 합니다.

현재 포커스가 있는 창, 대화 상자, 메뉴 항목 또는 도구 모음 단추가 아닌 다른 항목으로 도움말 컨텍스트를 설정 하려면이 멤버 함수를 재정의 합니다. `WinHelp`원하는 도움말 컨텍스트 ID를 사용 하 여를 호출 합니다.

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a> CWinApp:: OnHelpFinder

ID_HELP_FINDER 및 ID_DEFAULT_HELP 명령을 처리 합니다.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 된 경우 응용 프로그램의 사용자가 `WinHelp` 표준 **HELP_FINDER** 항목을 사용 하 여를 호출 하기 위해 Help Finder 명령을 선택할 때 프레임 워크는이 메시지 처리기 함수를 호출 합니다.

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a> CWinApp:: OnHelpIndex

ID_HELP_INDEX 명령을 처리 하 고 기본 도움말 항목을 제공 합니다.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 사용 하도록 설정 된 경우 응용 프로그램 사용자가 Help Index 명령을 선택 하 여 `WinHelp` 표준 **HELP_INDEX** 토픽으로 호출할 때 프레임 워크가이 메시지 처리기 함수를 호출 합니다.

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a> CWinApp:: OnHelpUsing

ID_HELP_USING 명령을 처리 합니다.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>설명

`ON_COMMAND( ID_HELP_USING, OnHelpUsing )` `CWinApp` 이 멤버 함수를 사용 하려면 클래스 메시지 맵에 문을 추가 해야 합니다. 응용 프로그램의 사용자가 `WinHelp` 표준 **HELP_HELPONHELP** 항목을 사용 하 여 응용 프로그램을 호출 하기 위해 명령을 사용 하는 도움말을 선택 하면 프레임 워크가이 메시지 처리기 함수를 호출 합니다.

## <a name="cwinapponidle"></a><a name="onidle"></a> CWinApp:: OnIdle

유휴 시간 처리를 수행 하려면이 멤버 함수를 재정의 합니다.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>매개 변수

*lCount*<br/>
`OnIdle`응용 프로그램의 메시지 큐가 비어 있을 때가 호출 될 때마다 증가 하는 카운터입니다. 이 개수는 새 메시지가 처리 될 때마다 0으로 다시 설정 됩니다. *Lcount* 매개 변수를 사용 하 여 메시지를 처리 하지 않고 응용 프로그램이 유휴 상태로 유지 된 시간의 상대적인 길이를 확인할 수 있습니다.

### <a name="return-value"></a>반환 값

0이 아니면 유휴 처리 시간을 더 받습니다. 유휴 시간을 더 이상 요구 하지 않는 경우 0입니다.

### <a name="remarks"></a>설명

`OnIdle` 는 응용 프로그램의 메시지 큐가 비어 있을 때 기본 메시지 루프에서 호출 됩니다. 재정의를 사용 하 여 사용자 고유의 백그라운드 유휴 처리기 작업을 호출 합니다.

`OnIdle` 는 유휴 처리 시간이 필요 하지 않음을 나타내려면 0을 반환 해야 합니다. *Lcount* 매개 변수는 `OnIdle` 메시지 큐가 비어 있을 때가 호출 될 때마다 증가 하며 새 메시지가 처리 될 때마다 0으로 다시 설정 됩니다. 이 수에 따라 다른 유휴 루틴을 호출할 수 있습니다.

다음은 유휴 루프 처리를 요약 합니다.

1. MFC 라이브러리의 메시지 루프가 메시지 큐를 확인 하 고 보류 중인 메시지를 찾지 못하면 `OnIdle` 응용 프로그램 개체에 대해를 호출 하 고 *lcount* 인수로 0을 제공 합니다.

2. `OnIdle` 일부 처리를 수행 하 고 0이 아닌 값을 반환 하 여 추가 처리를 위해 다시 호출 해야 함을 표시 합니다.

3. 메시지 루프는 메시지 큐를 다시 확인 합니다. 보류 중인 메시지가 없으면를 다시 호출 하 `OnIdle` 여 *lcount* 인수를 증가 시킵니다.

4. 결국는 `OnIdle` 모든 유휴 작업의 처리를 완료 하 고 0을 반환 합니다. 이는 메시지 큐에서 다음 메시지를 받을 때까지 메시지 루프에서 호출을 중지 하도록 지시 합니다 `OnIdle` .이 시점에서 인수를 0으로 설정 하 여 유휴 주기가 다시 시작 됩니다.

`OnIdle`응용 프로그램에서가 반환 될 때까지 사용자 입력을 처리할 수 없기 때문에에서 긴 작업을 수행 하지 마십시오 `OnIdle` .

> [!NOTE]
> 의 기본 구현은 `OnIdle` 메뉴 항목 및 도구 모음 단추와 같은 사용자 인터페이스 개체를 업데이트 하 고 내부 데이터 구조 정리를 수행 합니다. 따라서를 재정의 하 `OnIdle` `CWinApp::OnIdle` 는 경우 재정의 된 버전의를 사용 하 여를 호출 해야 합니다 `lCount` . 먼저 모든 기본 클래스 유휴 처리를 호출 합니다. 즉, 기본 클래스에서 `OnIdle` 0을 반환 합니다. 기본 클래스 처리가 완료 되기 전에 작업을 수행 해야 하는 경우 기본 클래스 구현을 검토 하 여 작업을 수행할 수 있는 적절 한 *Lcount* 를 선택 합니다.

메시지 `OnIdle` 큐에서 메시지를 검색할 때마다를 호출 하지 않으려면 [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)을 재정의할 수 있습니다. 응용 프로그램에서 매우 짧은 타이머를 설정 했거나 시스템이 WM_SYSTIMER 메시지를 전송 하는 경우가 `OnIdle` 반복적으로 호출 되 고 성능이 저하 됩니다.

### <a name="example"></a>예제

다음 두 예제에서는를 사용 하는 방법을 보여 줍니다 `OnIdle` . 첫 번째 예제에서는 *Lcount* 인수를 사용 하 여 작업의 우선 순위를 지정 하는 두 개의 유휴 작업을 처리 합니다. 첫 번째 작업은 높은 우선 순위 이며 가능 하면 항상 수행 해야 합니다. 두 번째 작업은 더 중요 하지 않으며 사용자 입력에 긴 일시 중지가 있는 경우에만 수행 해야 합니다. 의 기본 클래스 버전에 대 한 호출을 확인 합니다 `OnIdle` . 두 번째 예제에서는 다른 우선 순위로 유휴 작업 그룹을 관리 합니다.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a> CWinApp:: OpenDocumentFile

프레임 워크는이 메서드를 호출 하 여 응용 프로그램에 대 한 명명 된 [CDocument](../../mfc/reference/cdocument-class.md) 파일을 엽니다.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszFileName*<br/>
진행 열 파일의 이름입니다.

*bAddToMRU*<br/>
진행 TRUE는 문서가 가장 최근 파일 중 하나 임을 나타냅니다. FALSE는 문서가 가장 최근 파일 중 하나가 아님을 나타냅니다.

### <a name="return-value"></a>반환 값

성공 하면에 대 한 포인터 `CDocument` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

해당 이름을 가진 문서가 이미 열려 있는 경우 해당 문서를 포함 하는 첫 번째 프레임 창에 포커스가 표시 됩니다. 응용 프로그램에서 여러 문서 템플릿을 지 원하는 경우 프레임 워크는 파일 이름 확장명을 사용 하 여 문서 로드를 시도 하는 적절 한 문서 템플릿을 찾습니다. 성공 하면 문서 템플릿이 문서에 대 한 프레임 창과 뷰를 만듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a> CWinApp::P arseCommandLine

이 멤버 함수를 호출 하 여 명령줄을 구문 분석 하 고 매개 변수를 한 번에 하나씩 [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)로 보냅니다.

```cpp
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>매개 변수

*rCmdInfo*<br/>
[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

응용 프로그램 마법사를 사용 하 여 새 MFC 프로젝트를 시작 하면 응용 프로그램 마법사가의 로컬 인스턴스를 만든 `CCommandLineInfo` 다음 `ProcessShellCommand` `ParseCommandLine` [InitInstance](#initinstance) 멤버 함수에서 및를 호출 합니다. 명령줄은 아래에 설명 된 경로를 따릅니다.

1. 에서 생성 된 `InitInstance` `CCommandLineInfo` 개체는에 전달 됩니다 `ParseCommandLine` .

2. `ParseCommandLine` 그런 다음 `CCommandLineInfo::ParseParam` 은 각 매개 변수에 대해 한 번씩 반복적으로를 호출 합니다.

3. `ParseParam``CCommandLineInfo` [Processshellcommand](#processshellcommand)에 전달 되는 개체를 채웁니다.

4. `ProcessShellCommand` 명령줄 인수와 플래그를 처리 합니다.

필요에 따라를 직접 호출할 수 있습니다 `ParseCommandLine` .

명령줄 플래그에 대 한 자세한 내용은 [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)를 참조 하세요.

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a> CWinApp::P reTranslateMessage

Windows 함수 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 로 디스패치 되기 전에이 함수를 재정의 하 여 창 메시지를 필터링 합니다. 기본 구현에서는 액셀러레이터 키 변환을 수행 하므로 `CWinApp::PreTranslateMessage` 재정의 된 버전에서 멤버 함수를 호출 해야 합니다.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*pMsg*<br/>
처리할 메시지를 포함 하는 [MSG](/windows/win32/api/winuser/ns-winuser-msg) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

에서 메시지를 완전히 처리 `PreTranslateMessage` 하 고 추가로 처리 하지 않아야 하는 경우 0이 아닙니다. 메시지를 일반적인 방식으로 처리 해야 하는 경우 0입니다.

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a> CWinApp::P rocessMessageFilter

프레임 워크의 후크 함수는이 멤버 함수를 호출 하 여 특정 Windows 메시지를 필터링 하 고 응답 합니다.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>매개 변수

*code*<br/>
후크 코드를 지정 합니다. 이 멤버 함수는 코드를 사용 하 여 Lpmsg를 처리 하는 방법을 결정 *합니다.*

*lpMsg*<br/>
Windows [MSG](/windows/win32/api/winuser/ns-winuser-msg)t)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메시지가 처리 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

후크 함수는 응용 프로그램의 일반 메시지 처리에 전송 되기 전에 이벤트를 처리 합니다.

이 고급 기능을 재정의 하는 경우에는 기본 클래스 버전을 호출 하 여 프레임 워크의 후크 처리를 유지 해야 합니다.

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a> CWinApp::P rocessShellCommand

이 멤버 함수는 [](#initinstance) `CCommandLineInfo` *rcmdinfo* 로 식별 되는 개체에서 전달 되는 매개 변수를 수락 하 고 표시 된 작업을 수행 하기 위해 InitInstance에서 호출 됩니다.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>매개 변수

*rCmdInfo*<br/>
[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

셸 명령이 성공적으로 처리 되는 경우 0이 아닙니다. 0 인 경우 [InitInstance](#initinstance)에서 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

응용 프로그램 마법사를 사용 하 여 새 MFC 프로젝트를 시작 하면 응용 프로그램 마법사가의 로컬 인스턴스를 만든 `CCommandLineInfo` 다음를 호출 `ProcessShellCommand` 하 고 멤버 함수에서 [ParseCommandLine](#parsecommandline) 를 호출 합니다 `InitInstance` . 명령줄은 아래에 설명 된 경로를 따릅니다.

1. 에서 생성 된 `InitInstance` `CCommandLineInfo` 개체는에 전달 됩니다 `ParseCommandLine` .

2. `ParseCommandLine` 그런 다음 [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) 를 반복 해 서 각 매개 변수에 대해 한 번씩 호출 합니다.

3. `ParseParam``CCommandLineInfo`에 전달 되는 개체를 채웁니다 `ProcessShellCommand` .

4. `ProcessShellCommand` 명령줄 인수와 플래그를 처리 합니다.

`CCommandLineInfo` [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)으로 식별 되는 개체의 데이터 멤버는 클래스 내에 정의 된 다음과 같은 열거형 형식입니다 `CCommandLineInfo` .

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

이러한 각 값에 대 한 간략 한 설명은를 참조 하십시오 `CCommandLineInfo::m_nShellCommand` .

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a> CWinApp::P rocessWndProcException

처리기가 응용 프로그램의 메시지 또는 명령 처리기 중 하나에서 throw 된 예외를 catch 하지 않을 때마다 프레임 워크는이 멤버 함수를 호출 합니다.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>매개 변수

*e*<br/>
Catch 되지 않은 예외에 대 한 포인터입니다.

*pMsg*<br/>
프레임 워크에서 예외를 throw 한 windows 메시지에 대 한 정보를 포함 하는 [MSG](/windows/win32/api/winuser/ns-winuser-msg)t)입니다.

### <a name="return-value"></a>반환 값

Windows에 반환 해야 하는 값입니다. 일반적으로 windows 메시지의 경우 0L, 명령 메시지의 경우 1L (TRUE)입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 직접 호출 하지 마세요.

이 멤버 함수의 기본 구현에서는 메시지 상자를 만듭니다. Catch 되지 않은 예외가 메뉴, 도구 모음 또는 액셀러레이터 명령 오류로 인해 발생 하는 경우 메시지 상자에 "명령 실패" 메시지가 표시 됩니다. 그렇지 않으면 "내부 응용 프로그램 오류" 메시지를 표시 합니다.

예외에 대 한 전역 처리를 제공 하려면이 멤버 함수를 재정의 합니다. 메시지 상자를 표시 하려는 경우에만 기본 기능을 호출 합니다.

## <a name="cwinappregister"></a><a name="register"></a> CWinApp:: Register

에서 처리 하지 않는 등록 작업을 수행 `RegisterShellFileTypes` 합니다.

```
virtual BOOL Register();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

기본 구현에서는 단순히 TRUE를 반환 합니다. 사용자 지정 된 등록 단계를 제공 하려면이 함수를 재정의 합니다.

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a> CWinApp:: RegisterShellFileTypes

이 멤버 함수를 호출 하 여 모든 응용 프로그램의 문서 형식을 Windows 파일 관리자에 등록 합니다.

```cpp
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>매개 변수

*bCompat*<br/>
진행 TRUE로 설정 하면 셸 명령에 대 한 등록 항목을 인쇄 및 인쇄 하 여 사용자가 셸에서 직접 파일을 인쇄 하거나 파일을 프린터 개체로 끌어 놓을 수 있습니다. 또한 DefaultIcon 키를 추가 합니다. 이 매개 변수는 이전 버전과의 호환성을 위해 기본적으로 FALSE입니다.

### <a name="remarks"></a>설명

이를 통해 사용자는 파일 관리자 내에서 응용 프로그램을 두 번 클릭 하 여 응용 프로그램에서 만든 데이터 파일을 열 수 있습니다. `RegisterShellFileTypes`응용 프로그램의 각 문서 템플릿에 대해 [Adddoctemplate](#adddoctemplate) 을 호출한 후를 호출 합니다. 또한를 호출할 때 [EnableShellOpen](#enableshellopen) 멤버 함수를 호출 `RegisterShellFileTypes` 합니다.

`RegisterShellFileTypes` 응용 프로그램에서 유지 관리 하는 [Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체의 목록을 반복 하 고, 각 문서 템플릿에 대해 Windows에서 파일 연결에 대해 유지 관리 하는 등록 데이터베이스에 항목을 추가 합니다. 파일 관리자는 이러한 항목을 사용 하 여 사용자가 두 번 클릭 하면 데이터 파일을 엽니다. 이렇게 하면를 제공할 필요가 없습니다. 응용 프로그램을 사용 하는 REG 파일.

> [!NOTE]
> `RegisterShellFileTypes` 사용자가 관리자 권한으로 프로그램을 실행 하는 경우에만 작동 합니다. 프로그램에 관리자 권한이 없는 경우 레지스트리 키를 변경할 수 없습니다.

등록 데이터베이스에서 지정 된 파일 이름 확장명을 다른 파일 형식과 이미 연결한 경우에는 새 연결을 만들지 않습니다. `CDocTemplate`이 정보를 등록 하는 데 필요한 문자열 형식은 클래스를 참조 하세요.

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a> CWinApp:: RegisterWithRestartManager

다시 시작 관리자를 사용 하 여 응용 프로그램을 등록 합니다.

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>매개 변수

*bRegisterRecoveryCallback*\
진행 TRUE는 응용 프로그램의이 인스턴스가 복구 콜백 함수를 사용 함을 나타냅니다. FALSE는 그렇지 않음을 나타냅니다. 응용 프로그램이 예기치 않게 종료 되 면 프레임 워크에서 복구 콜백 함수를 호출 합니다. 자세한 내용은 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)을 참조 하세요.

*strRestartIdentifier*\
진행 다시 시작 관리자의 인스턴스를 식별 하는 고유 문자열입니다. 다시 시작 관리자 식별자는 응용 프로그램의 각 인스턴스에 대해 고유 합니다.

*pwzCommandLineArgs*\
진행 명령줄에서 추가 인수를 포함 하는 문자열입니다.

*dwRestartFlags*\
진행 다시 시작 관리자에 대 한 선택적 플래그입니다. 자세한 내용은 설명 섹션을 참조하세요.

*pRecoveryCallback*\
진행 복구 콜백 함수입니다. 이 함수는 LPVOID 매개 변수를 입력으로 사용 하 고 DWORD를 반환 해야 합니다. 기본 복구 콜백 함수는 `CWinApp::ApplicationRecoveryCallback` 입니다.

*lpvParam*\
진행 복구 콜백 함수에 대 한 입력 매개 변수입니다. 자세한 내용은 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)을 참조 하세요.

*dwPingInterval*\
진행 복구 콜백 함수가 반환 될 때까지 다시 시작 관리자가 대기 하는 시간입니다. 이 매개 변수는 밀리초 단위입니다.

*dwCallbackFlags*\
진행 복구 콜백 함수에 전달 된 플래그입니다. 다음에 사용하도록 예약됩니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK 하 고, 그렇지 않으면 오류 코드입니다.

### <a name="remarks"></a>설명

응용 프로그램에서 작업 파일에 대 한 기본 MFC 구현을 사용 하는 경우의 간단한 버전을 사용 해야 합니다 `RegisterWithRestartManager` . `RegisterWithRestartManager`응용 프로그램의 자동 저장 동작을 사용자 지정 하려면의 복합 버전을 사용 합니다.

*StrRestartIdentifier* 에 대 한 빈 문자열을 사용 하 여이 메서드를 호출 하는 경우는 `RegisterWithRestartManager` 다시 시작 관리자의이 인스턴스에 대 한 고유 식별자 문자열을 만듭니다.

응용 프로그램이 예기치 않게 종료 되 면 다시 시작 관리자가 명령줄에서 응용 프로그램을 다시 시작 하 고 고유한 다시 시작 식별자를 선택적 인수로 제공 합니다. 이 시나리오에서 프레임 워크는 `RegisterWithRestartManager` 두 번 호출 합니다. 첫 번째 호출은 [CWinApp:: InitInstance](#initinstance) 에서 문자열 식별자에 대 한 빈 문자열을 가져옵니다. 그런 다음 [CWinApp::P](#processshellcommand) 메서드는 `RegisterWithRestartManager` 고유한 다시 시작 식별자를 사용 하 여 rocessshellcommand를 호출 합니다.

다시 시작 관리자를 사용 하 여 응용 프로그램을 등록 하면 다시 시작 관리자가 응용 프로그램을 모니터링 합니다. 응용 프로그램이 예기치 않게 종료 되는 경우 다시 시작 관리자는 종료 프로세스 중에 복구 콜백 함수를 호출 합니다. 다시 시작 관리자는 복구 콜백 함수의 응답에 대해 *dwPingInterval* 를 대기 합니다. 이 시간 내에 복구 콜백 함수가 응답 하지 않으면 복구 콜백 함수를 실행 하지 않고 응용 프로그램이 종료 됩니다.

기본적으로 dwRestartFlags은 지원 되지 않지만 나중에 사용 하기 위해 제공 됩니다. *DwRestartFlags* 에 사용할 수 있는 값은 다음과 같습니다.

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a> CWinApp:: ReopenPreviousFilesAtRestart

응용 프로그램이 예기치 않게 종료 될 때 열려 있던 파일을 다시 시작 관리자가 다시 열 지 여부를 결정 합니다.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>반환 값

TRUE 이면 다시 시작 관리자가 이전에 연 파일을 다시 엽니다. FALSE는 다시 시작 관리자가 그렇지 않음을 나타냅니다.

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a> CWinApp:: RestartInstance

다시 시작 관리자에 의해 시작 된 응용 프로그램 다시 시작을 처리 합니다.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>반환 값

데이터 복구 처리기가 이전에 열린 문서를 여는 경우 TRUE입니다. 데이터 복구 처리기에 오류가 있거나 이전에 열린 문서가 없는 경우 FALSE입니다.

### <a name="remarks"></a>설명

다시 시작 관리자가 응용 프로그램을 다시 시작 하면 프레임 워크에서이 메서드를 호출 합니다. 이 메서드는 데이터 복구 처리기를 검색 하 고 자동으로 저장 된 파일을 복원 합니다. 이 메서드는 [CDataRecoveryHandler:: RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) 를 호출 하 여 사용자가 자동으로 저장 된 파일을 복원 하려고 할지 여부를 결정 합니다.

이 메서드는 [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) 가 열려 있는 문서가 없음을 확인 하는 경우 FALSE를 반환 합니다. 열려 있는 문서가 없으면 응용 프로그램이 일반적으로 시작 됩니다.

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a> CWinApp:: RestoreAutosavedFilesAtRestart

다시 시작 관리자가 응용 프로그램을 다시 시작할 때 자동으로 저장 된 파일을 복원할지 여부를 결정 합니다.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>반환 값

TRUE는 다시 시작 관리자가 자동으로 저장 된 파일을 복원 함을 나타냅니다. FALSE는 다시 시작 관리자가 그렇지 않음을 나타냅니다.

## <a name="cwinapprun"></a><a name="run"></a> CWinApp:: Run

기본 메시지 루프를 제공 합니다.

```
virtual int Run();
```

### <a name="return-value"></a>반환 값

**`int`** 에서 반환 하는 값입니다 `WinMain` .

### <a name="remarks"></a>설명

`Run` 응용 프로그램이 WM_QUIT 메시지를 받을 때까지 Windows 메시지를 가져와 디스패치합니다. 응용 프로그램의 메시지 큐에 현재 메시지가 없으면 OnIdle을 `Run` 호출 [](#onidle) 하 여 유휴 시간 처리를 수행 합니다. 들어오는 메시지는 특수 처리를 위해 [PreTranslateMessage](#pretranslatemessage) 멤버 함수로 이동 하 고 `TranslateMessage` 표준 키보드 변환의 경우 windows 함수로 이동 합니다. 마지막으로 `DispatchMessage` windows 함수가 호출 됩니다.

`Run` 는 거의 재정의 되지 않지만 특수 동작을 제공 하도록 재정의할 수 있습니다.

## <a name="cwinapprunautomated"></a><a name="runautomated"></a> CWinApp:: RunAutomated

이 함수를 호출 하 여 " **/Automation**" 또는 " **-Automation**" 옵션이 있는지 여부를 확인 합니다 .이 옵션은 클라이언트 응용 프로그램에서 서버 응용 프로그램을 시작 했는지 여부를 나타냅니다.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>반환 값

옵션이 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

있는 경우 옵션이 명령줄에서 제거 됩니다. OLE 자동화에 대 한 자세한 내용은 [자동화 서버](../../mfc/automation-servers.md)문서를 참조 하세요.

## <a name="cwinapprunembedded"></a><a name="runembedded"></a> CWinApp:: RunEmbedded

이 함수를 호출 하 여 " **프로그램이/embedding**" 또는 " **-포함**" 옵션이 있는지 여부를 확인 합니다 .이 옵션은 클라이언트 응용 프로그램에서 서버 응용 프로그램을 시작 했는지 여부를 나타냅니다.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>반환 값

옵션이 있으면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

있는 경우 옵션이 명령줄에서 제거 됩니다. 포함에 대 한 자세한 내용은 서버 [: 서버 구현](../../mfc/servers-implementing-a-server.md)문서를 참조 하세요.

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a> CWinApp:: SaveAllModified

응용 프로그램의 주 프레임 창을 닫을 때 또는 WM_QUERYENDSESSION 메시지를 통해 모든 문서를 저장 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>반환 값

응용 프로그램을 종료 하는 데 안전한 경우 0이 아님 응용 프로그램을 종료 하는 것이 안전 하지 않은 경우 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수의 기본 구현에서는 [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) 멤버 함수를 호출 하 여 응용 프로그램 내의 모든 수정 된 문서를 차례로 호출 합니다.

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a> CWinApp:: SelectPrinter

이 멤버 함수를 호출 하 여 특정 프린터를 선택 하 고 이전에 인쇄 대화 상자에서 선택한 프린터를 해제 합니다.

```cpp
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>매개 변수

*hDevNames*<br/>
특정 프린터의 드라이버, 장치 및 출력 포트 이름을 식별 하는 [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)t)에 대 한 핸들입니다.

*hDevMode*<br/>
프린터의 장치 초기화 및 환경에 대 한 정보를 지정 하는 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 구조체에 대 한 핸들입니다.

*bFreeOld*<br/>
이전에 선택한 프린터를 해제 합니다.

### <a name="remarks"></a>설명

*Hdevmode* 및 *HDEVNAMES* 가 모두 NULL 인 경우는 `SelectPrinter` 현재 기본 프린터를 사용 합니다.

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a> CWinApp:: SetHelpMode

응용 프로그램의 도움말 형식을 설정 합니다.

```cpp
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>매개 변수

*eHelpType*<br/>
사용할 도움말의 유형을 지정 합니다. 자세한 내용은 [CWinApp:: m_eHelpType](#m_ehelptype) 를 참조 하세요.

### <a name="remarks"></a>설명

응용 프로그램의 도움말 형식을 설정 합니다.

응용 프로그램의 도움말 형식을 HTMLHelp로 설정 하려면 [EnableHTMLHelp](#enablehtmlhelp)를 호출 하면 됩니다. 를 호출 하면 `EnableHTMLHelp` 응용 프로그램은 HTMLHelp를 도움말 응용 프로그램으로 사용 해야 합니다. WinHelp를 사용 하도록 변경 하려는 경우를 호출 하 `SetHelpMode` 고 *Ehelptype* 을로 설정할 수 있습니다 `afxWinHelp` .

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a> CWinApp:: SetRegistryKey

응용 프로그램 설정이 INI 파일 대신 레지스트리에 저장 되도록 합니다.

```cpp
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>매개 변수

*lpszRegistryKey*<br/>
키의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nIDRegistryKey*<br/>
레지스트리 키의 이름을 포함 하는 문자열 리소스의 ID입니다.

### <a name="remarks"></a>설명

이 함수는  `GetProfileInt` 의,, `GetProfileString` `WriteProfileInt` 및 `WriteProfileString` 멤버 함수 `CWinApp` 에서 사용 되는 m_pszRegistryKey를 설정 합니다. 이 함수가 호출 되 면 가장 최근에 사용한 (MRU) 파일의 목록도 레지스트리에 저장 됩니다. 레지스트리 키는 일반적으로 회사의 이름입니다. 이 파일은 HKEY_CURRENT_USER\Software\\<회사 이름 \> \\<응용 프로그램 이름 \> \\<섹션 이름 \> \\<값 이름과 \> 같은 형식의 키에 저장 됩니다.

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a> CWinApp:: SupportsApplicationRecovery

다시 시작 관리자가 예기치 않게 종료 된 응용 프로그램을 복구할 지 여부를 결정 합니다.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>반환 값

TRUE는 다시 시작 관리자가 응용 프로그램을 복구 함을 나타냅니다. FALSE는 다시 시작 관리자가 그렇지 않음을 나타냅니다.

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a> CWinApp:: SupportsAutosaveAtInterval

다시 시작 관리자가 열려 있는 문서를 일정 한 간격으로 자동 저장 하는지 여부를 결정 합니다.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>반환 값

TRUE는 다시 시작 관리자가 열려 있는 문서를 자동으로 저장 함을 나타냅니다. FALSE는 다시 시작 관리자가 그렇지 않음을 나타냅니다.

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a> CWinApp:: SupportsAutosaveAtRestart

응용 프로그램이 다시 시작 될 때 다시 시작 관리자가 열려 있는 모든 문서를 자동으로 저장할지 여부를 결정 합니다.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>반환 값

TRUE는 응용 프로그램이 다시 시작 될 때 다시 시작 관리자가 열려 있는 문서를 자동으로 저장 함을 나타냅니다. FALSE는 다시 시작 관리자가 그렇지 않음을 나타냅니다.

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a> CWinApp:: SupportsRestartManager

응용 프로그램에서 다시 시작 관리자를 지원 하는지 여부를 확인 합니다.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>반환 값

TRUE는 응용 프로그램이 다시 시작 관리자를 지원함을 나타냅니다. FALSE는 응용 프로그램이 그렇지 않음을 나타냅니다.

## <a name="cwinappunregister"></a><a name="unregister"></a> CWinApp:: 등록 취소

응용 프로그램 개체에서 등록 된 모든 파일의 등록을 취소 합니다.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아닌 값이고, 실패하면 0입니다.

### <a name="remarks"></a>설명

`Unregister`함수는 응용 프로그램 개체 및 [Register](#register) 함수에서 수행 하는 등록을 취소 합니다. 일반적으로 두 함수는 MFC에서 암시적으로 호출 되므로 코드에 표시 되지 않습니다.

사용자 지정 등록 취소 단계를 수행 하려면이 함수를 재정의 합니다.

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a> CWinApp:: UnregisterShellFileTypes

Windows 파일 관리자를 사용 하 여 모든 응용 프로그램의 문서 유형을 등록 취소 하려면이 멤버 함수를 호출 합니다.

```cpp
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a> CWinApp:: WinHelp

이 멤버 함수를 호출 하 여 WinHelp 응용 프로그램을 호출 합니다.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>매개 변수

*dwData*<br/>
추가 데이터를 지정 합니다. 사용 되는 값은 *Ncmd* 매개 변수의 값에 따라 달라 집니다.

*nCmd*<br/>
요청한 도움말의 형식을 지정합니다. 가능한 값 목록과이 값이 *Dwdata* 매개 변수에 영향을 주는 방법은 [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows 함수를 참조 하세요.

### <a name="remarks"></a>설명

또한 프레임 워크는이 함수를 호출 하 여 WinHelp 응용 프로그램을 호출 합니다.

응용 프로그램이 종료 되 면 프레임 워크가 자동으로 WinHelp 응용 프로그램을 닫습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a> CWinApp:: WriteProfileBinary

응용 프로그램 레지스트리의 지정 된 섹션 또는에 이진 데이터를 쓰려면이 멤버 함수를 호출 합니다. INI 파일.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다. 섹션이 없으면 생성 됩니다. 섹션 이름은 대/소문자를 구분 합니다. 문자열은 대/소문자를 임의로 조합 하 여 사용할 수 있습니다.

*lpszEntry*<br/>
값을 쓸 항목을 포함 하는 null로 끝나는 문자열을 가리킵니다. 지정 된 섹션에 항목이 없으면 해당 항목이 생성 됩니다.

*pData*<br/>
쓸 데이터를 가리킵니다.

*nBytes*<br/>
쓸 바이트 수를 포함 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

이 예제에서는를 사용 하 여 `CWinApp* pApp = AfxGetApp();` `WriteProfileBinary` `GetProfileBinary` MFC 응용 프로그램의 모든 함수에서 사용할 수 있는 방법을 보여 주는 CWinApp 클래스를 가져옵니다.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

다른 예제를 보려면 [CWinApp:: GetProfileBinary](#getprofilebinary)의 예제를 참조 하세요.

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a> CWinApp:: WriteProfileInt

응용 프로그램 레지스트리의 지정 된 섹션에 지정 된 값을 쓰려면이 멤버 함수를 호출 합니다. INI 파일.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다. 섹션이 없으면 생성 됩니다. 섹션 이름은 대/소문자를 구분 합니다. 문자열은 대/소문자를 임의로 조합 하 여 사용할 수 있습니다.

*lpszEntry*<br/>
값을 쓸 항목을 포함 하는 null로 끝나는 문자열을 가리킵니다. 지정 된 섹션에 항목이 없으면 해당 항목이 생성 됩니다.

*N 값*<br/>
쓸 값을 포함 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

이 예제에서는를 사용 `CWinApp* pApp = AfxGetApp();` 하 여 `WriteProfileString` ,, 및가 `WriteProfileInt` `GetProfileString` `GetProfileInt` MFC 응용 프로그램의 모든 함수에서 사용 될 수 있는 방법을 보여 주는 CWinApp 클래스를 가져옵니다.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

다른 예제를 보려면 [CWinApp:: GetProfileInt](#getprofileint)의 예제를 참조 하세요.

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a> CWinApp:: WriteProfileString

이 멤버 함수를 호출 하 여 지정 된 문자열을 응용 프로그램 레지스트리의 지정 된 섹션 또는에 씁니다. INI 파일.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>매개 변수

*lpszSection*<br/>
항목이 포함된 섹션을 지정하는 null로 끝나는 문자열을 가리킵니다. 섹션이 없으면 생성 됩니다. 섹션 이름은 대/소문자를 구분 합니다. 문자열은 대/소문자를 임의로 조합 하 여 사용할 수 있습니다.

*lpszEntry*<br/>
값을 쓸 항목을 포함 하는 null로 끝나는 문자열을 가리킵니다. 지정 된 섹션에 항목이 없으면 해당 항목이 생성 됩니다. 이 매개 변수가 NULL 이면 *lpszSection* 에서 지정한 섹션이 삭제 됩니다.

*lpszValue*<br/>
쓸 문자열을 가리킵니다. 이 매개 변수가 NULL 이면 *lpszEntry* 매개 변수로 지정 된 항목이 삭제 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

다른 예제를 보려면 [CWinApp:: GetProfileInt](#getprofileint)의 예제를 참조 하세요.

## <a name="cwinappsetappid"></a><a name="setappid"></a> CWinApp:: SetAppID

응용 프로그램의 응용 프로그램 사용자 모델 ID를 명시적으로 설정 합니다. 사용자 인터페이스가 사용자에 게 표시 되기 전에이 메서드를 호출 해야 합니다. 가장 좋은 장소는 응용 프로그램 생성자입니다.

```cpp
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>매개 변수

*lpcszAppID*<br/>
응용 프로그램 사용자 모델 ID를 지정 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[CWinThread 클래스](../../mfc/reference/cwinthread-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[방법: 다시 시작 관리자 지원 추가](../../mfc/how-to-add-restart-manager-support.md)

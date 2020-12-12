---
description: '자세히 알아보기: CCommandLineInfo 클래스'
title: CCommandLineInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 4c26ae86608725caa61ad4d1077bed01a3f40385
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227925"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 클래스

애플리케이션을 시작할 때 명령줄을 구문 분석하는 데 유용합니다.

## <a name="syntax"></a>구문

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|기본 개체를 생성 `CCommandLineInfo` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|개별 매개 변수를 구문 분석 하려면이 콜백을 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CCommandLineInfo:: m_bRunAutomated](#m_brunautomated)|명령줄 `/Automation` 옵션을 찾을 수 있음을 나타냅니다.|
|[CCommandLineInfo:: m_bRunEmbedded](#m_brunembedded)|명령줄 `/Embedding` 옵션을 찾을 수 있음을 나타냅니다.|
|[CCommandLineInfo:: m_bShowSplash](#m_bshowsplash)|시작 화면을 표시 해야 하는지 여부를 나타냅니다.|
|[CCommandLineInfo:: m_nShellCommand](#m_nshellcommand)|처리할 셸 명령을 나타냅니다.|
|[CCommandLineInfo:: m_strDriverName](#m_strdrivername)|셸 명령이 인쇄 되는 경우 드라이버 이름을 나타냅니다. 그렇지 않으면 비어 있습니다.|
|[CCommandLineInfo:: m_strFileName](#m_strfilename)|열거나 인쇄할 파일 이름을 나타냅니다. shell 명령이 New 또는 DDE 인 경우 비어 있습니다.|
|[CCommandLineInfo:: m_strPortName](#m_strportname)|셸 명령이 인쇄 되는 경우 포트 이름을 나타냅니다. 그렇지 않으면 비어 있습니다.|
|[CCommandLineInfo:: m_strPrinterName](#m_strprintername)|셸 명령이 인쇄 되는 경우 프린터 이름을 나타냅니다. 그렇지 않으면 비어 있습니다.|
|[CCommandLineInfo:: m_strRestartIdentifier](#m_strrestartidentifier)|다시 시작 관리자가 응용 프로그램을 다시 시작 하는 경우 다시 시작 관리자에 대 한 고유 다시 시작 식별자를 나타냅니다.|

## <a name="remarks"></a>설명

MFC 응용 프로그램은 일반적으로 해당 응용 프로그램 개체의 [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 함수에서이 클래스의 로컬 인스턴스를 만듭니다. 그런 다음이 개체는 [CWinApp::P arsecommandline](../../mfc/reference/cwinapp-class.md#parsecommandline)전달 됩니다 .이는 [ParseParam](#parseparam) 를 반복적으로 호출 하 여 개체를 채웁니다 `CCommandLineInfo` . `CCommandLineInfo`그런 다음이 개체는 [CWinApp::P rocessshellcommand](../../mfc/reference/cwinapp-class.md#processshellcommand) 에 전달 되어 명령줄 인수와 플래그를 처리 합니다.

이 개체를 사용 하 여 다음 명령줄 옵션과 매개 변수를 캡슐화 할 수 있습니다.

|명령줄 인수|명령이 실행 됨|
|----------------------------|----------------------|
|*app*|새 파일입니다.|
|*앱* 파일 이름|파일을 엽니다.|
|*앱* `/p` 이름도|파일을 기본 프린터로 인쇄 합니다.|
|*앱* `/pt` 파일 이름 프린터 드라이버 포트|지정 된 프린터에 파일을 인쇄 합니다.|
|*앱*`/dde`|DDE 명령을 시작 하 고 기다립니다.|
|*앱*`/Automation`|OLE 자동화 서버로 시작 합니다.|
|*앱*`/Embedding`|시작을 시작 하 여 포함 된 OLE 항목을 편집 합니다.|
|*앱*`/Register`<br /><br /> *앱*`/Regserver`|응용 프로그램에 등록 작업을 수행 하도록 알립니다.|
|*앱*`/Unregister`<br /><br /> *앱*`/Unregserver`|등록 취소 작업을 수행 하도록 응용 프로그램에 알립니다.|

에서 새 클래스를 파생 시켜 `CCommandLineInfo` 다른 플래그와 매개 변수 값을 처리 합니다. 새 플래그를 처리 하려면 [ParseParam](#parseparam) 를 재정의 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a> CCommandLineInfo::CCommandLineInfo

이 생성자는 `CCommandLineInfo` 기본값을 사용 하 여 개체를 만듭니다.

```
CCommandLineInfo();
```

### <a name="remarks"></a>설명

기본값은 시작 화면 ()을 표시 하 `m_bShowSplash=TRUE` 고 파일 메뉴에서 새 명령 ( `m_nShellCommand` **= NewFile**)을 실행 하는 것입니다.

응용 프로그램 프레임 워크는 [ParseParam](#parseparam) 을 호출 하 여이 개체의 데이터 멤버를 채웁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a> CCommandLineInfo:: m_bRunAutomated

`/Automation`명령줄에서 플래그를 찾을 수 있음을 나타냅니다.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>설명

TRUE 이면 OLE 자동화 서버로 시작을 의미 합니다.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a> CCommandLineInfo:: m_bRunEmbedded

`/Embedding`명령줄에서 플래그를 찾을 수 있음을 나타냅니다.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>설명

TRUE 이면 포함 된 OLE 항목을 편집 하기 위한 시작을 의미 합니다.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a> CCommandLineInfo:: m_bShowSplash

시작 화면이 표시 되어야 함을 나타냅니다.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>설명

TRUE 이면 시작 하는 동안이 응용 프로그램에 대 한 시작 화면이 표시 되어야 함을 의미 합니다. [ParseParam](#parseparam) 의 기본 구현에서는 [m_nShellCommand](#m_nshellcommand) 이와 같으면이 데이터 멤버를 TRUE로 설정 합니다 `CCommandLineInfo::FileNew` .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a> CCommandLineInfo:: m_nShellCommand

이 응용 프로그램 인스턴스에 대 한 셸 명령을 나타냅니다.

```
m_nShellCommand;
```

### <a name="remarks"></a>설명

이 데이터 멤버의 형식은 클래스에서 정의 되는 다음과 같은 열거형 형식입니다 `CCommandLineInfo` .

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

이러한 값에 대 한 간략 한 설명은 다음 목록을 참조 하세요.

- `CCommandLineInfo::FileNew` 는 명령줄에서 파일 이름을 찾을 수 없음을 나타냅니다.

- `CCommandLineInfo::FileOpen` 는 명령줄에서 파일 이름을 찾았지만 명령줄에서 다음 플래그를 찾지 못했음을 나타냅니다. `/p` , `/pt` , `/dde` .

- `CCommandLineInfo::FilePrint``/p`명령줄에서 플래그를 찾을 수 있음을 나타냅니다.

- `CCommandLineInfo::FilePrintTo``/pt`명령줄에서 플래그를 찾을 수 있음을 나타냅니다.

- `CCommandLineInfo::FileDDE``/dde`명령줄에서 플래그를 찾을 수 있음을 나타냅니다.

- `CCommandLineInfo::AppRegister``/Register` `/Regserver` 명령줄에서 또는 플래그를 찾았지만 응용 프로그램에 등록 하도록 요청 했음을 나타냅니다.

- `CCommandLineInfo::AppUnregister``/Unregister`또는 `/Unregserver` 응용 프로그램을 등록 취소 하도록 요청 했음을 나타냅니다.

- `CCommandLineInfo::RestartByRestartManager` 다시 시작 관리자가 응용 프로그램을 다시 시작한 것을 나타냅니다.

- `CCommandLineInfo::FileNothing` 시작할 때 새 MDI 자식 창 표시를 해제 합니다. 기본적으로 응용 프로그램 마법사에서 생성 된 MDI 응용 프로그램은 시작 시 새 자식 창을 표시 합니다. 이 기능을 해제 하기 위해 응용 프로그램은 `CCommandLineInfo::FileNothing` [processshellcommand](../../mfc/reference/cwinapp-class.md#processshellcommand)를 호출할 때 shell 명령으로 사용할 수 있습니다. `ProcessShellCommand` 는 `InitInstance( )` 모든 파생 클래스의에서 호출 됩니다 `CWinApp` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a> CCommandLineInfo:: m_strDriverName

명령줄에 플래그 이외의 세 번째 매개 변수 값을 저장 합니다.

```
CString m_strDriverName;
```

### <a name="remarks"></a>설명

이 매개 변수는 일반적으로 셸 인쇄 명령에 대 한 프린터 드라이버의 이름입니다. [ParseParam](#parseparam) 의 기본 구현은 `/pt` 명령줄에서 플래그를 찾은 경우에만이 데이터 멤버를 설정 합니다.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a> CCommandLineInfo:: m_strFileName

명령줄에 플래그가 지정 되지 않은 첫 번째 매개 변수의 값을 저장 합니다.

```
CString m_strFileName;
```

### <a name="remarks"></a>설명

이 매개 변수는 일반적으로 열려는 파일의 이름입니다.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a> CCommandLineInfo:: m_strPortName

명령줄에 플래그 이외의 네 번째 매개 변수 값을 저장 합니다.

```
CString m_strPortName;
```

### <a name="remarks"></a>설명

이 매개 변수는 일반적으로 shell으로 인쇄 명령의 프린터 포트 이름입니다. [ParseParam](#parseparam) 의 기본 구현은 `/pt` 명령줄에서 플래그를 찾은 경우에만이 데이터 멤버를 설정 합니다.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a> CCommandLineInfo:: m_strPrinterName

명령줄에 플래그 이외의 두 번째 매개 변수 값을 저장 합니다.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>설명

이 매개 변수는 일반적으로 셸 인쇄 명령의 프린터 이름입니다. [ParseParam](#parseparam) 의 기본 구현은 `/pt` 명령줄에서 플래그를 찾은 경우에만이 데이터 멤버를 설정 합니다.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a> CCommandLineInfo:: m_strRestartIdentifier

명령줄의 고유한 다시 시작 식별자입니다.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>설명

Restart 식별자는 응용 프로그램의 각 인스턴스에 대해 고유 합니다.

다시 시작 관리자가 응용 프로그램을 종료 하 고 다시 시작 하도록 구성 된 경우 다시 시작 관리자는 다시 시작 식별자를 선택적 매개 변수로 사용 하 여 명령줄에서 응용 프로그램을 실행 합니다. 다시 시작 관리자가 다시 시작 식별자를 사용 하는 경우 응용 프로그램은 이전에 열린 문서를 다시 열고 자동으로 저장 된 파일을 복구할 수 있습니다.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a> CCommandLineInfo::P arseParam

프레임 워크는이 함수를 호출 하 여 명령줄에서 개별 매개 변수를 구문 분석/해석 합니다. 두 번째 버전은 유니코드 프로젝트의 첫 번째 버전과 다릅니다.

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>매개 변수

*pszParam*<br/>
매개 변수 또는 플래그입니다.

*bFlag*<br/>
*PszParam* 가 매개 변수 인지 플래그 인지를 나타냅니다.

*트*<br/>
명령줄의 마지막 매개 변수 또는 플래그 인지 여부를 나타냅니다.

### <a name="remarks"></a>설명

[CWinApp::P arsecommandline](../../mfc/reference/cwinapp-class.md#parsecommandline) 는 `ParseParam` 명령줄에서 각 매개 변수 또는 플래그에 대해 한 번 호출 하 여 *pszParam* 에 인수를 전달 합니다. 매개 변수의 첫 번째 문자가 ' **-** ' 또는 ' **/** ' 이면 제거 되 고 *BFLAG* 가 TRUE로 설정 됩니다. 최종 매개 변수를 구문 분석할 때 *폭발* 은 TRUE로 설정 됩니다.

이 함수의 기본 구현에서는 `/p` `/pt` `/dde` `/Automation` `/Embedding` 다음 표에 표시 된 것 처럼,,, 및 플래그를 인식 합니다.

|명령줄 인수|명령이 실행 됨|
|----------------------------|----------------------|
|*app*|새 파일입니다.|
|*앱* 파일 이름|파일을 엽니다.|
|*앱* `/p` 이름도|파일을 기본 프린터로 인쇄 합니다.|
|*앱* `/pt` 파일 이름 프린터 드라이버 포트|지정 된 프린터에 파일을 인쇄 합니다.|
|*앱*`/dde`|DDE 명령을 시작 하 고 기다립니다.|
|*앱*`/Automation`|OLE 자동화 서버로 시작 합니다.|
|*앱*`/Embedding`|시작을 시작 하 여 포함 된 OLE 항목을 편집 합니다.|
|*앱*`/Register`<br /><br /> *앱*`/Regserver`|응용 프로그램에 등록 작업을 수행 하도록 알립니다.|
|*앱*`/Unregister`<br /><br /> *앱*`/Unregserver`|등록 취소 작업을 수행 하도록 응용 프로그램에 알립니다.|

이 정보는 [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded)및 [m_nShellCommand](#m_nshellcommand)에 저장 됩니다. 플래그는 슬래시 (' **/** ') 또는 하이픈 ' ' (으)로 표시 됩니다 **-** .

기본 구현은 플래그가 지정 되지 않은 첫 번째 매개 변수를 [m_strFileName](#m_strfilename)에 배치 합니다. 플래그의 경우 `/pt` 기본 구현은 두 번째, 세 번째 및 네 번째 플래그 이외의 매개 변수를 각각 [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)및 [m_strPortName](#m_strportname)에 배치 합니다.

또한 기본 구현은 새 파일의 경우에만 [m_bShowSplash](#m_bshowsplash) 을 TRUE로 설정 합니다. 새 파일의 경우 사용자는 응용 프로그램 자체와 관련 된 작업을 수행 했습니다. 셸을 사용 하 여 기존 파일을 여는 등의 다른 모든 경우에는 사용자 작업에 해당 파일이 직접 포함 됩니다. 문서 중심 관점에서 시작 화면은 응용 프로그램 시작을 알릴 필요가 없습니다.

파생 클래스에서이 함수를 재정의 하 여 다른 플래그와 매개 변수 값을 처리 합니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::P arseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::P rocessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

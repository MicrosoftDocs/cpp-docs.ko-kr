---
description: '자세히 알아보기: CTaskDialog 클래스'
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: 91cd3caec703f8e81116fccd75c0457abb69a3e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318587"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

메시지 상자처럼 작동하지만 사용자에게 추가 정보를 표시할 수 있는 팝업 대화 상자입니다. `CTaskDialog` 에는 사용자로부터 정보를 수집하는 기능을 포함합니다.

## <a name="syntax"></a>구문

```
class CTaskDialog : public CObject
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[CTaskDialog:: CTaskDialog](#ctaskdialog)|`CTaskDialog` 개체를 생성합니다.|

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[CTaskDialog:: AddCommandControl](#addcommandcontrol)|에 명령 단추 컨트롤을 추가 `CTaskDialog` 합니다.|
|[CTaskDialog:: AddRadioButton](#addradiobutton)|에 라디오 단추를 추가 `CTaskDialog` 합니다.|
|[CTaskDialog:: 클릭 Commandcontrol](#clickcommandcontrol)|명령 단추 컨트롤이 나 일반 단추를 프로그래밍 방식으로 클릭 합니다.|
|[CTaskDialog:: 클릭 Radiobutton](#clickradiobutton)|라디오 단추를 프로그래밍 방식으로 클릭 합니다.|
|[CTaskDialog::D oModal](#domodal)|`CTaskDialog`를 표시합니다.|
|[CTaskDialog:: GetCommonButtonCount](#getcommonbuttoncount)|사용할 수 있는 일반 단추 수를 검색 합니다.|
|[CTaskDialog:: GetCommonButtonFlag](#getcommonbuttonflag)|표준 Windows 단추를 클래스와 연결 된 일반 단추 형식으로 변환 합니다 `CTaskDialog` .|
|[CTaskDialog:: GetCommonButtonId](#getcommonbuttonid)|클래스와 연결 된 공통 단추 형식 중 하나 `CTaskDialog` 를 표준 Windows 단추로 변환 합니다.|
|[CTaskDialog:: GetOptions](#getoptions)|이에 대 한 옵션 플래그를 반환 합니다 `CTaskDialog` .|
|[CTaskDialog:: GetSelectedCommandControlID](#getselectedcommandcontrolid)|선택한 명령 단추 컨트롤을 반환 합니다.|
|[CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid)|선택 된 라디오 단추를 반환 합니다.|
|[CTaskDialog:: GetVerificationCheckboxState](#getverificationcheckboxstate)|확인 확인란의 상태를 검색 합니다.|
|[CTaskDialog:: IsCommandControlEnabled](#iscommandcontrolenabled)|명령 단추 컨트롤 또는 일반 단추를 사용할 수 있는지 여부를 결정 합니다.|
|[CTaskDialog:: IsRadioButtonEnabled](#isradiobuttonenabled)|라디오 단추를 사용할 수 있는지 여부를 확인 합니다.|
|[CTaskDialog:: IsSupported](#issupported)|응용 프로그램을 실행 하는 컴퓨터에서을 지원 하는지 여부를 확인 `CTaskDialog` 합니다.|
|[CTaskDialog:: LoadCommandControls](#loadcommandcontrols)|문자열 테이블의 데이터를 사용 하 여 명령 단추 컨트롤을 추가 합니다.|
|[CTaskDialog:: LoadRadioButtons](#loadradiobuttons)|문자열 테이블의 데이터를 사용 하 여 라디오 단추를 추가 합니다.|
|[CTaskDialog:: NavigateTo](#navigateto)|포커스를 다른로 이동 합니다 `CTaskDialog` .|
|[CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick)|사용자가 명령 단추 컨트롤을 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: OnCreate](#oncreate)|프레임 워크는를 만든 후이 메서드를 호출 합니다 `CTaskDialog` .|
|[CTaskDialog:: OnDestroy](#ondestroy)|프레임 워크는를 소멸 하기 바로 전에이 메서드를 호출 합니다 `CTaskDialog` .|
|[CTaskDialog:: OnExpandButtonClick](#onexpandbuttonclick)|사용자가 확장 단추를 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: OnHelp](#onhelp)|사용자가 도움말을 요청 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: Onhyperlink 클릭](#onhyperlinkclick)|사용자가 하이퍼링크를 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: OnInit](#oninit)|프레임 워크는가 초기화 될 때이 메서드를 호출 합니다 `CTaskDialog` .|
|[CTaskDialog:: OnNavigatePage](#onnavigatepage)|프레임 워크는 사용자가의 컨트롤과 관련 하 여 포커스를 이동할 때이 메서드를 호출 합니다 `CTaskDialog` .|
|[CTaskDialog:: OnRadioButtonClick](#onradiobuttonclick)|사용자가 라디오 단추 컨트롤을 선택 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: OnTimer](#ontimer)|프레임 워크는 타이머가 만료 될 때이 메서드를 호출 합니다.|
|[CTaskDialog:: OnVerificationCheckboxClick](#onverificationcheckboxclick)|사용자가 확인 확인란을 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.|
|[CTaskDialog:: RemoveAllCommandControls](#removeallcommandcontrols)|에서 모든 명령 컨트롤을 제거 합니다 `CTaskDialog` .|
|[CTaskDialog:: RemoveAllRadioButtons](#removeallradiobuttons)|에서 라디오 단추를 모두 제거 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetCommandControlOptions](#setcommandcontroloptions)|에서 명령 단추 컨트롤을 업데이트 `CTaskDialog` 합니다.|
|[CTaskDialog:: SetCommonButtonOptions](#setcommonbuttonoptions)|사용할 수 있는 공용 단추의 하위 집합을 업데이트 하 고 UAC 권한 상승이 필요 합니다.|
|[CTaskDialog:: SetCommonButtons](#setcommonbuttons)|에 일반 단추를 추가 `CTaskDialog` 합니다.|
|[CTaskDialog:: SetContent](#setcontent)|의 콘텐츠를 업데이트 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetDefaultCommandControl](#setdefaultcommandcontrol)|기본 명령 단추 컨트롤을 지정 합니다.|
|[CTaskDialog:: SetDefaultRadioButton](#setdefaultradiobutton)|기본 라디오 단추를 지정 합니다.|
|[CTaskDialog:: SetDialogWidth](#setdialogwidth)|의 너비를 조정 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetExpansionArea](#setexpansionarea)|의 확장 영역을 업데이트 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetFooterIcon](#setfootericon)|의 바닥글 아이콘을 업데이트 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetFooterText](#setfootertext)|의 바닥글에 있는 텍스트를 업데이트 `CTaskDialog` 합니다.|
|[CTaskDialog:: SetMainIcon](#setmainicon)|의 주 아이콘을 업데이트 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetMainInstruction](#setmaininstruction)|의 주 명령을 업데이트 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetOptions](#setoptions)|에 대 한 옵션을 구성 `CTaskDialog` 합니다.|
|[CTaskDialog:: SetProgressBarMarquee](#setprogressbarmarquee)|의 움직이는 텍스트 막대를 구성 하 `CTaskDialog` 고 대화 상자에 추가 합니다.|
|[CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)|진행률 표시줄의 위치를 조정 합니다.|
|[CTaskDialog:: SetProgressBarRange](#setprogressbarrange)|진행률 표시줄의 범위를 조정 합니다.|
|[CTaskDialog:: SetProgressBarState](#setprogressbarstate)|진행률 표시줄의 상태를 설정 하 고에 표시 합니다 `CTaskDialog` .|
|[CTaskDialog:: SetRadioButtonOptions](#setradiobuttonoptions)|라디오 단추를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CTaskDialog:: SetVerificationCheckbox](#setverificationcheckbox)|확인 확인란의 선택 상태를 설정 합니다.|
|[CTaskDialog:: SetVerificationCheckboxText](#setverificationcheckboxtext)|확인 확인란의 오른쪽에 있는 텍스트를 설정 합니다.|
|[CTaskDialog:: SetWindowTitle](#setwindowtitle)|의 제목을 설정 합니다 `CTaskDialog` .|
|[CTaskDialog:: ShowDialog](#showdialog)|을 만들어 표시 `CTaskDialog` 합니다.|
|[CTaskDialog:: TaskDialogCallback](#taskdialogcallback)|프레임 워크는 다양 한 Windows 메시지에 대 한 응답으로이를 호출 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|`m_aButtons`|에 대 한 명령 단추 컨트롤의 배열입니다 `CTaskDialog` .|
|`m_aRadioButtons`|에 대 한 라디오 단추 컨트롤의 배열입니다 `CTaskDialog` .|
|`m_bVerified`|`TRUE` 확인 확인란을 선택 했음을 나타냅니다. `FALSE` 는 그렇지 않음을 나타냅니다.|
|`m_footerIcon`|의 바닥글에 있는 아이콘 `CTaskDialog` 입니다.|
|`m_hWnd`|의 창에 대 한 핸들 `CTaskDialog` 입니다.|
|`m_mainIcon`|의 주 아이콘입니다 `CTaskDialog` .|
|`m_nButtonDisabled`|사용할 수 없는 일반 단추를 나타내는 마스크입니다.|
|`m_nButtonElevation`|UAC 권한 상승이 필요한 일반 단추를 나타내는 마스크입니다.|
|`m_nButtonId`|선택한 명령 단추 컨트롤의 ID입니다.|
|`m_nCommonButton`|에 표시 되는 일반적인 단추를 나타내는 마스크입니다 `CTaskDialog` .|
|`m_nDefaultCommandControl`|이 표시 될 때 선택 되는 명령 단추 컨트롤의 ID입니다 `CTaskDialog` .|
|`m_nDefaultRadioButton`|이 표시 될 때 선택 되는 라디오 단추 컨트롤의 ID입니다 `CTaskDialog` .|
|`m_nFlags`|에 대 한 옵션을 나타내는 마스크입니다 `CTaskDialog` .|
|`m_nProgressPos`|진행률 표시줄의 현재 위치입니다.  이 값은 `m_nProgressRangeMin`와 `m_nProgressRangeMax` 사이의 값이어야 합니다.|
|`m_nProgressRangeMax`|진행률 표시줄의 최대값입니다.|
|`m_nProgressRangeMin`|진행률 표시줄의 최소값입니다.|
|`m_nProgressState`|진행률 표시줄의 상태입니다. 자세한 내용은 [Ctaskdialog:: SetProgressBarState](#setprogressbarstate)를 참조 하세요.|
|`m_nRadioId`|선택 된 라디오 단추 컨트롤의 ID입니다.|
|`m_nWidth`|`CTaskDialog`의 너비(픽셀)입니다.|
|`m_strCollapse`|`CTaskDialog`확장 된 정보를 숨길 때 확장 상자 오른쪽에 표시 되는 문자열입니다.|
|`m_strContent`|의 콘텐츠 문자열입니다 `CTaskDialog` .|
|`m_strExpand`|`CTaskDialog`확장 된 정보가 표시 될 때 확장 상자 오른쪽에 표시 되는 문자열입니다.|
|`m_strFooter`|의 바닥글 `CTaskDialog` 입니다.|
|`m_strInformation`|에 대 한 확장 된 정보 `CTaskDialog` 입니다.|
|`m_strMainInstruction`|의 기본 명령 `CTaskDialog` 입니다.|
|`m_strTitle`|`CTaskDialog`의 제목입니다.|
|`m_strVerification`|가 `CTaskDialog` 확인 확인란의 오른쪽에 표시 하는 문자열입니다.|

## <a name="remarks"></a>설명

`CTaskDialog`클래스는 표준 Windows 메시지 상자를 대체 하며 사용자 로부터 정보를 수집 하는 새 컨트롤과 같은 추가 기능을 포함 합니다. 이 클래스는 Visual Studio 2010 이상 버전의 MFC 라이브러리에 있습니다. 는 `CTaskDialog` Windows Vista부터 사용할 수 있습니다. 이전 버전의 Windows에서는 개체를 표시할 수 없습니다 `CTaskDialog` . `CTaskDialog::IsSupported`현재 사용자가 작업 대화 상자를 표시할 수 있는지 여부를 런타임에 확인 하는 데 사용 합니다. 표준 Windows 메시지 상자는 계속 지원 됩니다.

는 `CTaskDialog` 유니코드 라이브러리를 사용 하 여 응용 프로그램을 빌드하는 경우에만 사용할 수 있습니다.

에는 `CTaskDialog` 두 개의 다른 생성자가 있습니다. 한 생성자를 사용 하 여 두 개의 명령 단추와 최대 6 개의 일반 단추 컨트롤을 지정할 수 있습니다. 을 만든 후 명령 단추를 더 추가할 수 있습니다 `CTaskDialog` . 두 번째 생성자는 명령 단추를 지원 하지 않지만, 일반 단추 컨트롤을 무제한으로 추가할 수 있습니다. 생성자에 대 한 자세한 내용은 [ctaskdialog:: CTaskDialog](#ctaskdialog)를 참조 하십시오.

다음 그림에서는 `CTaskDialog` 일부 컨트롤의 위치를 보여 주는 샘플을 보여 줍니다.

![CTaskDialog의 예](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog의 예") <br/>
CTaskDialog 샘플

## <a name="requirements"></a>요구 사항

**필요한 최소 운영 체제:** Windows Vista

**헤더:** afxtaskdialog

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a> CTaskDialog:: AddCommandControl

에 새 명령 단추 컨트롤을 추가 `CTaskDialog` 합니다.

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 명령 컨트롤 id 번호입니다.

*strCaption*<br/>
진행 `CTaskDialog` 가 사용자에 게 표시 하는 문자열입니다. 이 문자열을 사용 하 여 명령의 용도를 설명 합니다.

*bEnabled*<br/>
진행 새 단추를 사용할 수 있는지 여부를 나타내는 부울 매개 변수입니다.

*bRequiresElevation*<br/>
진행 명령에 권한 상승이 필요한 지 여부를 나타내는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

에는 `CTaskDialog Class` 무제한 개수의 명령 단추 컨트롤이 표시 될 수 있습니다. 그러나가 `CTaskDialog` 명령 단추 컨트롤을 표시 하는 경우 최대 6 개의 단추를 표시할 수 있습니다. 에 `CTaskDialog` 명령 단추 컨트롤이 없으면 개수에 제한 없이 단추를 표시할 수 있습니다.

사용자가 명령 단추 컨트롤을 선택 하면이 `CTaskDialog` 닫힙니다. 응용 프로그램에서 [Ctaskdialog::D oModal](#domodal)을 사용 하 여 대화 상자를 표시 하는 경우 `DoModal` 선택한 명령 단추 컨트롤의 *ncommandcontrolid* 를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a> CTaskDialog:: AddRadioButton

에 라디오 단추를 추가 `CTaskDialog` 합니다.

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 라디오 단추의 id 번호입니다.

*strCaption*<br/>
진행 가 `CTaskDialog` 라디오 단추 옆에 표시 하는 문자열입니다.

*bEnabled*<br/>
진행 라디오 단추를 사용할 수 있는지 여부를 나타내는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

[Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md) 의 라디오 단추를 사용 하 여 사용자 로부터 정보를 수집할 수 있습니다. [Ctaskdialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid) 함수를 사용 하 여 선택한 라디오 단추를 확인 합니다.

에서는 `CTaskDialog` *nRadioButtonID* 매개 변수가 각 라디오 단추에 대해 고유할 필요가 없습니다. 그러나 각 라디오 단추에 대해 고유한 식별자를 사용 하지 않으면 예기치 않은 동작이 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a> CTaskDialog:: 클릭 Commandcontrol

명령 단추 컨트롤이 나 일반 단추를 프로그래밍 방식으로 클릭 합니다.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 클릭할 컨트롤의 명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 windows 메시지 TDM_CLICK_BUTTON를 생성 합니다.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a> CTaskDialog:: 클릭 Radiobutton

라디오 단추를 프로그래밍 방식으로 클릭 합니다.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 클릭할 라디오 단추의 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 windows 메시지 TDM_CLICK_RADIO_BUTTON를 생성 합니다.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a> CTaskDialog:: CTaskDialog

[Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)의 인스턴스를 만듭니다.

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>매개 변수

*strContent*<br/>
진행 의 내용에 사용할 문자열 `CTaskDialog` 입니다.

*strMainInstruction*<br/>
진행 의 기본 명령 `CTaskDialog` 입니다.

*strTitle*<br/>
진행 의 제목 `CTaskDialog` 입니다.

*nCommonButtons*<br/>
진행 에 추가할 공용 단추의 마스크입니다 `CTaskDialog` .

*nTaskDialogOptions*<br/>
진행 에 사용할 옵션 집합입니다 `CTaskDialog` .

*strFooter*<br/>
진행 바닥글로 사용할 문자열입니다.

*nIDCommandControlsFirst*<br/>
진행 첫 번째 명령의 문자열 ID입니다.

*nIDCommandControlsLast*<br/>
진행 마지막 명령의 문자열 ID입니다.

### <a name="remarks"></a>설명

를 응용 프로그램에 추가 하는 방법에는 두 가지가 있습니다 `CTaskDialog` . 첫 번째 방법은 생성자 중 하나를 사용 하 여를 만들고 `CTaskDialog` [Ctaskdialog::D omodal](#domodal)을 사용 하 여 표시 하는 것입니다. 두 번째 방법은 정적 함수 [Ctaskdialog:: ShowDialog](#showdialog)를 사용 하는 것입니다 .이 함수를 사용 하면 `CTaskDialog` 개체를 명시적으로 만들지 않고도를 표시할 수 있습니다 `CTaskDialog` .

두 번째 생성자는 응용 프로그램의 리소스 파일에 있는 데이터를 사용 하 여 명령 단추 컨트롤을 만듭니다. 리소스 파일의 문자열 테이블에는 문자열 Id가 연결 된 여러 문자열이 있습니다. 이 메서드는 *nIDCommandControlsFirst* 과 *nCommandControlsLast* 사이에 있는 문자열 테이블의 유효한 각 항목에 대 한 명령 단추 컨트롤을 추가 합니다. 이러한 명령 단추 컨트롤의 경우 문자열 테이블의 문자열은 컨트롤의 캡션입니다. 문자열 ID는 컨트롤의 ID입니다.

유효한 옵션 목록은 [Ctaskdialog:: SetOptions](#setoptions) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a> CTaskDialog::D oModal

를 표시 `CTaskDialog` 하 고 모달로 만듭니다.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>매개 변수

*hParent*<br/>
진행 의 부모 창 `CTaskDialog` 입니다.

### <a name="return-value"></a>반환 값

사용자가 선택한 항목에 해당 하는 정수입니다.

### <a name="remarks"></a>설명

[Ctaskdialog](../../mfc/reference/ctaskdialog-class.md)의이 인스턴스를 표시 합니다. 그런 다음 응용 프로그램은 사용자가 대화 상자를 닫을 때까지 기다립니다.

는 `CTaskDialog` 사용자가 일반 단추 또는 명령 링크 컨트롤을 선택 하거나를 닫을 때 닫힙니다 `CTaskDialog` . 반환 값은 사용자가 대화 상자를 닫은 방법을 나타내는 식별자입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a> CTaskDialog:: GetCommonButtonCount

공용 단추 수를 검색 합니다.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>반환 값

사용할 수 있는 일반 단추 수입니다.

### <a name="remarks"></a>설명

공용 단추는 [ctaskdialog:: ctaskdialog](#ctaskdialog)에 제공 하는 기본 단추입니다. [Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md) 는 대화 상자 아래쪽의 단추를 표시 합니다.

열거 되는 단추의 목록에는 Ctrl. h가 제공 됩니다.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a> CTaskDialog:: GetCommonButtonFlag

표준 Windows 단추를 [Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)와 연결 된 일반 단추 형식으로 변환 합니다.

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>매개 변수

*nButtonId*<br/>
진행 표준 Windows 단추 값입니다.

### <a name="return-value"></a>반환 값

해당 하는 `CTaskDialog` 공용 단추의 값입니다. 해당 하는 공통 단추가 없으면이 메서드는 0을 반환 합니다.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a> CTaskDialog:: GetCommonButtonId

[Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md) 와 연결 된 공통 단추 형식 중 하나를 표준 Windows 단추로 변환 합니다.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>매개 변수

*nFlag*<br/>
진행 클래스와 연결 된 공용 단추 형식 `CTaskDialog` 입니다.

### <a name="return-value"></a>반환 값

해당 표준 Windows 단추의 값입니다. 해당 하는 Windows 단추가 없으면 메서드는 0을 반환 합니다.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a> CTaskDialog:: GetOptions

이에 대 한 옵션 플래그를 반환 합니다 `CTaskDialog` .

```
int GetOptions() const;
```

### <a name="return-value"></a>반환 값

에 대 한 플래그 `CTaskDialog` 입니다.

### <a name="remarks"></a>설명

[Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)에 사용할 수 있는 옵션에 대 한 자세한 내용은 [Ctaskdialog:: SetOptions](#setoptions)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a> CTaskDialog:: GetSelectedCommandControlID

선택한 명령 단추 컨트롤을 반환 합니다.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>반환 값

현재 선택 된 명령 단추 컨트롤의 ID입니다.

### <a name="remarks"></a>설명

사용자가 선택한 명령 단추의 ID를 검색 하기 위해이 메서드를 사용할 필요는 없습니다. 이 ID는 [Ctaskdialog::D oModal](#domodal) 또는 [Ctaskdialog:: ShowDialog](#showdialog)에서 반환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a> CTaskDialog:: GetSelectedRadioButtonID

선택 된 라디오 단추를 반환 합니다.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>반환 값

선택 된 라디오 단추의 ID입니다.

### <a name="remarks"></a>설명

사용자가 대화 상자를 닫은 후이 메서드를 사용 하 여 선택한 라디오 단추를 검색할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a> CTaskDialog:: GetVerificationCheckboxState

확인 확인란의 상태를 검색 합니다.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>반환 값

확인란이 선택 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a> CTaskDialog:: IsCommandControlEnabled

명령 단추 컨트롤이 나 단추를 사용할 수 있는지 여부를 확인 합니다.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 테스트할 명령 단추 컨트롤 또는 단추의 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤을 사용할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 두 명령 단추 컨트롤과 * 클래스의 공통 단추를 모두 사용할 수 있는지 확인할 수 있습니다 `CTaskDialog` .

*Ncommandcontrolid* 가 일반 단추나 명령 단추 컨트롤에 대 한 유효한 식별자가 아닌 경우 `CTaskDialog` 이 메서드는 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a> CTaskDialog:: IsRadioButtonEnabled

라디오 단추를 사용할 수 있는지 여부를 확인 합니다.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 테스트할 라디오 단추의 ID입니다.

### <a name="return-value"></a>반환 값

라디오 단추가 사용 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*NRadioButtonID* 가 라디오 단추에 대 한 유효한 식별자가 아닌 경우이 메서드는 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a> CTaskDialog:: IsSupported

응용 프로그램을 실행 하는 컴퓨터에서을 지원 하는지 여부를 확인 `CTaskDialog` 합니다.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>반환 값

컴퓨터에서를 지원 하면 TRUE `CTaskDialog` 이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

응용 프로그램을 실행 하는 컴퓨터에서 클래스를 지 원하는 경우이 함수를 사용 하 여 런타임에 확인 `CTaskDialog` 합니다. 컴퓨터에서를 지원 하지 않는 경우 `CTaskDialog` 사용자에 게 정보를 전달 하는 다른 방법을 제공 해야 합니다. `CTaskDialog`클래스를 지원 하지 않는 컴퓨터에서를 사용 하려고 하면 응용 프로그램의 작동이 중단 됩니다 `CTaskDialog` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a> CTaskDialog:: LoadCommandControls

문자열 테이블의 데이터를 사용 하 여 명령 단추 컨트롤을 추가 합니다.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>매개 변수

*nIDCommandControlsFirst*<br/>
진행 첫 번째 명령의 문자열 ID입니다.

*nIDCommandControlsLast*<br/>
진행 마지막 명령의 문자열 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 응용 프로그램의 리소스 파일에 있는 데이터를 사용 하 여 명령 단추 컨트롤을 만듭니다. 리소스 파일의 문자열 테이블에는 문자열 Id가 연결 된 여러 문자열이 있습니다. 이 메서드를 사용 하 여 추가 된 새 명령 단추 컨트롤은 컨트롤의 캡션에 대 한 문자열 및 컨트롤 ID의 문자열 ID를 사용 합니다. 선택한 문자열 범위는 *nIDCommandControlsFirst* 및 *nCommandControlsLast*(포함)에 의해 제공 됩니다. 범위에 빈 항목이 있는 경우 메서드는 해당 항목에 대 한 명령 단추 컨트롤을 추가 하지 않습니다.

기본적으로 새 명령 단추 컨트롤이 활성화 되며 권한 상승이 필요 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a> CTaskDialog:: LoadRadioButtons

문자열 테이블의 데이터를 사용 하 여 라디오 단추 컨트롤을 추가 합니다.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>매개 변수

*nIDRadioButtonsFirst*<br/>
진행 첫 번째 라디오 단추의 문자열 ID입니다.

*nIDRadioButtonsLast*<br/>
진행 마지막 라디오 단추의 문자열 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 응용 프로그램의 리소스 파일에 있는 데이터를 사용 하 여 라디오 단추를 만듭니다. 리소스 파일의 문자열 테이블에는 문자열 Id가 연결 된 여러 문자열이 있습니다. 이 메서드를 사용 하 여 추가 된 새 라디오 단추는 라디오 단추 캡션에 문자열을 사용 하 고 라디오 단추의 ID에 문자열 ID를 사용 합니다. 선택한 문자열 범위는 *nIDRadioButtonsFirst* 및 *nRadioButtonsLast*(포함)에 의해 제공 됩니다. 범위에 빈 항목이 있는 경우 메서드는 해당 항목에 대 한 라디오 단추를 추가 하지 않습니다.

기본적으로 새 라디오 단추를 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a> CTaskDialog:: NavigateTo

포커스를 다른로 이동 합니다 `CTaskDialog` .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>매개 변수

*oTaskDialog*<br/>
진행 `CTaskDialog` 포커스를 받는입니다.

### <a name="remarks"></a>설명

이 메서드는 `CTaskDialog` *Otaskdialog* 가 표시 될 때 현재를 숨깁니다. *Otaskdialog* 는 현재와 동일한 위치에 표시 됩니다 `CTaskDialog` .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a> CTaskDialog:: OnCommandControlClick

사용자가 명령 단추 컨트롤을 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 사용자가 선택한 명령 단추 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a> CTaskDialog:: OnCreate

프레임 워크는를 만든 후이 메서드를 호출 합니다 `CTaskDialog` .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a> CTaskDialog:: OnDestroy

프레임 워크는를 소멸 하기 바로 전에이 메서드를 호출 합니다 `CTaskDialog` .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a> CTaskDialog:: OnExpandButtonClick

사용자가 확장 단추를 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>매개 변수

*bExpanded 됨*<br/>
진행 0이 아닌 값은 추가 정보가 표시 됨을 나타냅니다. 0은 추가 정보가 숨겨져 있음을 나타냅니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a> CTaskDialog:: OnHelp

사용자가 도움말을 요청 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a> CTaskDialog:: Onhyperlink 클릭

사용자가 하이퍼링크를 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>매개 변수

*strHref*<br/>
진행 하이퍼링크를 나타내는 문자열입니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 S_OK를 반환 하기 전에 [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) 를 호출 합니다.

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a> CTaskDialog:: OnInit

프레임 워크는가 초기화 될 때이 메서드를 호출 합니다 `CTaskDialog` .

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a> CTaskDialog:: OnNavigatePage

프레임 워크는 [Ctaskdialog:: NavigateTo](#navigateto) 메서드에 대 한 응답으로이 메서드를 호출 합니다.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a> CTaskDialog:: OnRadioButtonClick

사용자가 라디오 단추 컨트롤을 선택 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 사용자가 클릭 한 라디오 단추 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a> CTaskDialog:: OnTimer

프레임 워크는 타이머가 만료 될 때이 메서드를 호출 합니다.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>매개 변수

*lTime*<br/>
진행 가 만들어지거나 타이머가 다시 설정 된 이후의 시간 (밀리초) `CTaskDialog` 입니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a> CTaskDialog:: OnVerificationCheckboxClick

사용자가 확인 확인란을 클릭 하면 프레임 워크에서이 메서드를 호출 합니다.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>매개 변수

*bChecked*<br/>
진행 TRUE는 확인 확인란을 선택 했음을 나타냅니다. FALSE는 그렇지 않음을 나타냅니다.

### <a name="return-value"></a>반환 값

기본 구현에서는 S_OK을 반환 합니다.

### <a name="remarks"></a>설명

사용자 지정 동작을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a> CTaskDialog:: RemoveAllCommandControls

에서 모든 명령 단추 컨트롤을 제거 합니다 `CTaskDialog` .

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a> CTaskDialog:: RemoveAllRadioButtons

에서 라디오 단추를 모두 제거 합니다 `CTaskDialog` .

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a> CTaskDialog:: SetCommandControlOptions

에서 명령 단추 컨트롤을 업데이트 `CTaskDialog` 합니다.

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 업데이트할 명령 컨트롤의 ID입니다.

*bEnabled*<br/>
진행 지정 된 명령 단추 컨트롤을 사용할 수 있는지 여부를 나타내는 부울 매개 변수입니다.

*bRequiresElevation*<br/>
진행 지정 된 명령 단추 컨트롤에 권한 상승이 필요한 지 여부를 나타내는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 명령 단추 컨트롤이 활성화 되는지 여부를 변경 하거나 클래스에 추가 된 후에 권한 상승이 필요한 지 여부를 변경할 수 `CTaskDialog` 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a> CTaskDialog:: SetCommonButtonOptions

사용할 수 있는 공용 단추의 하위 집합을 업데이트 하 고 UAC 권한 상승을 요구 합니다.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>매개 변수

*nDisabledButtonMask*<br/>
진행 비활성화 하는 일반 단추에 대 한 마스크입니다.

*nElevationButtonMask*<br/>
진행 권한 상승이 필요한 일반 단추에 대 한 마스크입니다.

### <a name="remarks"></a>설명

Ctaskdialog [:: ctaskdialog](#ctaskdialog) 생성자와 [Ctaskdialog:: SetCommonButtons](#setcommonbuttons)메서드를 사용 하 여 [ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md) 의 인스턴스에 사용할 수 있는 공용 단추를 설정할 수 있습니다. `CTaskDialog::SetCommonButtonOptions` 는 새로운 일반 단추를 추가 하는 기능을 지원 하지 않습니다.

이 메서드를 사용 하 여이에 사용할 수 없는 일반 단추를 사용 하거나 사용 하지 않도록 설정 하는 경우 `CTaskDialog` 이 메서드는 [확인](diagnostic-services.md#ensure) 매크로를 사용 하 여 예외를 throw 합니다.

이 메서드는에 사용할 수 있지만 이전에는 `CTaskDialog` 사용 하지 않도록 설정 했더라도 *nDisabledButtonMask* 에 없는 모든 단추를 사용 하도록 설정 합니다. 이 메서드는 비슷한 방식으로 권한 상승을 처리 합니다. 공용 단추를 사용할 수 있지만 *nElevationButtonMask* 에 포함 되지 않은 경우에는 권한 상승이 필요 하지 않은 일반 단추를 기록 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a> CTaskDialog:: SetCommonButtons

에 일반 단추를 추가 `CTaskDialog` 합니다.

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>매개 변수

*nButtonMask*<br/>
진행 에 추가할 단추의 마스크입니다 `CTaskDialog` .

*nDisabledButtonMask*<br/>
진행 사용 하지 않을 단추의 마스크입니다.

*nElevationButtonMask*<br/>
진행 권한 상승이 필요한 단추의 마스크입니다.

### <a name="remarks"></a>설명

클래스의이 인스턴스에 대 한 표시 창이 생성 된 후에는이 메서드를 호출할 수 없습니다 `CTaskDialog` . 이렇게 하면이 메서드는 예외를 throw 합니다.

*Nbuttonmask* 로 표시 되는 단추는 이전에에 추가 된 모든 공통 단추를 재정의 합니다 `CTaskDialog` . *Nbuttonmask* 에 표시 된 단추만 사용할 수 있습니다.

*NDisabledButtonMask* 또는 *NElevationButtonMask* 에 *nbuttonmask* 에 없는 단추가 포함 된 경우이 메서드는 [확인](diagnostic-services.md#ensure) 매크로를 사용 하 여 예외를 throw 합니다.

기본적으로 모든 일반 단추가 활성화 되며 권한 상승이 필요 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a> CTaskDialog:: SetContent

의 콘텐츠를 업데이트 합니다 `CTaskDialog` .

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>매개 변수

*strContent*<br/>
진행 사용자에 게 표시할 문자열입니다.

### <a name="remarks"></a>설명

클래스의 내용은 `CTaskDialog` 대화 상자의 주 섹션에서 사용자에 게 표시 되는 텍스트입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a> CTaskDialog:: SetDefaultCommandControl

기본 명령 단추 컨트롤을 지정 합니다.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>매개 변수

*nCommandControlID*<br/>
진행 기본값으로 사용할 명령 단추 컨트롤의 ID입니다.

### <a name="remarks"></a>설명

기본 명령 단추 컨트롤은가 `CTaskDialog` 사용자에 게 처음 표시 될 때 선택 되는 컨트롤입니다.

이 메서드는 *Ncommandcontrolid* 로 지정 된 명령 단추 컨트롤을 찾을 수 없는 경우 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a> CTaskDialog:: SetDefaultRadioButton

기본 라디오 단추를 지정 합니다.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 기본값으로 사용할 라디오 단추의 ID입니다.

### <a name="remarks"></a>설명

기본 라디오 단추는가 `CTaskDialog` 사용자에 게 처음 표시 될 때 선택 되는 단추입니다.

*NRadioButtonID* 로 지정 된 라디오 단추를 찾을 수 없는 경우이 메서드는 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a> CTaskDialog:: SetDialogWidth

의 너비를 조정 합니다 `CTaskDialog` .

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>매개 변수

*nWidth*<br/>
진행 대화 상자의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

매개 변수 *Nwidth* 는 0 보다 크거나 같아야 합니다. 그렇지 않으면이 메서드는 예외를 throw 합니다.

*Nwidth* 가 0으로 설정 된 경우이 메서드는 대화 상자를 기본 크기로 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a> CTaskDialog:: SetExpansionArea

의 확장 영역을 업데이트 합니다 `CTaskDialog` .

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>매개 변수

*strExpandedInformation 정보*<br/>
진행 `CTaskDialog` 사용자가 확장 단추를 클릭할 때가 대화 상자의 본문에 표시 하는 문자열입니다.

*strCollapsedLabel*<br/>
진행 `CTaskDialog` 확장 된 영역이 축소 될 때 확장 단추 옆에가 표시 하는 문자열입니다.

*strExpandedLabel 레이블*<br/>
진행 `CTaskDialog` 확장 된 영역이 표시 될 때가 확장 단추 옆에 표시 하는 문자열입니다.

### <a name="remarks"></a>설명

클래스의 확장 영역을 `CTaskDialog` 사용 하면 사용자에 게 추가 정보를 제공할 수 있습니다. 확장 영역은의 주 부분에 있으며 `CTaskDialog` 제목 및 콘텐츠 문자열 바로 아래에 있습니다.

`CTaskDialog`가 처음 표시 될 때 확장 된 정보를 표시 하지 않고 `strCollapsedLabel` 확장 단추 옆에 배치 합니다. 사용자가 확장 단추를 클릭 하면에서 `CTaskDialog` *strex놓을* 수 있는 정보를 표시 하 고 레이블을 *strexancached 레이블로* 변경 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a> CTaskDialog:: SetFooterIcon

의 바닥글 아이콘을 업데이트 합니다 `CTaskDialog` .

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>매개 변수

*hFooterIcon*<br/>
진행 의 새 아이콘 `CTaskDialog` 입니다.

*lpszFooterIcon*<br/>
진행 의 새 아이콘 `CTaskDialog` 입니다.

### <a name="remarks"></a>설명

[Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)의 아래쪽에 바닥글 아이콘이 표시 됩니다. 연결 된 바닥글 텍스트가 있을 수 있습니다. [Ctaskdialog:: SetFooterText](#setfootertext)를 사용 하 여 바닥글 텍스트를 변경할 수 있습니다.

이 메서드는 [](diagnostic-services.md#ensure) `CTaskDialog` 가 표시 되거나 입력 매개 변수가 NULL 일 경우 확인 매크로를 사용 하 여 예외를 throw 합니다.

는 `CTaskDialog` `HICON` 또는 바닥글 아이콘 으로만 사용할 수 있습니다 `LPCWSTR` . 생성자 또는 [Ctaskdialog:: SetOptions](#setoptions)에서 옵션 TDF_USE_HICON_FOOTER 설정 하 여 구성 합니다. 기본적으로는 `CTaskDialog` `LPCWSTR` 바닥글 아이콘의 입력 형식으로 사용 하도록 구성 됩니다. 이 메서드는 부적절 한 유형을 사용 하 여 아이콘을 설정 하려고 하면 예외를 발생 시킵니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a> CTaskDialog:: SetFooterText

의 바닥글에 있는 텍스트를 업데이트 `CTaskDialog` 합니다.

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>매개 변수

*strFooterText*<br/>
진행 바닥글의 새 텍스트입니다.

### <a name="remarks"></a>설명

바닥글 아이콘이 아래쪽에 있는 바닥글 텍스트 옆에 표시 됩니다 `CTaskDialog` . [Ctaskdialog:: SetFooterIcon](#setfootericon)를 사용 하 여 바닥글 아이콘을 변경할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a> CTaskDialog:: SetMainIcon

의 주 아이콘을 업데이트 합니다 `CTaskDialog` .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>매개 변수

*hMainIcon*<br/>
진행 새 아이콘입니다.

*lpszMainIcon*<br/>
진행 새 아이콘입니다.

### <a name="remarks"></a>설명

이 메서드는 [](diagnostic-services.md#ensure) `CTaskDialog` 가 표시 되거나 입력 매개 변수가 NULL 일 경우 확인 매크로를 사용 하 여 예외를 throw 합니다.

는 `CTaskDialog` 또는를 주 아이콘 으로만 수락할 수 있습니다 `HICON` `LPCWSTR` . 생성자 또는 [Ctaskdialog:: SetOptions](#setoptions) 메서드에서 TDF_USE_HICON_MAIN 옵션을 설정 하 여이를 구성할 수 있습니다. 기본적으로는 `CTaskDialog` `LPCWSTR` 주 아이콘의 입력 형식으로 사용 하도록 구성 됩니다. 이 메서드는 부적절 한 유형을 사용 하 여 아이콘을 설정 하려고 하면 예외를 발생 시킵니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a> CTaskDialog:: SetMainInstruction

의 주 명령을 업데이트 합니다 `CTaskDialog` .

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>매개 변수

*strInstructions*<br/>
진행 새 주 명령입니다.

### <a name="remarks"></a>설명

클래스의 기본 명령은 `CTaskDialog` 사용자에 게 굵은 굵은 글꼴로 표시 되는 텍스트입니다. 이 대화 상자는 제목 표시줄 아래의 대화 상자에 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a> CTaskDialog:: SetOptions

에 대 한 옵션을 구성 `CTaskDialog` 합니다.

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>매개 변수

*nOptionFlag*<br/>
진행 에 사용할 플래그 집합입니다 `CTaskDialog` .

### <a name="remarks"></a>설명

이 메서드는에 대 한 현재 옵션을 모두 지웁니다 `CTaskDialog` . 현재 옵션을 유지 하려면 먼저 [Ctaskdialog:: GetOptions](#getoptions) 를 사용 하 여 해당 옵션을 검색 하 고 설정 하려는 옵션과 결합 해야 합니다.

다음 표에서는 모든 유효한 옵션을 보여 줍니다.

|Name|설명|
|-|-|
|TDF_ENABLE_HYPERLINKS|에서 하이퍼링크를 사용 하도록 설정 `CTaskDialog` 합니다.|
|TDF_USE_HICON_MAIN|`CTaskDialog`주 아이콘에를 사용 하도록를 구성 합니다 `HICON` . 대안은를 사용 하는 것입니다 `LPCWSTR` .|
|TDF_USE_HICON_FOOTER|`CTaskDialog`바닥글 아이콘에를 사용 하도록를 구성 합니다 `HICON` . 대안은를 사용 하는 것입니다 `LPCWSTR` .|
|TDF_ALLOW_DIALOG_CANCELLATION|`CTaskDialog` **취소** 단추를 사용할 수 없는 경우에도 사용자가 키보드를 사용 하거나 대화 상자의 오른쪽 위 모퉁이에 있는 아이콘을 사용 하 여를 닫을 수 있습니다. 이 플래그를 설정 하지 않고 **취소** 단추를 사용할 수 없는 경우 사용자는 Alt + F4, esc 키 또는 제목 표시줄의 닫기 단추를 사용 하 여 대화 상자를 닫을 수 없습니다.|
|TDF_USE_COMMAND_LINKS|`CTaskDialog`명령 단추 컨트롤을 사용 하도록를 구성 합니다.|
|TDF_USE_COMMAND_LINKS_NO_ICON|`CTaskDialog`컨트롤 옆에 아이콘을 표시 하지 않고 명령 단추 컨트롤을 사용 하도록를 구성 합니다. TDF_USE_COMMAND_LINKS TDF_USE_COMMAND_LINKS_NO_ICON를 재정의 합니다.|
|TDF_EXPAND_FOOTER_AREA|확장 영역이 현재 확장 되었음을 나타냅니다.|
|TDF_EXPANDED_BY_DEFAULT|확장 영역이 기본적으로 확장 되는지 여부를 결정 합니다.|
|TDF_VERIFICATION_FLAG_CHECKED|확인 확인란이 현재 선택 되어 있음을 나타냅니다.|
|TDF_SHOW_PROGRESS_BAR|`CTaskDialog`진행률 표시줄을 표시 하도록를 구성 합니다.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|진행률 표시줄을 움직이는 진행률 막대로 구성 합니다. 이 옵션을 사용 하도록 설정 하는 경우 예상 되는 동작을 포함 하도록 TDF_SHOW_PROGRESS_BAR 설정 해야 합니다.|
|TDF_CALLBACK_TIMER|`CTaskDialog`콜백 간격이 약 200 밀리초로 설정 되어 있음을 나타냅니다.|
|TDF_POSITION_RELATIVE_TO_WINDOW|`CTaskDialog`부모 창에 상대적으로 가운데 맞춤 되도록를 구성 합니다. 이 플래그를 사용 하지 않는 경우는 `CTaskDialog` 모니터를 기준으로 가운데에 배치 됩니다.|
|TDF_RTL_LAYOUT|`CTaskDialog`오른쪽에서 왼쪽 읽기 레이아웃에 대 한를 구성 합니다.|
|TDF_NO_DEFAULT_RADIO_BUTTON|이 표시 될 때 라디오 단추가 선택 되지 않았음을 나타냅니다 `CTaskDialog` .|
|TDF_CAN_BE_MINIMIZED|사용자가를 최소화할 수 있습니다 `CTaskDialog` . 이 옵션을 지원 하기 위해는 `CTaskDialog` 모달이 될 수 없습니다. Mfc는 모덜리스를 지원 하지 않으므로 MFC는이 옵션을 지원 하지 않습니다 `CTaskDialog` .|

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a> CTaskDialog:: SetProgressBarMarquee

의 움직이는 텍스트 막대를 구성 하 `CTaskDialog` 고 대화 상자에 추가 합니다.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>매개 변수

*bEnabled*<br/>
진행 움직이는 막대를 사용 하려면 TRUE이 고, 그렇지 않으면입니다. 선택 윤곽 표시줄을 사용 하지 않도록 설정 하 고에서 제거 하려면 FALSE로 설정 `CTaskDialog` 합니다.

*nMarqueeSpeed*<br/>
진행 움직이는 막대의 속도를 나타내는 정수입니다.

### <a name="remarks"></a>설명

Marquee 막대가 클래스의 기본 텍스트 아래에 나타납니다 `CTaskDialog` .

*NMarqueeSpeed* 를 사용 하 여 움직이는 막대의 속도를 설정 합니다. 값이 클수록 속도가 느립니다. *NMarqueeSpeed* 의 값이 0 이면 움직이는 텍스트 막대가 Windows의 기본 속도로 이동 합니다.

이 메서드는 *nMarqueeSpeed* 가 0 보다 작은 [경우 매크로를](diagnostic-services.md#ensure) 사용 하 여 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a> CTaskDialog:: SetProgressBarPosition

진행률 표시줄의 위치를 조정 합니다.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>매개 변수

*nProgressPos*<br/>
진행 진행률 표시줄의 위치입니다.

### <a name="remarks"></a>설명

이 메서드는 *nProgressPos* 가 진행률 표시줄 범위에 없는 경우 [확인](diagnostic-services.md#ensure) 매크로와 함께 예외를 throw 합니다. [Ctaskdialog:: SetProgressBarRange](#setprogressbarrange)를 사용 하 여 진행률 표시줄 범위를 변경할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a> CTaskDialog:: SetProgressBarRange

진행률 표시줄의 범위를 조정 합니다.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>매개 변수

*nRangeMin*<br/>
진행 진행률 표시줄의 하 한입니다.

*nRangeMax*<br/>
진행 진행률 표시줄의 상한입니다.

### <a name="remarks"></a>설명

진행률 표시줄의 위치는 *nRangeMin* 및 *nRangeMax* 을 기준으로 합니다. 예를 들어 *nRangeMin* 가 50이 고 *nRangeMax* 가 100 이면 75의 위치는 진행률 표시줄의 중간입니다. [Ctaskdialog:: SetProgressBarPosition](#setprogressbarposition) 를 사용 하 여 진행률 표시줄의 위치를 설정 합니다.

진행률 표시줄을 표시 하려면 TDF_SHOW_PROGRESS_BAR 옵션을 사용 하도록 설정 하 고 TDF_SHOW_MARQUEE_PROGRESS_BAR 사용 하지 않도록 설정 해야 합니다. 이 메서드는 TDF_SHOW_PROGRESS_BAR를 자동으로 설정 하 고 TDF_SHOW_MARQUEE_PROGRESS_BAR를 지웁니다. [Ctaskdialog:: SetOptions](#setoptions) 를 사용 하 여 [Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)의이 인스턴스에 대 한 옵션을 수동으로 변경 합니다.

이 메서드는 *nRangeMin* 가 *nRangeMax* 보다 작지 않은 경우 [확인](diagnostic-services.md#ensure) 매크로와 함께 예외를 throw 합니다. 이 메서드는 `CTaskDialog` 가 이미 표시 되어 있고 움직이는 텍스트 진행률 표시줄을 포함 하는 경우에도 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a> CTaskDialog:: SetProgressBarState

진행률 표시줄의 상태를 설정 하 고에 표시 합니다 `CTaskDialog` .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>매개 변수

*nState*<br/>
진행 진행률 표시줄의 상태입니다. 가능한 값은 설명 섹션을 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는가 이미 표시 되어 있고 움직이는 텍스트 진행률 표시줄이 있는 경우 매크로를 사용 하 여 예외를 throw 합니다 [](diagnostic-services.md#ensure) `CTaskDialog` .

다음 표에서는 *Nstate* 에 사용할 수 있는 값을 보여 줍니다. 이러한 모든 경우에는 지정 된 중지 위치에 도달할 때까지 진행률 표시줄이 일반 색으로 채워집니다. 그러면 상태에 따라 색이 변경 됩니다.

|Name|설명|
|-|-|
|PBST_NORMAL|진행률 표시줄이 채워지면에서 `CTaskDialog` 막대의 색을 변경 하지 않습니다. 기본적으로 일반 색은 녹색입니다.|
|PBST_ERROR|진행률 표시줄이 채워지면에서 `CTaskDialog` 막대의 색을 오류 색으로 변경 합니다. 기본적으로이는 빨강입니다.|
|PBST_PAUSED|진행률 표시줄이 채워지면에서 `CTaskDialog` 막대의 색을 일시 중지 된 색으로 변경 합니다. 기본적으로 노란색입니다.|

[Ctaskdialog:: SetProgressBarPosition](#setprogressbarposition)를 사용 하 여 진행률 표시줄이 중지 되는 위치를 설정할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a> CTaskDialog:: SetRadioButtonOptions

라디오 단추를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>매개 변수

*nRadioButtonID*<br/>
진행 라디오 단추 컨트롤의 ID입니다.

*bEnabled*<br/>
진행 라디오 단추를 사용 하려면 TRUE이 고, 그렇지 않으면입니다. 라디오 단추를 사용 하지 않으려면 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

이 메서드는 *nRadioButtonID* 가 라디오 단추에 대 한 유효한 ID가 아닌 경우 [확인](diagnostic-services.md#ensure) 매크로를 사용 하 여 예외를 throw 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a> CTaskDialog:: SetVerificationCheckbox

확인 확인란의 선택 상태를 설정 합니다.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>매개 변수

*bChecked*<br/>
진행 이 표시 될 때 확인 확인란을 선택 하려면 TRUE로 설정 하 `CTaskDialog` 고, FALSE 이면가 표시 될 때 확인 확인란을 선택 취소 합니다 `CTaskDialog` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a> CTaskDialog:: SetVerificationCheckboxText

확인 확인란의 오른쪽에 표시 되는 텍스트를 설정 합니다.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>매개 변수

*strVerificationText*<br/>
진행 이 메서드가 확인 확인란 옆에 표시 하는 텍스트입니다.

### <a name="remarks"></a>설명

클래스의이 인스턴스가 이미 표시 되어 있는 경우이 메서드는 [확인](diagnostic-services.md#ensure) 매크로를 사용 하 여 예외를 throw `CTaskDialog` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a> CTaskDialog:: SetWindowTitle

의 제목을 설정 합니다 `CTaskDialog` .

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>매개 변수

*strWindowTitle*<br/>
진행 의 새 제목 `CTaskDialog` 입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a> CTaskDialog:: ShowDialog

을 만들어 표시 `CTaskDialog` 합니다.

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>매개 변수

*strContent*<br/>
진행 의 내용에 사용할 문자열 `CTaskDialog` 입니다.

*strMainInstruction*<br/>
진행 의 기본 명령 `CTaskDialog` 입니다.

*strTitle*<br/>
진행 의 제목 `CTaskDialog` 입니다.

*nIDCommandControlsFirst*<br/>
진행 첫 번째 명령의 문자열 ID입니다.

*nIDCommandControlsLast*<br/>
진행 마지막 명령의 문자열 ID입니다.

*nCommonButtons*<br/>
진행 에 추가할 단추의 마스크입니다 `CTaskDialog` .

*nTaskDialogOptions*<br/>
진행 에 사용할 옵션 집합입니다 `CTaskDialog` .

*strFooter*<br/>
진행 바닥글로 사용할 문자열입니다.

### <a name="return-value"></a>반환 값

사용자가 선택한 항목에 해당 하는 정수입니다.

### <a name="remarks"></a>설명

이 정적 메서드를 사용 하면 `CTaskDialog` 코드에서 개체를 명시적으로 만들지 않고도 클래스의 인스턴스를 만들 수 있습니다 `CTaskDialog` . 개체가 없기 때문에 `CTaskDialog` `CTaskDialog` 이 메서드를 사용 하 여 사용자에 게를 표시 하는 경우의 다른 메서드를 호출할 수 없습니다 `CTaskDialog` .

이 메서드는 응용 프로그램의 리소스 파일에 있는 데이터를 사용 하 여 명령 단추 컨트롤을 만듭니다. 리소스 파일의 문자열 테이블에는 문자열 Id가 연결 된 여러 문자열이 있습니다. 이 메서드는 *nIDCommandControlsFirst* 과 *nCommandControlsLast* 사이에 있는 문자열 테이블의 유효한 각 항목에 대 한 명령 단추 컨트롤을 추가 합니다. 이러한 명령 단추 컨트롤의 경우 문자열 테이블의 문자열은 컨트롤의 캡션입니다. 문자열 ID는 컨트롤의 ID입니다.

유효한 옵션 목록은 [Ctaskdialog:: SetOptions](#setoptions) 를 참조 하세요.

는 `CTaskDialog` 사용자가 일반 단추 또는 명령 링크 컨트롤을 선택 하거나를 닫을 때 닫힙니다 `CTaskDialog` . 반환 값은 사용자가 대화 상자를 닫은 방법을 나타내는 식별자입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a> CTaskDialog:: TaskDialogCallback

프레임 워크는 다양 한 Windows 메시지에 대 한 응답으로이 메서드를 호출 합니다.

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>매개 변수

*hwnd*<br/>
진행 의 `m_hWnd` 구조체에 대 한 핸들 `CTaskDialog` 입니다.

*uNotification*<br/>
진행 생성 된 메시지를 지정 하는 알림 코드입니다.

*wParam*<br/>
진행 메시지에 대 한 자세한 정보입니다.

*lParam*<br/>
진행 메시지에 대 한 자세한 정보입니다.

*dwRefData*<br/>
진행 `CTaskDialog` 콜백 메시지가 적용 되는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

는 특정 알림 코드에 따라 달라 집니다. 자세한 내용은 설명 부분을 참조하세요.

### <a name="remarks"></a>설명

의 기본 구현은 `TaskDialogCallback` 특정 메시지를 처리 한 다음 [Ctaskdialog 클래스](../../mfc/reference/ctaskdialog-class.md)의 적절 한 메서드를 호출 합니다. 예를 들어 TDN_BUTTON_CLICKED 메시지에 대 한 응답으로 `TaskDialogCallback` [Ctaskdialog:: OnCommandControlClick](#oncommandcontrolclick)을 호출 합니다.

*WParam* 및 *lParam* 의 값은 생성 된 특정 메시지에 따라 다릅니다. 이러한 값 중 하나 또는 둘 모두를 비워 둘 수 있습니다. 다음 표에는 지원 되는 기본 알림과 *wParam* 및 *lParam* 의 값이 표시 됩니다. 파생 클래스에서이 메서드를 재정의 하는 경우 다음 표의 각 메시지에 대 한 콜백 코드를 구현 해야 합니다.

|알림 메시지|*wParam* 기본값|*lParam* 기본값|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|사용되지 않습니다.|사용되지 않습니다.|
|TDN_NAVIGATED|사용되지 않습니다.|사용되지 않습니다.|
|TDN_BUTTON_CLICKED|명령 단추 컨트롤 ID입니다.|사용되지 않습니다.|
|TDN_HYPERLINK_CLICKED|사용되지 않습니다.|링크를 포함 하는 [Lpcwstr](/windows/win32/WinProg/windows-data-types) 구조체입니다.|
|TDN_TIMER|가 만들어지거나 타이머가 다시 설정 된 이후의 시간 (밀리초) `CTaskDialog` 입니다.|사용되지 않습니다.|
|TDN_DESTROYED|사용되지 않습니다.|사용되지 않습니다.|
|TDN_RADIO_BUTTON_CLICKED|라디오 단추 ID입니다.|사용되지 않습니다.|
|TDN_DIALOG_CONSTRUCTED|사용되지 않습니다.|사용되지 않습니다.|
|TDN_VERIFICATION_CLICKED|확인란이 선택 되어 있으면 1이 고, 그렇지 않으면 0입니다.|사용되지 않습니다.|
|TDN_HELP|사용되지 않습니다.|사용되지 않습니다.|
|TDN_EXPANDO_BUTTON_CLICKED|확장 영역이 축소 된 경우 0입니다. 확장 텍스트가 표시 되는 경우 0이 아닙니다.|사용되지 않습니다.|

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[연습: 응용 프로그램에 CTaskDialog 추가](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)

---
description: '자세히 알아보기: CMFCEditBrowseCtrl 클래스'
title: CMFCEditBrowseCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: f63ab87207678cca87db84b73e49fba571634f3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293893"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 클래스

`CMFCEditBrowseCtrl`클래스는 찾아보기 단추를 선택적으로 포함 하는 편집 가능한 텍스트 상자 인 편집 찾아보기 컨트롤을 지원 합니다. 사용자가 찾아보기 단추를 클릭하면 컨트롤은 사용자 지정 작업을 수행하거나 파일 브라우저 또는 폴더 브라우저가 포함된 표준 대화 상자를 표시합니다.

## <a name="syntax"></a>구문

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|기본 생성자입니다.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton)|찾아보기 단추를 사용 하거나 사용 하지 않도록 설정 합니다 (숨기기).|
|[CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)|찾아보기 단추를 사용 하도록 설정 하 고 편집 찾아보기 컨트롤을 *파일 찾아보기* 모드로 전환 합니다.|
|[CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton)|찾아보기 단추를 사용 하도록 설정 하 고 편집 찾아보기 컨트롤을 *폴더 찾아보기* 모드로 전환 합니다.|
|[CMFCEditBrowseCtrl:: GetMode](#getmode)|현재 찾아보기 모드를 반환 합니다.|
|[CMFCEditBrowseCtrl:: OnAfterUpdate](#onafterupdate)|찾아보기 작업의 결과로 편집 찾아보기 컨트롤이 업데이트 된 후 프레임 워크에서 호출 됩니다.|
|[CMFCEditBrowseCtrl:: OnBrowse](#onbrowse)|사용자가 찾아보기 단추를 클릭 한 후 프레임 워크에서 호출 됩니다.|
|[CMFCEditBrowseCtrl:: OnChangeLayout](#onchangelayout)|현재 편집 찾아보기 컨트롤을 다시 그립니다.|
|[CMFCEditBrowseCtrl:: OnDrawBrowseButton](#ondrawbrowsebutton)|찾아보기 단추를 그리기 위해 프레임 워크에서 호출 됩니다.|
|[CMFCEditBrowseCtrl:: OnIllegalFileName](#onillegalfilename)|편집 컨트롤에 잘못 된 파일 이름을 입력 한 경우 프레임 워크에서 호출 됩니다.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|창 메시지가 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 및 [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 함수로 디스패치 되기 전에 변환 합니다. 구문 및 자세한 내용은 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 참조 하세요.|
|[CMFCEditBrowseCtrl:: SetBrowseButtonImage](#setbrowsebuttonimage)|찾아보기 단추에 대 한 사용자 지정 이미지를 설정 합니다.|

## <a name="remarks"></a>설명

편집 찾아보기 컨트롤을 사용 하 여 파일 또는 폴더 이름을 선택 합니다. 필요에 따라 컨트롤을 사용 하 여 대화 상자를 표시 하는 등의 사용자 지정 작업을 수행 합니다. 찾아보기 단추를 표시 하거나 표시 하지 않고 단추에 사용자 지정 레이블이나 이미지를 적용할 수 있습니다.

편집 찾아보기 컨트롤의 *찾아보기 모드* 는 찾아보기 단추를 표시할지 여부와 단추를 클릭할 때 발생 하는 동작을 결정 합니다. 자세한 내용은 [Getmode](#getmode) 메서드를 참조 하세요.

`CMFCEditBrowseCtrl`클래스는 다음과 같은 모드를 지원 합니다.

- **사용자 지정 모드**

   사용자 지정 작업은 사용자가 찾아보기 단추를 클릭할 때 수행 됩니다. 예를 들어 응용 프로그램 관련 대화 상자를 표시할 수 있습니다.

- **파일 모드**

   사용자가 찾아보기 단추를 클릭 하면 표준 파일 선택 대화 상자가 표시 됩니다.

- **폴더 모드**

   사용자가 찾아보기 단추를 클릭 하면 표준 폴더 선택 대화 상자가 표시 됩니다.

## <a name="how-to-specify-an-edit-browse-control"></a>방법: 편집 찾아보기 컨트롤 지정

응용 프로그램에서 편집 찾아보기 컨트롤을 통합 하려면 다음 단계를 수행 합니다.

1. 사용자 지정 찾아보기 모드를 구현 하려면 클래스에서 고유한 클래스를 파생 시킨 `CMFCEditBrowseCtrl` 다음 [CMFCEditBrowseCtrl:: onbrowse](#onbrowse) 메서드를 재정의 합니다. 재정의 된 메서드에서 사용자 지정 찾아보기 동작을 실행 하 고 결과를 사용 하 여 편집 찾아보기 컨트롤을 업데이트 합니다.

1. `CMFCEditBrowseCtrl`개체 또는 파생 된 편집 찾아보기 컨트롤 개체를 부모 창 개체에 포함 합니다.

1. **클래스 마법사** 를 사용 하 여 대화 상자를 만드는 경우 편집 컨트롤 ( `CEdit` )을 대화 상자 폼에 추가 합니다. 또한 헤더 파일의 컨트롤에 액세스 하는 변수를 추가 합니다. 헤더 파일에서 변수의 형식을에서로 변경 합니다 `CEdit` `CMFCEditBrowseCtrl` . 편집 찾아보기 컨트롤은 자동으로 생성 됩니다. **클래스 마법사** 를 사용 하지 않는 경우 `CMFCEditBrowseCtrl` 헤더 파일에 변수를 추가한 다음 해당 메서드를 호출 `Create` 합니다.

1. 대화 상자에 편집 찾아보기 컨트롤을 추가 하는 경우에는 **클래스 마법사** 도구를 사용 하 여 데이터 교환을 설정 합니다.

1. [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)또는 [EnableBrowseButton](#enablebrowsebutton) 메서드를 호출 하 여 찾아보기 모드를 설정 하 고 찾아보기 단추를 표시 합니다. [Getmode](#getmode) 메서드를 호출 하 여 현재 찾아보기 모드를 가져옵니다.

1. 찾아보기 단추에 대 한 사용자 지정 이미지를 제공 하려면 [SetBrowseButtonImage](#setbrowsebuttonimage) 메서드를 호출 하거나 [OnDrawBrowseButton](#ondrawbrowsebutton) 메서드를 재정의 합니다.

1. 편집 찾아보기 컨트롤에서 찾아보기 단추를 제거 하려면 *Benable* 매개 변수를 FALSE로 설정 하 여 [EnableBrowseButton](#enablebrowsebutton) 메서드를 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>예제

다음 예제에서는 클래스에서 및의 두 메서드를 사용 하는 방법을 보여 줍니다. `CMFCEditBrowseCtrl` `EnableFolderBrowseButton` `EnableFileBrowseButton` 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxeditbrowsectrl

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a> CMFCEditBrowseCtrl:: EnableBrowseButton

현재 편집 찾아보기 컨트롤에 찾아보기 단추를 표시 하거나 표시 하지 않습니다.

```cpp
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
찾아보기 단추를 표시 하려면 TRUE로 설정 합니다. FALSE는 찾아보기 단추를 표시 하지 않습니다. 기본값은 TRUE입니다.

*szLabel*<br/>
찾아보기 단추에 표시 되는 레이블입니다. 기본값은 " **...**"입니다.

### <a name="remarks"></a>설명

*Benable* 매개 변수가 TRUE 이면 찾아보기 단추를 클릭할 때 수행할 사용자 지정 작업을 구현 합니다. 사용자 지정 작업을 구현 하려면 클래스에서 클래스를 파생 시킨 `CMFCEditBrowseCtrl` 다음 해당 [onbrowse](#onbrowse) 메서드를 재정의 합니다.

*Benable* 매개 변수가 TRUE 이면 컨트롤의 찾아보기 모드는이 `BrowseMode_Default` 고, 그렇지 않으면 찾아보기 모드는 `BrowseMode_None` 입니다. 찾아보기 모드에 대 한 자세한 내용은 [Getmode](#getmode) 메서드를 참조 하세요.

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a> CMFCEditBrowseCtrl:: EnableFileBrowseButton

현재 편집 찾아보기 컨트롤의 찾아보기 단추를 표시 하 고 컨트롤을 *파일 찾아보기* 모드로 전환 합니다.

```cpp
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>매개 변수

*lpszDefExt*<br/>
파일 선택 대화 상자에서 사용되는 기본 파일 이름 확장명을 지정합니다. 기본값은 NULL입니다.

*lpszFilter*<br/>
파일 선택 대화 상자에서 사용되는 기본 필터 문자열을 지정합니다. 기본값은 NULL입니다.

*dwFlags*<br/>
대화 상자 플래그입니다. 기본값은 OFN_HIDEREADONLY와 OFN_OVERWRITEPROMPT의 비트 조합(OR)입니다.

### <a name="remarks"></a>설명

편집 찾아보기 컨트롤이 파일 찾아보기 모드에 있고 사용자가 찾아보기 단추를 클릭하는 경우 컨트롤이 표준 파일 선택 대화 상자를 표시합니다.

사용 가능한 플래그의 전체 목록은 [OPENFILENAME 구조체](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)를 참조 하세요.

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a> CMFCEditBrowseCtrl:: EnableFolderBrowseButton

현재 편집 찾아보기 컨트롤에 찾아보기 단추를 표시 하 고 *폴더 찾아보기* 모드에 컨트롤을 배치 합니다.

```cpp
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>설명

편집 찾아보기 컨트롤이 폴더 찾아보기 모드에 있고 사용자가 찾아보기 단추를 클릭 하면 컨트롤이 표준 폴더 선택 대화 상자를 표시 합니다.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a> CMFCEditBrowseCtrl:: GetMode

현재 편집 찾아보기 컨트롤의 찾아보기 모드를 검색 합니다.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>반환 값

편집 찾아보기 컨트롤의 현재 모드를 지정 하는 열거형 값 중 하나입니다. 찾아보기 모드는 프레임 워크에서 찾아보기 단추를 표시할지 여부와 사용자가 해당 단추를 클릭할 때 발생 하는 동작을 결정 합니다.

다음 표에서는 가능한 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|`BrowseMode_Default`|**사용자 지정 모드** 입니다. 프로그래머가 정의한 동작을 수행 합니다.|
|`BrowseMode_File`|**파일 모드** 입니다. 표준 파일 브라우저 대화 상자가 표시 됩니다.|
|`BrowseMode_Folder`|**폴더 모드** 입니다. 표준 폴더 브라우저 대화 상자가 표시 됩니다.|
|`BrowseMode_None`|찾아보기 단추가 표시 되지 않습니다.|

### <a name="remarks"></a>설명

기본적으로 개체는 `CMFCEditBrowseCtrl` 모드로 초기화 됩니다 `BrowseMode_None` . [CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)및 [CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton) 메서드를 사용 하 여 찾아보기 모드를 수정 합니다.

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a> CMFCEditBrowseCtrl:: OnAfterUpdate

찾아보기 작업의 결과로 편집 찾아보기 컨트롤이 업데이트 된 후 프레임 워크에서 호출 됩니다.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>설명

사용자 지정 작업을 구현 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a> CMFCEditBrowseCtrl:: OnBrowse

사용자가 편집 찾아보기 컨트롤의 찾아보기 단추를 클릭 한 후 프레임 워크에서 호출 됩니다.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>설명

사용자가 편집 찾아보기 컨트롤의 찾아보기 단추를 클릭할 때이 메서드를 사용 하 여 사용자 지정 코드를 실행 합니다. 클래스에서 고유한 클래스를 파생 시키고 `CMFCEditBrowseCtrl` 메서드를 재정의 `OnBrowse` 합니다. 이 메서드에서 사용자 지정 찾아보기 작업을 구현 하 고 필요에 따라 편집 찾아보기 컨트롤의 텍스트 상자를 업데이트 합니다. 응용 프로그램에서 [EnableBrowseButton](#enablebrowsebutton) 메서드를 사용 하 여 편집 찾아보기 컨트롤을 *사용자 지정 찾아보기* 모드로 전환 합니다.

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a> CMFCEditBrowseCtrl:: OnChangeLayout

현재 편집 찾아보기 컨트롤을 다시 그립니다.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>설명

프레임 워크는 편집 찾아보기 컨트롤의 찾아보기 모드가 변경 될 때이 메서드를 호출 합니다. 자세한 내용은 [CMFCEditBrowseCtrl:: GetMode](#getmode)를 참조 하세요.

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a> CMFCEditBrowseCtrl:: OnDrawBrowseButton

편집 찾아보기 컨트롤에 찾아보기 단추를 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
디바이스 컨텍스트에 대한 포인터입니다.

*직교*<br/>
찾아보기 단추의 경계 사각형입니다.

*bIsButtonPressed*<br/>
단추를 누르면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

*bIsButtonHot*<br/>
단추가 강조 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

파생 클래스에서이 함수를 재정의 하 여 찾아보기 단추의 모양을 사용자 지정 합니다.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a> CMFCEditBrowseCtrl:: SetBrowseButtonImage

편집 찾아보기 컨트롤의 찾아보기 단추에 사용자 지정 이미지를 설정 합니다.

```cpp
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>매개 변수

*hIcon*<br/>
아이콘 핸들입니다.

*hBitmap*<br/>
비트맵 핸들입니다.

*uiBmpResId*<br/>
비트맵의 리소스 ID입니다.

*bAutoDestroy*<br/>
이 메서드가 종료 될 때 지정 된 아이콘 또는 비트맵을 삭제 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 찾아보기 단추에 사용자 지정 이미지를 적용할 수 있습니다. 기본적으로 프레임 워크는 편집 찾아보기 컨트롤이 *파일 찾아보기* 또는 *폴더 찾아보기* 모드에 있을 때 표준 이미지를 가져옵니다.

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a> CMFCEditBrowseCtrl:: OnIllegalFileName

편집 컨트롤에 잘못 된 파일 이름을 입력 한 경우 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>매개 변수

*strFileName*<br/>
잘못 된 파일 이름을 지정 합니다.

### <a name="return-value"></a>반환 값

이 파일 이름을 파일 대화 상자에 추가로 전달할 수 없으면 FALSE를 반환 해야 합니다. 이 경우 포커스가 편집 컨트롤로 다시 설정 되 고 사용자는 계속 편집 해야 합니다. 기본 구현에서는 사용자에 게 잘못 된 파일 이름을 알려 주는 메시지 상자를 표시 하 고 FALSE를 반환 합니다. 이 메서드를 재정의 하 고, 파일 이름을 수정 하 고, 추가 처리를 위해 TRUE를 반환할 수 있습니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)

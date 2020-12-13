---
description: '자세히 알아보기: CColorDialog 클래스'
title: CColorDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: d9af49d4986f0619211ed4fd2dc9174acea27d0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150139"
---
# <a name="ccolordialog-class"></a>CColorDialog 클래스

색 선택 대화 상자를 응용 프로그램에 통합할 수 있습니다.

## <a name="syntax"></a>구문

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|`CColorDialog` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CColorDialog::D oModal](#domodal)|색 대화 상자를 표시 하 고 사용자가 선택할 수 있게 합니다.|
|[CColorDialog:: GetColor](#getcolor)|`COLORREF`선택한 색의 값을 포함 하는 구조체를 반환 합니다.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|사용자가 만든 사용자 지정 색을 검색 합니다.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|현재 색 선택을 지정 된 색으로 강제로 적용 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CColorDialog:: OnColorOK](#oncolorok)|대화 상자에 입력 된 색의 유효성을 검사 하려면를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CColorDialog:: m_cc](#m_cc)|대화 상자의 설정을 사용자 지정 하는 데 사용 되는 구조체입니다.|

## <a name="remarks"></a>설명

`CColorDialog`개체는 표시 시스템에 대해 정의 된 색 목록을 포함 하는 대화 상자입니다. 사용자는 목록에서 특정 색을 선택 하거나 만들 수 있습니다. 그러면이 대화 상자가 종료 될 때 응용 프로그램에 다시 보고 됩니다.

개체를 생성 하려면 `CColorDialog` 제공 된 생성자를 사용 하거나 새 클래스를 파생 시키고 사용자 지정 생성자를 사용 합니다.

대화 상자를 생성 한 후에는 [m_cc](#m_cc) 구조체의 값을 설정 하거나 수정 하 여 대화 상자의 컨트롤 값을 초기화할 수 있습니다. *M_cc* 구조체의 형식은 [사용자가 choosecolor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1)입니다.

대화 상자의 컨트롤을 초기화 한 후 `DoModal` 멤버 함수를 호출 하 여 대화 상자를 표시 하 고 사용자가 색을 선택할 수 있습니다. `DoModal` 대화 상자의 OK (IDOK) 또는 Cancel (IDCANCEL) 단추 중에서 사용자가 선택한 항목을 반환 합니다.

`DoModal`에서 IDOK를 반환 하는 경우의 `CColorDialog` 멤버 함수 중 하나를 사용 하 여 사용자가 입력 한 정보를 검색할 수 있습니다.

Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 사용 하 여 대화 상자를 초기화 하는 동안 오류가 발생 했는지 확인 하 고 오류에 대해 자세히 알아볼 수 있습니다.

`CColorDialog` 는 Windows 버전 3.1 이상과 함께 제공 되는 COMMDLG.DLL 파일을 기반으로 합니다.

대화 상자를 사용자 지정 하려면에서 클래스를 파생 시키고 `CColorDialog` , 사용자 지정 대화 상자 템플릿을 제공 하 고, 확장 된 컨트롤에서 알림 메시지를 처리 하는 메시지 맵을 추가 합니다. 처리 되지 않은 모든 메시지는 기본 클래스에 전달 되어야 합니다.

후크 함수 사용자 지정은 필요 하지 않습니다.

> [!NOTE]
> 일부 설치에서는 `CColorDialog` 프레임 워크를 사용 하 여 다른 개체를 회색으로 만든 경우 개체가 회색 배경으로 표시 되지 않습니다 `CDialog` .

사용에 대 한 자세한 내용은 `CColorDialog` [일반 대화 상자 클래스](../../mfc/common-dialog-classes.md) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxdlgs

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a> CColorDialog::CColorDialog

`CColorDialog` 개체를 생성합니다.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>매개 변수

*clrInit*<br/>
기본 색 선택입니다. 값을 지정 하지 않으면 기본값은 RGB (0, 0, 0) (검정)입니다.

*dwFlags*<br/>
대화 상자의 함수와 모양을 사용자 지정 하는 플래그 집합입니다. 자세한 내용은 Windows SDK [사용자가 choosecolor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1) 구조체를 참조 하세요.

*pParentWnd*<br/>
대화 상자의 부모 또는 소유자 창에 대 한 포인터입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a> CColorDialog::D oModal

이 함수를 호출 하 여 Windows 일반 색 대화 상자를 표시 하 고 사용자가 색을 선택할 수 있습니다.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>반환 값

IDOK 또는 IDCANCEL. IDCANCEL이 반환 되는 경우 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) 함수를 호출 하 여 오류가 발생 했는지 여부를 확인 합니다.

IDOK 및 IDCANCEL는 사용자가 확인 또는 취소 단추를 선택 했는지 여부를 나타내는 상수입니다.

### <a name="remarks"></a>설명

[M_cc](#m_cc) 구조의 멤버를 설정 하 여 다양 한 색 대화 상자 옵션을 초기화 하려면를 호출 하기 전에 `DoModal` 대화 상자 개체가 생성 된 후에이 작업을 수행 해야 합니다.

를 호출한 후에 `DoModal` 는 다른 멤버 함수를 호출 하 여 사용자가 대화 상자에 입력 한 설정 또는 정보를 검색할 수 있습니다.

### <a name="example"></a>예제

  [CColorDialog:: CColorDialog](#ccolordialog)의 예제를 참조 하세요.

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a> CColorDialog:: GetColor

`DoModal`사용자가 선택한 색에 대 한 정보를 검색 하려면를 호출한 후이 함수를 호출 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

색 대화 상자에서 선택한 색의 RGB 정보를 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a> CColorDialog::GetSavedCustomColors

`CColorDialog` 개체를 사용 하면 색을 선택 하는 것 외에 사용자가 최대 16 개의 사용자 지정 색을 정의할 수 있습니다.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>반환 값

사용자가 만든 사용자 지정 색을 저장 하는 16 개의 RGB 색 값 배열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`GetSavedCustomColors`멤버 함수는 이러한 색에 대 한 액세스를 제공 합니다. 이러한 색은 [DoModal](#domodal) 가 IDOK를 반환한 후 검색할 수 있습니다.

반환 된 배열의 각 16 개 RGB 값은 RGB (255255255) (흰색)로 초기화 됩니다. 사용자가 선택한 사용자 지정 색은 응용 프로그램 내에서 대화 상자 호출 사이에만 저장 됩니다. 응용 프로그램 호출 사이에 이러한 색을 저장 하려는 경우 초기화 ()와 같은 다른 방식으로 저장 해야 합니다. INI) 파일을

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a> CColorDialog:: m_cc

해당 멤버가 대화 상자의 특성 및 값을 저장 하는 [사용자가 choosecolor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1)형식의 구조체입니다.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 `CColorDialog` [DoModal](#domodal) 멤버 함수를 호출 하기 전에 *m_cc* 를 사용 하 여 대화 상자의 다양 한 측면을 설정할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a> CColorDialog:: OnColorOK

대화 상자에 입력 된 색의 유효성을 검사 하려면를 재정의 합니다.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>반환 값

대화 상자를 해제할 수 없으면 0이 아닙니다. 그렇지 않으면 0은 입력 된 색을 그대로 적용 합니다.

### <a name="remarks"></a>설명

색 대화 상자에서 사용자가 선택 하는 색의 사용자 지정 유효성 검사를 제공 하려는 경우에만이 함수를 재정의 합니다.

사용자는 다음 두 가지 방법 중 하나를 사용 하 여 색을 선택할 수 있습니다.

- 색상표에서 색을 클릭 합니다. 그러면 선택한 색의 RGB 값이 적절 한 RGB 편집 상자에 반영 됩니다.

- RGB 편집 상자에 값 입력

재정의 `OnColorOK` 를 사용 하면 사용자가 응용 프로그램별 이유로 일반 색 대화 상자에 입력 하는 색을 거부할 수 있습니다.

일반적으로 프레임 워크는 색의 기본 유효성 검사를 제공 하 고 잘못 된 색을 입력 한 경우 메시지 상자를 표시 하기 때문에이 함수를 사용할 필요가 없습니다.

내에서 [SetCurrentColor](#setcurrentcolor) `OnColorOK` 를 호출 하 여 색 선택을 강제로 적용할 수 있습니다. 가 실행 `OnColorOK` 된 후 (즉, 사용자가 **확인** 을 클릭 하 여 색 변경을 수락) [getcolor](#getcolor) 를 호출 하 여 새 색의 RGB 값을 가져올 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a> CColorDialog::SetCurrentColor

를 호출한 후이 함수를 호출 `DoModal` 하 여 현재 색 선택을 *clr* 에 지정 된 색 값으로 강제로 적용 합니다.

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
RGB 색 값입니다.

### <a name="remarks"></a>설명

이 함수는 메시지 처리기 또는에서 호출 됩니다 `OnColorOK` . 이 대화 상자는 *clr* 매개 변수의 값에 따라 사용자의 선택 항목을 자동으로 업데이트 합니다.

### <a name="example"></a>예제

  [CColorDialog:: OnColorOK](#oncolorok)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)

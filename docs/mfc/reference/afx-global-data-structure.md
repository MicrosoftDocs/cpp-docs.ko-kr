---
description: '다음에 대 한 자세한 정보: AFX_GLOBAL_DATA 구조체'
title: AFX_GLOBAL_DATA 구조체
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 3f7bb7bfeb4e5985d558211450755972c0f55812
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322855"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA 구조체

`AFX_GLOBAL_DATA` 구조는 프레임워크를 관리하거나 애플리케이션의 모양과 동작을 사용자 지정하는 데 사용되는 필드 및 메서드를 포함합니다.

## <a name="syntax"></a>구문

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|`AFX_GLOBAL_DATA` 구조를 생성합니다.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|브러시, 글꼴 및 DLL 등 프레임워크에 의해 할당되는 리소스를 해제합니다.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|지정된 점을 기준으로 지정된 각도만큼 회전하는 회전 변환을 만듭니다.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|지정된 영역에 컨트롤 부모의 배경을 그립니다.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|지정된 테마의 비주얼 스타일로 지정된 텍스트를 그립니다.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|지정된 버퍼에서 지정된 XML 태그 쌍을 제거합니다.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|지정된 사용자 인터페이스 요소의 현재 색을 검색합니다.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|글로벌 데이터에 저장된 `ID2D1Factory` 인터페이스로 포인터를 반환합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|식별자가 `IDC_HAND`인 손 모양의 미리 정의된 커서를 검색합니다.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|ITaskBarList 인터페이스에 대한 포인터를 만들고 글로벌 데이터에 저장합니다.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|ITaskBarList3 인터페이스에 대한 포인터를 만들고 글로벌 데이터에 저장합니다.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|최소화되지 않은 창의 비클라이언트 영역과 관련된 메트릭을 검색합니다.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|셸 자동 숨기기 막대의 위치를 결정합니다.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|현재 글꼴에서 텍스트 문자의 높이를 검색합니다.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|글로벌 데이터에 저장된 `IWICImagingFactory` 인터페이스로 포인터를 반환합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|글로벌 데이터에 저장된 `IDWriteFactory` 인터페이스로 포인터를 반환합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|`D2D`, `DirectWrite`및 `WIC` 팩터리를 초기화합니다. 주 창이 초기화되기 전에 이 메서드를 호출합니다.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|미리 정의된 32비트 아이콘이 지원되는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|`D2D` 의 초기화 여부를 확인합니다.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 메서드를 호출하는 간단한 방법을 제공합니다.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|이미지가 현재 고대비로 표시되는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|데스크톱 메뉴 애니메이션의 현재 상태 및 작업 표시줄 자동 숨기기 기능을 탐지합니다.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|지정된 MFC 창 클래스를 등록합니다.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|GetITaskbarList 및 GetITaskbarList3 메서드를 통해 얻은 인터페이스를 해제합니다.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Windows [테마 및 비주얼 스타일](/windows/win32/Controls/visual-styles-overview)을 지원하는 메서드에 액세스하는 내부 함수 포인터를 다시 초기화합니다.|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 메서드를 호출하는 간단한 방법을 제공합니다.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|지정된 논리 글꼴을 만듭니다.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|구문 분석 이름에서 셸 항목 개체를 만들고 초기화합니다.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|프레임워크에서 사용하는 논리 글꼴을 다시 초기화합니다.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|프레임워크에서 사용하는 색, 색 농도, 브러시, 펜 및 이미지를 초기화합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Microsoft Active Accessibility 지원을 사용하거나 사용하지 않도록 설정합니다. Active Accessibility는 사용자 인터페이스 요소에 대한 정보를 노출하기 위한 신뢰할 수 있는 방법을 제공합니다.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Microsoft Active Accessibility 지원이 활성화되어 있는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|운영 체제가 계층화된 창을 지원하는지 여부를 나타냅니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|현재 운영 체제가 알파 혼합을 지원하는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|애플리케이션이 Windows 7 운영 체제 이상에서 실행되고 있는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|활성 캡션의 그라데이션 색을 지정합니다. 도킹 창에 일반적으로 사용됩니다.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|비활성 캡션의 그라데이션 색을 지정합니다. 도킹 창에 일반적으로 사용됩니다.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|프레임워크가 미리 정의된 32비트 컬러 아이콘을 사용하는지, 아니면 더 낮은 해상도의 아이콘을 사용하는지를 나타냅니다.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|시스템 글꼴이 메뉴, 도구 모음 및 리본에 사용되는지 여부를 나타냅니다.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|손 모양 커서에 대한 핸들을 저장합니다.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|가로 늘이기 커서에 대한 핸들을 저장합니다.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|세로 늘이기 커서에 대한 핸들을 저장합니다.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|도구 아이콘에 대한 핸들을 저장합니다.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|맨 왼쪽 자동 숨기기 도구 모음에서 도킹 모음의 왼쪽까지의 오프셋을 지정합니다.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|자동 숨기기 도구 모음 사이의 간격을 지정합니다.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|도킹된 상태를 전달하는 데 사용되는 끌기 프레임의 두께를 지정합니다.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|부동 상태를 전달하는 데 사용되는 끌기 프레임의 두께를 지정합니다.|

### <a name="remarks"></a>설명

`AFX_GLOBAL_DATA` 구조에서 대부분의 데이터는 애플리케이션 시작 시 초기화됩니다.

### <a name="inheritance-hierarchy"></a>상속 계층 구조

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>요구 사항

**헤더:** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA:: bIsOSAlphaBlendingSupport

운영 체제에서 알파 혼합을 지원 하는지 여부를 나타냅니다.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>설명

TRUE는 알파 혼합이 지원 됨을 나타냅니다. 그렇지 않으면 FALSE입니다.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a> AFX_GLOBAL_DATA:: CleanUp

브러시, 글꼴 및 DLL 등 프레임워크에 의해 할당되는 리소스를 해제합니다.

```cpp
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D 2D1MakeRotateMatrix

지정된 점을 기준으로 지정된 각도만큼 회전하는 회전 변환을 만듭니다.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>매개 변수

*각도*<br/>
시계 방향 회전 각도(도)입니다.

*중심과*<br/>
회전할 점입니다.

*행렬*<br/>
이 메서드가 반환 될 때 새 회전 변환을 포함 합니다. 이 매개 변수에 대 한 저장소를 할당 해야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK을 반환 하 고 그렇지 않으면 오류 값을 반환 합니다.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a> AFX_GLOBAL_DATA::D rawParentBackground

지정된 영역에 컨트롤 부모의 배경을 그립니다.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 컨트롤 창에 대 한 포인터입니다.

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*lpRect*<br/>
진행 그릴 영역을 제한 하는 사각형에 대 한 포인터입니다. 기본값은 NULL입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a> AFX_GLOBAL_DATA::D rawTextOnGlass

지정된 테마의 비주얼 스타일로 지정된 텍스트를 그립니다.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>매개 변수

*hTheme*<br/>
진행 창의 테마 데이터 또는 NULL에 대 한 핸들입니다. 이 매개 변수가 NULL이 아니고 테마가 지원 되는 경우 프레임 워크는 지정 된 테마를 사용 하 여 텍스트를 그립니다. 그렇지 않으면 테마를 사용하여 텍스트를 그리지 않습니다.

[만들려면 openthemedata](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) 메서드를 사용 하 여 htheme을 만듭니다.

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*iPartId*<br/>
진행 원하는 텍스트 모양이 있는 컨트롤 파트입니다. 자세한 내용은 [파트 및 상태](/windows/win32/controls/parts-and-states)에 설명된 표의 파트 열을 참조하세요. 이 값이 0이면 텍스트가 기본 글꼴로 그려지거나 디바이스 컨텍스트로 선택된 글꼴로 그려집니다.

*iStateId*<br/>
진행 원하는 텍스트 모양이 있는 컨트롤 상태입니다. 자세한 내용은 [파트 및 상태](/windows/win32/controls/parts-and-states)에 설명된 표의 상태 열을 참조하세요.

*strText*<br/>
진행 그릴 텍스트입니다.

*rect*<br/>
진행 지정 된 텍스트가 그려지는 영역의 경계입니다.

*dwFlags*<br/>
진행 지정 된 텍스트를 그리는 방법을 지정 하는 플래그의 비트 조합 (OR)입니다.

*Htheme* 매개 변수가 `NULL` 이거나 테마를 지원 하지 않고 사용할 수 있는 경우 [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) 메서드의 *nformat* 매개 변수는 유효한 플래그를 설명 합니다. 테마가 지원 되는 경우에는 [DrawdwFlags Etextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) 메서드의  매개 변수가 유효한 플래그를 설명 합니다.

*nGlowSize*<br/>
진행 지정 된 텍스트를 그리기 전에 배경에 그려지는 글로우 효과의 크기입니다. 기본값은 0입니다.

*clrText*<br/>
진행 지정 된 텍스트가 그려지는 색입니다. 기본값은 기본 색입니다.

### <a name="return-value"></a>반환 값

지정 된 텍스트를 그리는 데 테마가 사용 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

테마는 애플리케이션의 비주얼 스타일을 정의합니다. *Htheme* 매개 변수가 NULL 이거나 [Drawthemetextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) 메서드가 지원 되지 않거나 [바탕 화면 창 관리자](/windows/win32/dwm/dwm-overview) (DWM) 컴퍼지션을 사용할 수 없는 경우 테마는 텍스트를 그리는 데 사용 되지 않습니다.

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA:: EnableAccessibilitySupport

Microsoft Active Accessibility 지원을 사용하거나 사용하지 않도록 설정합니다.

```cpp
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 액세스 가능성 지원을 사용 하려면 TRUE로 설정 합니다. 액세스 가능성 지원을 사용 하지 않으려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

Active Accessibility는 프로그램의 방식을 향상시키는 COM 기반의 기술이고 Windows 운영 체제는 보조 기술 제품과 함께 작동합니다. 이는 사용자 인터페이스 요소에 대한 정보를 노출하기 위한 신뢰할 수 있는 메서드를 제공합니다. 그러나 이제부터 Microsoft UI 자동화라고 하는 새로운 내게 필요한 옵션 모델을 사용할 수 있습니다. 두 기술에 대 한 비교는 [UI 자동화 및 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)를 참조 하세요.

[AFX_GLOBAL_DATA:: IsAccessibilitySupport](#isaccessibilitysupport) 메서드를 사용 하 여 Microsoft Active Accessibility 지원이 사용 되는지 여부를 확인 합니다.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a> AFX_GLOBAL_DATA:: ExcludeTag

지정된 버퍼에서 지정된 XML 태그 쌍을 제거합니다.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>매개 변수

*strBuffer*<br/>
진행 텍스트 버퍼입니다.

*lpszTag*<br/>
진행 열기 및 닫기 XML 태그 쌍의 이름입니다.

*strTag*<br/>
제한이 이 메서드가 반환 될 때 *Strtag* 매개 변수는 *lpszTag* 매개 변수로 명명 된 여는 XML 태그와 닫는 XML 태그 사이에 있는 텍스트를 포함 합니다. 선행 또는 후행 공백이 결과에서 잘립니다.

*bIsCharsList*<br/>
진행 *Strtag* 매개 변수의 이스케이프 문자에 대 한 기호를 실제 이스케이프 문자로 변환 하려면 TRUE로 설정 합니다. 변환을 수행 하지 않을 경우 FALSE입니다. 기본값은 FALSE입니다. 자세한 내용은 설명 부분을 참조하세요.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

XML 태그 쌍은 지정 된 버퍼에서 텍스트 실행의 시작과 끝을 나타내는 명명 된 여는 태그와 닫는 태그로 구성 됩니다. *Strbuffer* 매개 변수는 버퍼를 지정 하 고 *lpszTag* 매개 변수는 XML 태그의 이름을 지정 합니다.

다음 표의 기호를 사용 하 여 지정 된 버퍼의 이스케이프 문자 집합을 인코딩합니다. *Strtag* 매개 변수에서 기호를 실제 이스케이프 문자로 변환 하려면 *BISCHARSLIST* 매개 변수에 TRUE를 지정 합니다. 다음 표에서는 [_T ()](../../c-runtime-library/data-type-mappings.md) 매크로를 사용 하 여 기호 및 이스케이프 문자열을 지정 합니다.

|기호|이스케이프 문자|
|------------|----------------------|
|_T (" \\ \t")|_T ("\t")|
|_T (" \\ \n")|_T ("\n")|
|_T (" \\ \r")|_T ("\r")|
|_T (" \\ \b")|_T ("\b")|
|_T ("LT")|_T (" \< ")|
|_T ("GT")|_T (">")|
|_T ("AMP")|_T ("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a> AFX_GLOBAL_DATA:: GetColor

지정된 사용자 인터페이스 요소의 현재 색을 검색합니다.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>매개 변수

*nColor*<br/>
진행 색이 검색 되는 사용자 인터페이스 요소를 지정 하는 값입니다. 유효한 값 목록은 [Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor) 메서드의 *nindex* 매개 변수를 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 사용자 인터페이스 요소의 RGB 색 값입니다. 자세한 내용은 설명 부분을 참조하세요.

### <a name="remarks"></a>설명

*Ncolor* 매개 변수가 범위를 벗어나는 경우 반환 값은 0입니다. 0이 유효한 RGB 값 이기도 하기 때문에이 메서드를 사용 하 여 시스템 색이 현재 운영 체제에서 지원 되는지 여부를 확인할 수 없습니다. 대신, 색이 지원 되지 않는 경우 NULL을 반환 하는 [Getsyscolorbrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) 메서드를 사용 합니다.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA:: GetDirect2dFactory

글로벌 데이터에 저장 된 ID2D1Factory 인터페이스에 대 한 포인터를 반환 합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>반환 값

팩터리 생성에 성공 하는 경우 ID2D1Factory 인터페이스에 대 한 포인터이 고, 만들기가 실패 하거나 현재 작업 시스템에 D2D 지원이 없는 경우 NULL입니다.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a> AFX_GLOBAL_DATA:: GetHandCursor

직접와 비슷하며 식별자가 IDC_HAND 되는 미리 정의 된 커서를 검색 합니다.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>반환 값

손 모양 커서의 핸들입니다.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA:: GetNonClientMetrics

최소화되지 않은 창의 비클라이언트 영역과 관련된 메트릭을 검색합니다.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>매개 변수

*나타납니다*<br/>
[in, out] 최소화 되지 않은 창의 비클라이언트 영역과 관련 된 확장 가능한 메트릭을 포함 하는 [비 client메트릭](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) 구조입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a> AFX_GLOBAL_DATA:: GetTextHeight

현재 글꼴에서 텍스트 문자의 높이를 검색합니다.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>매개 변수

*bHorz*<br/>
진행 텍스트를 가로로 실행할 때 문자 높이를 검색 하려면 TRUE로 설정 합니다. 텍스트가 세로로 실행 될 때 문자 높이를 검색 하려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

Ascender에서 디센더로 측정 되는 현재 글꼴의 높이입니다.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a> AFX_GLOBAL_DATA:: GetWICFactory

글로벌 데이터에 저장 된 IWICImagingFactory 인터페이스에 대 한 포인터를 반환 합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>반환 값

팩터리 생성에 성공 하는 경우 IWICImagingFactory 인터페이스에 대 한 포인터이 고, 만들기가 실패 하거나 현재 작업 시스템에 WIC 지원이 없는 경우 NULL입니다.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a> AFX_GLOBAL_DATA:: GetWriteFactory

글로벌 데이터에 저장 된 IDWriteFactory 인터페이스에 대 한 포인터를 반환 합니다. 인터페이스가 초기화되지 않은 경우 기본 매개 변수와 함께 인터페이스가 생성됩니다.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>반환 값

팩터리 생성에 성공 하는 경우 IDWriteFactory 인터페이스에 대 한 포인터이 고, 만들기가 실패 하거나 현재 작업 시스템에 DirectWrite 지원이 없는 경우 NULL입니다.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a> AFX_GLOBAL_DATA:: InitD2D

D2D, DirectWrite 및 WIC 팩터리를 초기화 합니다. 주 창이 초기화되기 전에 이 메서드를 호출합니다.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>매개 변수

*d2dFactoryType*<br/>
D2D 팩터리의 스레딩 모델 및이 모델에서 만드는 리소스입니다.

*writeFactoryType*<br/>
쓰기 팩터리 개체를 공유할지 아니면 격리할 지를 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

팩터리가 intilalizrd 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a> AFX_GLOBAL_DATA:: Is32BitIcons

미리 정의된 32비트 아이콘이 지원되는지 여부를 나타냅니다.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>반환 값

미리 정의 된 32 비트 아이콘이 지원 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 프레임 워크가 32 비트 기본 제공 아이콘을 지원 하 고, 운영 체제에서 픽셀당 16 비트 이상을 지원 하며, 이미지가 고대비로 표시 되지 않는 경우 TRUE를 반환 합니다.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA:: IsAccessibilitySupport

Microsoft Active Accessibility 지원이 활성화되어 있는지 여부를 나타냅니다.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>반환 값

내게 필요한 옵션 지원 기능이 사용 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Microsoft Active Accessibility는 응용 프로그램에 액세스할 수 있도록 하기 위한 이전 솔루션 이었습니다. Microsoft UI Automation은 Microsoft Windows의 새로운 접근성 모델 이며 보조 기술 제품 및 자동화 된 테스트 도구의 요구를 해결 하기 위한 것입니다.

[AFX_GLOBAL_DATA:: EnableAccessibilitySupport](#enableaccessibilitysupport) 메서드를 사용 하 여 Active Accessibility 지원을 설정 하거나 해제할 수 있습니다.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a> AFX_GLOBAL_DATA:: IsD2DInitialized

D2D가 초기화 되었는지 여부를 확인 합니다.

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>반환 값

D2D가 초기화 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA:: IsDwmCompositionEnabled

Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 메서드를 호출하는 간단한 방법을 제공합니다.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>반환 값

DWM ( [바탕 화면 창 관리자](/windows/win32/dwm/dwm-overview) ) 컴퍼지션을 사용할 수 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA:: IsHighContrastMode

이미지가 현재 고대비로 표시되는지 여부를 나타냅니다.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>반환 값

이미지가 현재 검정색 또는 흰색 고대비 모드로 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

검은색 고대비 모드에서는 조명을 향한 가장자리가 흰색 이며 배경은 검정색입니다. 흰색 고대비 모드에서는 조명을 향한 가장자리가 검정색 이며 배경은 흰색입니다.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA:: IsWindowsLayerSupportAvailable

운영 체제가 계층화된 창을 지원하는지 여부를 나타냅니다.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>반환 값

계층화 된 창이 지원 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

계층화 된 창이 지원 되는 경우 *스마트 도킹* 마커는 계층화 된 창을 사용 합니다.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA:: m_bUseBuiltIn32BitIcons

프레임워크가 미리 정의된 32비트 컬러 아이콘을 사용하는지, 아니면 더 낮은 해상도의 아이콘을 사용하는지를 나타냅니다.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>설명

TRUE 이면 프레임 워크에서 32 비트 색 아이콘을 사용 합니다. FALSE 이면 낮은 해상도 아이콘을 지정 합니다. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 TRUE로 초기화 합니다.

이 멤버는 응용 프로그램을 시작할 때 설정 해야 합니다.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a> AFX_GLOBAL_DATA:: m_bUseSystemFont

시스템 글꼴이 메뉴, 도구 모음 및 리본에 사용되는지 여부를 나타냅니다.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>설명

TRUE 이면 시스템 글꼴을 사용 합니다. 그렇지 않으면 FALSE입니다. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 FALSE로 초기화 합니다.

이 멤버 테스트는 프레임 워크가 사용할 글꼴을 결정 하는 유일한 방법이 아닙니다. `AFX_GLOBAL_DATA::UpdateFonts`또한이 메서드는 기본 및 대체 글꼴을 테스트 하 여 메뉴, 도구 모음 및 리본에 적용 될 수 있는 비주얼 스타일을 결정 합니다.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a> AFX_GLOBAL_DATA:: m_hcurHand

손 모양 커서에 대한 핸들을 저장합니다.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a> AFX_GLOBAL_DATA:: m_hcurStretch

가로 늘이기 커서에 대한 핸들을 저장합니다.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA:: m_hcurStretchVert

세로 늘이기 커서에 대한 핸들을 저장합니다.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a> AFX_GLOBAL_DATA:: m_hiconTool

도구 아이콘에 대한 핸들을 저장합니다.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA:: m_nAutoHideToolBarMargin

가장 왼쪽에 있는 자동 숨기기 도구 모음에서 도킹 막대 왼쪽 까지의 오프셋을 지정 합니다.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>설명

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 4 픽셀로 초기화 합니다.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA:: m_nAutoHideToolBarSpacing

자동 숨기기 도구 모음 사이의 간격을 지정합니다.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>설명

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 14 픽셀로 초기화 합니다.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA:: m_nDragFrameThicknessDock

도킹 된 상태를 나타내는 데 사용 되는 끌기 프레임의 두께를 지정 합니다.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>설명

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 3 픽셀로 초기화 합니다.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA:: m_nDragFrameThicknessFloat

부동 상태를 나타내는 데 사용 되는 끌기 프레임의 두께를 지정 합니다.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>설명

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`생성자는이 멤버를 4 픽셀로 초기화 합니다.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a> AFX_GLOBAL_DATA:: OnSettingChange

데스크톱 메뉴 애니메이션의 현재 상태 및 작업 표시줄 자동 숨기기 기능을 탐지합니다.

```cpp
void OnSettingChange();
```

### <a name="remarks"></a>설명

이 메서드는 프레임 워크 변수를 사용자 데스크톱의 특정 특성 상태로 설정 합니다. 이 메서드는 메뉴 애니메이션, 메뉴 페이드 및 작업 표시줄 자동 숨기기 기능의 현재 상태를 검색 합니다.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a> AFX_GLOBAL_DATA:: RegisterWindowClass

지정된 MFC 창 클래스를 등록합니다.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>매개 변수

*lpszClassNamePrefix*<br/>
진행 등록할 창 클래스의 이름입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하는 경우 등록 된 클래스의 정규화 된 이름입니다. 그렇지 않으면 [리소스 예외가 발생](exception-processing.md#afxthrowresourceexception)합니다.

### <a name="remarks"></a>설명

반환 값은 콜론으로 구분 된 *lpszClassNamePrefix* 매개 변수 문자열 목록 및 현재 응용 프로그램 인스턴스 핸들의 16 진수 텍스트 표현입니다. 응용 프로그램 커서는 식별자가 IDC_ARROW 되는 화살표 커서입니다. 배경 브러시입니다. MFC 창 클래스를 등록 하는 방법에 대 한 자세한 내용은 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)를 참조 하세요.

## <a name="afx_global_dataresume"></a><a name="resume"></a> AFX_GLOBAL_DATA:: Resume

Windows 테마 및 비주얼 스타일을 지원하는 메서드에 액세스하는 내부 함수 포인터를 다시 초기화합니다.

```
BOOL Resume();
```

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다. 디버그 모드에서이 메서드는이 메서드가 실패 한 경우를 어설션 합니다.

### <a name="remarks"></a>설명

이 메서드는 프레임 워크가 [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) 메시지를 받을 때 호출 됩니다.

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a> AFX_GLOBAL_DATA:: SetLayeredAttrib

Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 메서드를 호출하는 간단한 방법을 제공합니다.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>매개 변수

*hwnd*<br/>
진행 계층화 된 창에 대 한 핸들입니다.

*crKey*<br/>
진행 [바탕 화면 창 관리자](/windows/win32/dwm/dwm-overview) 에서 계층화 된 창을 구성 하는 데 사용 하는 투명도 색 키입니다.

*bAlpha*<br/>
진행 계층화 된 창의 불투명도를 설명 하는 데 사용 되는 알파 값입니다.

*dwFlags*<br/>
진행 사용할 메서드 매개 변수를 지정 하는 플래그의 비트 조합 (OR)입니다. *Crkey* 매개 변수를 투명도 색으로 사용 하려면 LWA_COLORKEY를 지정 합니다. *BAlpha* 매개 변수를 사용 하 여 계층화 된 창의 불투명도를 결정 LWA_ALPHA를 지정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a> AFX_GLOBAL_DATA:: SetMenuFont

지정된 논리 글꼴을 만듭니다.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

*lpLogFont*<br/>
진행 글꼴의 특성을 포함 하는 구조체에 대 한 포인터입니다.

*bHorz*<br/>
진행 텍스트를 가로로 실행 하도록 지정 하려면 TRUE로 설정 합니다. 텍스트를 세로로 실행 하도록 지정 하려면 FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다. 디버그 모드에서이 메서드는이 메서드가 실패 한 경우를 어설션 합니다.

### <a name="remarks"></a>설명

이 메서드는 기본 메뉴 항목에 사용 되는 가로 일반 글꼴, 밑줄이 그어진 글꼴 및 굵은 글꼴을 만듭니다. 이 메서드는 필요에 따라 일반 세로 글꼴을 만듭니다. 논리 글꼴에 대 한 자세한 내용은 [Cfont:: create글꼴](../../mfc/reference/cfont-class.md#createfontindirect)을 참조 하십시오.

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a> AFX_GLOBAL_DATA:: UpdateFonts

프레임워크에서 사용하는 논리 글꼴을 다시 초기화합니다.

```cpp
void UpdateFonts();
```

### <a name="remarks"></a>설명

논리 글꼴에 대 한 자세한 내용은을 참조 하십시오 `CFont::CreateFontIndirect` .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a> AFX_GLOBAL_DATA:: UpdateSysColors

프레임워크에서 사용하는 색, 색 농도, 브러시, 펜 및 이미지를 초기화합니다.

```cpp
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a> AFX_GLOBAL_DATA:: bIsWindows7

응용 프로그램이 Windows 7 이상에서 실행 되 고 있는지 여부를 나타냅니다.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA:: clrActiveCaptionGradient

활성 캡션의 그라데이션 색을 지정 합니다. 도킹 창에 일반적으로 사용됩니다.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA:: clrInactiveCaptionGradient

비활성 캡션의 그라데이션 색을 지정합니다. 도킹 창에 일반적으로 사용됩니다.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a> AFX_GLOBAL_DATA:: Getitask바코드 목록

인터페이스에 대 한 포인터를 만들고 글로벌 데이터에 저장 `ITaskBarList` 합니다.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>반환 값

`ITaskbarList`작업 표시줄 목록 개체를 만드는 데 성공 하면 인터페이스에 대 한 포인터입니다. 만들기가 실패 하거나 현재 작업 시스템이 Windows 7 보다 작은 경우 NULL입니다.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA:: GetITaskbarList3

인터페이스에 대 한 포인터를 만들고 글로벌 데이터에 저장 `ITaskBarList3` 합니다.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>반환 값

`ITaskbarList3`작업 표시줄 목록 개체를 만드는 데 성공 하면 인터페이스에 대 한 포인터입니다. 만들기가 실패 하거나 현재 작업 시스템이 Windows 7 보다 작은 경우 NULL입니다.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a> AFX_GLOBAL_DATA:: GetShellAutohideBars

셸 자동 숨기기 막대의 위치를 결정합니다.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>반환 값

자동 숨기기 막대의 위치를 지정 하는 인코딩된 플래그를 포함 하는 정수 값입니다. AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT 값을 결합할 수 있습니다.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA:: ReleaseTaskBarRefs

및 메서드를 통해 얻은 인터페이스를 해제 `GetITaskbarList` `GetITaskbarList3` 합니다.

```cpp
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA:: ShellCreateItemFromParsingName

구문 분석 이름에서 셸 항목 개체를 만들고 초기화합니다.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>매개 변수

*pszPath*<br/>
진행 표시 이름에 대 한 포인터입니다.

*pc*<br/>
구문 분석 작업을 제어 하는 바인드 컨텍스트에 대 한 포인터입니다.

*riid*<br/>
인터페이스 ID에 대 한 참조입니다.

*ppv*<br/>
제한이 이 함수가 반환 될 때 *riid* 에서 요청 된 인터페이스 포인터를 포함 합니다. 이는 일반적으로 `IShellItem` 또는 `IShellItem2` 입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 반환 합니다. 그렇지 않으면 오류 값입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../hierarchy-chart.md)<br/>
[구조체, 스타일, 콜백 및 메시지 맵](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[파트 및 상태](/windows/win32/controls/parts-and-states)<br/>
[nFormat](cdc-class.md#drawtext)<br/>
[메서드의](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[바탕 화면 창 관리자](/windows/win32/dwm/dwm-overview)<br/>
[DWM 컴퍼지션 설정 및 제어](/windows/win32/dwm/composition-ovw)<br/>
[UI 자동화 및 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor 함수](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS 구조](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)

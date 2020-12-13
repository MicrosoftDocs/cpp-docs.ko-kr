---
description: '자세한 정보: 도킹 및 부동 도구 모음'
title: 도구 모음 고정 및 고정 해제
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 0cd4595dcc9353255408ce0bd1d3bb23e9b005f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330306"
---
# <a name="docking-and-floating-toolbars"></a>도구 모음 고정 및 고정 해제

MFC 라이브러리는 도킹 가능한 도구 모음을 지원 합니다. 도킹 가능한 도구 모음을 해당 부모 창에 연결 하거나 도킹할 수 있거나 자체 미니 프레임 창에서 분리 하거나 부동 상태로 만들 수 있습니다. 이 문서에서는 응용 프로그램에서 도킹 가능한 도구 모음을 사용 하는 방법을 설명 합니다.

응용 프로그램 마법사를 사용 하 여 응용 프로그램의 기본 구조를 생성 하는 경우 도킹 가능한 도구 모음을 사용할지 여부를 선택 하 라는 메시지가 표시 됩니다. 기본적으로 응용 프로그램 마법사는 응용 프로그램에 도킹 가능한 도구 모음을 추가 하는 데 필요한 세 가지 작업을 수행 하는 코드를 생성 합니다.

- [프레임 창에서 도킹을 사용 하도록 설정](#_core_enabling_docking_in_a_frame_window)합니다.

- [도구 모음에 대 한 도킹을 사용](#_core_enabling_docking_for_a_toolbar)합니다.

- [도구 모음을 프레임 창에 도킹](#_core_docking_the_toolbar)합니다.

이러한 단계가 없는 경우 응용 프로그램에 표준 도구 모음이 표시 됩니다. 응용 프로그램에서 도킹 가능한 각 도구 모음에 대해 마지막 두 단계를 수행 해야 합니다.

이 문서에서 다루는 다른 항목은 다음과 같습니다.

- [도구 모음 부동](#_core_floating_the_toolbar)

- [동적으로 도구 모음 크기 조정](#_core_dynamically_resizing_the_toolbar)

- [고정 스타일 도구 모음의 줄 바꿈 위치 설정](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

예제는 MFC 일반 샘플 [DOCKTOOL](../overview/visual-cpp-samples.md) 을 참조 하세요.

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a> 프레임 창에서 도킹 사용

프레임 창에 도구 모음을 도킹 하려면 도킹을 허용 하도록 프레임 창 (또는 대상)을 설정 해야 합니다. 이 작업은 [CFrameWnd:: EnableDocking](reference/cframewnd-class.md#enabledocking) 함수를 사용 하 여 수행 됩니다 .이 함수에는 도킹을 허용 하는 프레임 창에서 사용 되는 스타일 비트 집합을 나타내는 *DWORD* 매개 변수 하나를 사용 합니다. 도구 모음이 도킹 되 고 여러 면에 도킹할 수 있는 경우에 전달 된 매개 변수에 표시 되는 면은 `EnableDocking` top, bottom, left, right 순서로 사용 됩니다. 컨트롤 막대를 어디에 나 도킹할 수 있도록 하려면 **CBRS_ALIGN_ANY** 를에 전달 `EnableDocking` 합니다.

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a> 도구 모음에 대 한 도킹 사용

도킹 대상의 준비를 완료 한 후에는 도구 모음 (또는 원본)을 비슷한 방식으로 준비 해야 합니다. 도킹할 각 도구 모음에 대해 [Ccontrolbar:: enabledocking](reference/ccontrolbar-class.md#enabledocking) 를 호출 하 여 도구 모음을 도킹할 대상 쪽을 지정 합니다. 호출에서 지정 된 면 `CControlBar::EnableDocking` 이 프레임 창에서 도킹에 사용할 수 있는 면과 일치 하지 않는 경우 도구 모음은 도킹할 수 없습니다. 부동 도구 모음은 부동 도구 모음으로 유지 되므로 프레임 창에 도킹할 수 없습니다.

원하는 효과가 영구적으로 부동 도구 모음 인 경우 `EnableDocking` 0의 매개 변수를 사용 하 여를 호출 합니다. 그런 다음 [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)를 호출 합니다. 도구 모음은 부동 상태로 유지 되며, 아무 곳에 나 고정할 수 없습니다.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a> 도구 모음 도킹

프레임 워크는 사용자가 도킹을 허용 하는 프레임 창의 측면에서 도구 모음을 삭제 하려고 할 때 [CFrameWnd::D ockControlBar](reference/cframewnd-class.md#dockcontrolbar) 를 호출 합니다.

또한 언제 든 지이 함수를 호출 하 여 컨트롤 막대를 프레임 창에 도킹할 수 있습니다. 일반적으로 초기화 하는 동안 수행 됩니다. 두 개 이상의 도구 모음을 프레임 창의 특정 면에 도킹할 수 있습니다.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a> 도구 모음 부동

프레임 창에서 도킹 가능한 도구 모음을 분리 하는 것을 도구 모음의 부동 이라고 합니다. 이 작업을 수행 하려면 [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar) 를 호출 합니다. 도구 모음을 부동 도구 모음이 가로 또는 세로 인지 여부를 결정 하는 정렬 스타일, 부동 도구 모음을 배치할 위치를 지정 합니다.

사용자가 도구 모음을 도킹 된 위치 밖으로 끌어 도킹을 사용할 수 없는 위치에 놓으면 프레임 워크에서이 함수를 호출 합니다. 이는 프레임 창의 내부 또는 외부에 있을 수 있습니다. 와 마찬가지로 `DockControlBar` 초기화 하는 동안이 함수를 호출할 수도 있습니다.

도킹 가능한 도구 모음의 MFC 구현에서는 도킹 가능한 도구 모음을 지 원하는 일부 응용 프로그램에서 제공 하는 일부 확장 된 기능을 제공 하지 않습니다. 사용자 지정 가능한 도구 모음과 같은 기능은 제공 되지 않습니다.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a> 동적으로 도구 모음 크기 조정

Visual C++ 버전 4.0을 통해 응용 프로그램 사용자가 부동 도구 모음을 동적으로 크기를 조정할 수 있습니다. 일반적으로 도구 모음은 긴 선형 셰이프를 가로로 표시 합니다. 그러나 도구 모음의 방향과 셰이프를 변경할 수 있습니다. 예를 들어 사용자가 프레임 창의 세로 가장자리 중 하나에 대해 도구 모음을 도킹 하면 모양이 세로 레이아웃으로 변경 됩니다. 또한 도구 모음을 여러 행의 단추를 포함 하는 사각형으로 변형할 수 있습니다.

다음과 같습니다.

- 동적 크기 조정을 도구 모음 특징으로 지정 합니다.

- 고정 크기 조정을 도구 모음 특징으로 지정 합니다.

이러한 지원을 제공 하기 위해 [CToolBar:: Create](reference/ctoolbar-class.md#create) 멤버 함수를 호출 하는 데 사용할 수 있는 두 가지 새 도구 모음 스타일이 있습니다. 관련 토폴로지는 다음과 같습니다.

- **CBRS_SIZE_DYNAMIC** 컨트롤 막대는 동적입니다.

- **CBRS_SIZE_FIXED** 컨트롤 표시줄이 고정 되어 있습니다.

크기 동적 스타일을 사용 하면 사용자가 도구 모음이 부동 상태 이지만 도킹 되는 동안에는 도구 모음의 크기를 조정할 수 있습니다. 도구 모음은 사용자가 가장자리를 끌 때 셰이프를 변경 해야 하는 위치를 "래핑합니다".

크기 고정 스타일은 각 열에서 단추의 위치를 수정 하 여 도구 모음의 줄 바꿈 상태를 유지 합니다. 응용 프로그램의 사용자가 도구 모음 셰이프를 변경할 수 없습니다. 도구 모음은 단추 사이의 구분 기호 위치와 같은 지정 된 위치에 배치 됩니다. 이 셰이프는 도구 모음이 도킹 되었는지 아니면 부동 도구 인지에 관계 없이 유지 됩니다. 단추의 여러 열이 있는 고정 된 색상표가 적용 됩니다.

[CToolBar:: GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle) 을 사용 하 여 도구 모음에 있는 단추에 대 한 상태 및 스타일을 반환할 수도 있습니다. 단추의 스타일은 단추가 표시 되는 방법 및 사용자 입력에 응답 하는 방법을 결정 합니다. 상태는 단추가 래핑된 상태 인지 여부를 나타냅니다.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Fixed-Style 도구 모음에 대 한 줄 바꿈 위치 설정

크기가 고정 된 도구 모음의 경우 도구 모음이 줄 바꿈되는 도구 모음 단추 인덱스를 지정 합니다. 다음 코드는 주 프레임 창의 재정의에서이 작업을 수행 하는 방법을 보여 줍니다 `OnCreate` .

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 일반 샘플 [DOCKTOOL](../overview/visual-cpp-samples.md) 는 [ccontrolbar](reference/ccontrolbar-class.md) 및 [CToolBar](reference/ctoolbar-class.md) 클래스의 멤버 함수를 사용 하 여 도구 모음의 동적 레이아웃을 관리 하는 방법을 보여 줍니다. 파일 EDITBAR를 참조 하세요. DOCKTOOL의 CPP.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [도구 모음 기본 사항](toolbar-fundamentals.md)

- [도구 모음 도구 설명](toolbar-tool-tips.md)

- [이전 도구 모음 사용](using-your-old-toolbars.md)

## <a name="see-also"></a>참고 항목

[MFC 도구 모음 구현](mfc-toolbar-implementation.md)

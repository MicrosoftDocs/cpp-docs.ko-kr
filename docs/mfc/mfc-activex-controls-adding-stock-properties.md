---
description: '자세히 알아보기: MFC ActiveX 컨트롤: 스톡 속성 추가'
title: 'MFC ActiveX 컨트롤: 스톡 속성 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 1bcfc69fe5fd7cdcadcd641fb831c07bde79bbfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202823"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 컨트롤: 스톡 속성 추가

스톡 속성은 클래스에 의해 이미 구현 된다는 점에서 사용자 지정 속성과 다릅니다 `COleControl` . `COleControl` 컨트롤의 공용 속성을 지 원하는 미리 정의 된 멤버 함수를 포함 합니다. 일부 공용 속성에는 컨트롤의 캡션과 전경색 및 배경색이 포함 됩니다. 다른 스톡 속성에 대 한 자세한 내용은이 문서의 뒷부분에 나오는 [속성 추가 마법사에서 지 원하는 스톡 속성](#_core_stock_properties_supported_by_classwizard) 을 참조 하세요. 스톡 속성의 디스패치 맵 항목에는 항상 DISP_STOCKPROP 접두사가 붙습니다.

이 문서에서는 속성 추가 마법사를 사용 하 여 ActiveX 컨트롤에 스톡 속성 (이 경우 캡션)을 추가 하 고 결과 코드를 수정 하는 방법을 설명 합니다. 다룰 주제는 다음과 같습니다.

- [속성 추가 마법사를 사용 하 여 스톡 속성 추가](#_core_using_classwizard_to_add_a_stock_property)

- [스톡 속성에 대 한 속성 추가 마법사 변경 내용](#_core_classwizard_changes_for_stock_properties)

- [속성 추가 마법사에서 지 원하는 스톡 속성](#_core_stock_properties_supported_by_classwizard)

- [스톡 속성 및 알림](#_core_stock_properties_and_notification)

- [색 속성](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 사용자 지정 컨트롤에는 일반적으로 Top, Left, Width, Height, Align, Tag, Name, TabIndex, TabStop, Parent 등의 속성이 있습니다. 그러나 ActiveX 컨트롤 컨테이너는 이러한 컨트롤 속성을 구현 하는 일을 담당 하므로 ActiveX 컨트롤은 이러한 속성을 지원 하지 않습니다.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a> 속성 추가 마법사를 사용 하 여 스톡 속성 추가

속성에 대 한 지원이에서 자동으로 처리 되므로 스톡 속성을 추가 하려면 사용자 지정 속성을 추가 하는 것 보다 더 작은 코드가 필요 `COleControl` 합니다. 다음 절차에서는 스톡 Caption 속성을 ActiveX 컨트롤 프레임 워크에 추가 하는 방법을 보여 주고 다른 스톡 속성을 추가 하는 데에도 사용할 수 있습니다. 캡션에 대해 선택한 스톡 속성 이름을 대체 합니다.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 스톡 Caption 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가** 를 클릭 합니다.

   그러면 [속성 추가 마법사](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)가 열립니다.

1. **속성 이름** 상자에서 **캡션** 을 클릭 합니다.

1. **Finish** 를 클릭합니다.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a> 스톡 속성에 대 한 속성 추가 마법사 변경 내용

`COleControl`는 스톡 속성을 지원 하므로 속성 추가 마법사는 클래스 선언을 변경 하지 않으며 디스패치 맵에 속성을 추가 합니다. 속성 추가 마법사는 구현 ()에 있는 컨트롤의 디스패치 맵에 다음 줄을 추가 합니다. CPP) 파일:

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

다음 줄이 컨트롤의 인터페이스 설명 ()에 추가 됩니다. IDL) 파일:

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

이 줄에서는 Caption 속성에 특정 ID를 할당 합니다. 속성은 바인딩 가능 하 고 값을 수정 하기 전에 데이터베이스에서 사용 권한을 요청 합니다.

이렇게 하면 컨트롤의 사용자가 Caption 속성을 사용할 수 있습니다. 스톡 속성의 값을 사용 하려면 기본 클래스의 멤버 변수 또는 멤버 함수에 액세스 `COleControl` 합니다. 이러한 멤버 변수 및 멤버 함수에 대 한 자세한 내용은 다음 섹션인 속성 추가 마법사에서 지 원하는 스톡 속성을 참조 하세요.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a> 속성 추가 마법사에서 지 원하는 스톡 속성

`COleControl`클래스는 9 개의 스톡 속성을 제공 합니다. 속성 추가 마법사를 사용 하 여 원하는 속성을 추가할 수 있습니다.

|속성|디스패치 맵 항목|값에 액세스 하는 방법|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ()|로 액세스할 수 있는 값 `m_sAppearance` 입니다.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ()|을 호출 하 여 액세스할 수 있는 값 `GetBackColor` 입니다.|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ()|로 액세스할 수 있는 값 `m_sBorderStyle` 입니다.|
|`Caption`|DISP_STOCKPROP_CAPTION ()|을 호출 하 여 액세스할 수 있는 값 `InternalGetText` 입니다.|
|`Enabled`|DISP_STOCKPROP_ENABLED ()|로 액세스할 수 있는 값 `m_bEnabled` 입니다.|
|`Font`|DISP_STOCKPROP_FONT ()|[MFC ActiveX 컨트롤:](mfc-activex-controls-using-fonts.md) 사용을 위한 글꼴 사용 문서를 참조 하세요.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ()|을 호출 하 여 액세스할 수 있는 값 `GetForeColor` 입니다.|
|`hWnd`|DISP_STOCKPROP_HWND ()|로 액세스할 수 있는 값 `m_hWnd` 입니다.|
|`Text`|DISP_STOCKPROP_TEXT ()|을 호출 하 여 액세스할 수 있는 값 `InternalGetText` 입니다. 이 속성은 `Caption` 속성 이름을 제외 하 고와 동일 합니다.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ()|또는로 액세스할 수 있는 값 `m_lReadyState``GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a> 스톡 속성 및 알림

대부분의 스톡 속성에는 재정의할 수 있는 알림 함수가 있습니다. 예를 들어, `BackColor` 속성이 변경 될 때마다 `OnBackColorChanged` 함수 (컨트롤 클래스의 멤버 함수)가 호출 됩니다. 기본 구현 (의)은를 `COleControl` 호출 `InvalidateControl` 합니다. 이러한 상황에 대 한 응답으로 추가 작업을 수행 하려는 경우이 함수를 재정의 합니다.

## <a name="color-properties"></a><a name="_core_color_properties"></a> 색 속성

`ForeColor`컨트롤을 그릴 때 스톡 및 `BackColor` 속성 또는 고유한 사용자 지정 색 속성을 사용할 수 있습니다. Color 속성을 사용 하려면 [COleControl:: TranslateColor](reference/colecontrol-class.md#translatecolor) 멤버 함수를 호출 합니다. 이 함수의 매개 변수는 color 속성 값과 색상표 핸들 (선택 사항)입니다. 반환 값은 및와 같은 GDI 함수에 전달할 수 있는 **Colorref** 값입니다 `SetTextColor` `CreateSolidBrush` .

스톡 및 속성의 색 값 `ForeColor` 은 `BackColor` `GetForeColor` 각각 또는 함수를 호출 하 여 액세스 됩니다 `GetBackColor` .

다음 예제에서는 컨트롤을 그릴 때 이러한 두 색 속성을 사용 하는 방법을 보여 줍니다. 속성을 사용 하는 메서드 및 속성을 사용 하는를 호출 하 여 임시 **Colorref** 변수 및 개체를 초기화 합니다 `CBrush` `TranslateColor` . `ForeColor` `BackColor` `CBrush`그런 다음 임시 개체는 컨트롤의 사각형을 그리는 데 사용 되 고 텍스트 색은 속성을 사용 하 여 설정 됩니다 `ForeColor` .

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 속성](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)

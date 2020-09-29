---
title: 'MFC ActiveX 컨트롤: 글꼴 사용'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: 02c52d2544afdc9d13fc3ec67ad9eed757a3f277
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499690"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 컨트롤: 글꼴 사용

ActiveX 컨트롤에서 텍스트를 표시 하는 경우 font 속성을 변경 하 여 컨트롤 사용자가 텍스트 모양을 변경 하도록 허용할 수 있습니다. 글꼴 속성은 font 개체로 구현 되며 스톡 또는 custom 이라는 두 가지 형식 중 하나일 수 있습니다. 스톡 글꼴 속성은 속성 추가 마법사를 사용 하 여 추가할 수 있는 미리 구현 된 글꼴 속성입니다. 사용자 지정 글꼴 속성은 미리 구현 되지 않으며 컨트롤 개발자는 속성의 동작 및 사용을 결정 합니다.

이 문서는 다음 항목을 설명합니다.

- [스톡 글꼴 속성 사용](#_core_using_the_stock_font_property)

- [컨트롤에서 사용자 지정 글꼴 속성 사용](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a> 스톡 글꼴 속성 사용

스톡 글꼴 속성은 [COleControl](reference/colecontrol-class.md)클래스에서 미리 구현 됩니다. 또한 표준 글꼴 속성 페이지를 사용 하 여 사용자가 글꼴 개체의 이름, 크기 및 스타일과 같은 다양 한 특성을 변경할 수 있습니다.

의 [Getfont](reference/colecontrol-class.md#getfont), [Setfont](reference/colecontrol-class.md#setfont)및 [internalgetfont](reference/colecontrol-class.md#internalgetfont) 함수를 통해 font 개체에 액세스 `COleControl` 합니다. 컨트롤 사용자는 `GetFont` 및 함수를 통해 `SetFont` 다른 Get/Set 속성과 동일한 방식으로 글꼴 개체에 액세스 합니다. 컨트롤 내에서 font 개체에 대 한 액세스가 필요한 경우 함수를 사용 `InternalGetFont` 합니다.

[MFC ActiveX 컨트롤: 속성](mfc-activex-controls-properties.md)에서 설명한 대로 [속성 추가 마법사](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)를 사용 하 여 스톡 속성을 쉽게 추가할 수 있습니다. Font 속성을 선택 하면 속성 추가 마법사에서 스톡 글꼴 항목을 컨트롤의 디스패치 맵에 자동으로 삽입 합니다.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 스톡 글꼴 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가**를 클릭 합니다.

   그러면 속성 추가 마법사가 열립니다.

1. **속성 이름** 상자에서 **글꼴**을 클릭 합니다.

1. **Finish**를 클릭합니다.

속성 추가 마법사는 컨트롤 클래스 구현 파일에 있는 컨트롤의 디스패치 맵에 다음 줄을 추가 합니다.

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

또한 속성 추가 마법사는 컨트롤에 다음 줄을 추가 합니다. IDL 파일:

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

스톡 Caption 속성은 스톡 글꼴 속성 정보를 사용 하 여 그릴 수 있는 텍스트 속성의 예입니다. 스톡 Caption 속성을 컨트롤에 추가 하면 스톡 글꼴 속성에 사용 된 것과 비슷한 단계가 사용 됩니다.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 스톡 Caption 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가**를 클릭 합니다.

   그러면 속성 추가 마법사가 열립니다.

1. **속성 이름** 상자에서 **캡션**을 클릭 합니다.

1. **Finish**를 클릭합니다.

속성 추가 마법사는 컨트롤 클래스 구현 파일에 있는 컨트롤의 디스패치 맵에 다음 줄을 추가 합니다.

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a> OnDraw 함수 수정

의 기본 구현에서는 `OnDraw` 컨트롤에 표시 되는 모든 텍스트에 대해 Windows 시스템 글꼴을 사용 합니다. 즉, `OnDraw` 장치 컨텍스트에서 글꼴 개체를 선택 하 여 코드를 수정 해야 합니다. 이렇게 하려면 다음 예제와 같이 [COleControl:: SelectStockFont](reference/colecontrol-class.md#selectstockfont) 를 호출 하 고 컨트롤의 장치 컨텍스트를 전달 합니다.

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

`OnDraw`글꼴 개체를 사용 하도록 함수를 수정한 후에는 컨트롤의 스톡 글꼴 속성의 특징에 맞게 컨트롤의 텍스트가 표시 됩니다.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a> 컨트롤에서 사용자 지정 글꼴 속성 사용

스톡 글꼴 속성 외에도 ActiveX 컨트롤은 사용자 지정 글꼴 속성을 가질 수 있습니다. 사용자 지정 글꼴 속성을 추가 하려면 다음을 수행 해야 합니다.

- 속성 추가 마법사를 사용 하 여 사용자 지정 글꼴 속성을 구현 합니다.

- [글꼴 알림을 처리](#_core_processing_font_notifications)하 고 있습니다.

- [새 글꼴 알림 인터페이스를 구현](#_core_implementing_a_new_font_notification_interface)합니다.

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a> 사용자 지정 글꼴 속성 구현

사용자 지정 글꼴 속성을 구현 하려면 속성 추가 마법사를 사용 하 여 속성을 추가한 다음 코드를 수정 합니다. 다음 섹션에서는 예제 컨트롤에 사용자 지정 속성을 추가 하는 방법에 대해 설명 합니다 `HeadingFont` .

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 사용자 지정 글꼴 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가**를 클릭 합니다.

   그러면 속성 추가 마법사가 열립니다.

1. **속성 이름** 상자에 속성의 이름을 입력 합니다. 이 예에서는 **HeadingFont**를 사용 합니다.

1. **구현 형식**에서 **Get/Set 메서드**를 클릭합니다.

1. **속성 형식** 상자에서 **IDispatch** <strong>\*</strong> 속성의 형식에 대해 IDispatch를 선택 합니다.

1. **Finish**를 클릭합니다.

속성 추가 마법사는 `HeadingFont` 클래스 및 샘플에 사용자 지정 속성을 추가 하는 코드를 만듭니다 `CSampleCtrl` . IDL 파일. `HeadingFont`는 Get/Set 속성 형식 이므로 속성 추가 마법사는 `CSampleCtrl` DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) 매크로 항목을 포함 하도록 클래스의 디스패치 맵을 수정 합니다.

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 매크로는 `HeadingFont` 속성 이름을 해당 하는 클래스의 `CSampleCtrl` Get 및 Set 메서드와 연결 `GetHeadingFont` `SetHeadingFont` 합니다. 또한 속성 값의 형식이 지정 됩니다. 이 경우 VT_FONT 합니다.

또한 속성 추가 마법사는 컨트롤 헤더 파일 ()에 선언을 추가 합니다. H) 및 함수에 대 한 `GetHeadingFont` `SetHeadingFont` 및 함수 템플릿을 제어 구현 파일 ()에 추가 합니다. CPP):

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

마지막으로 속성 추가 마법사가 컨트롤을 수정 합니다. 속성에 대 한 항목을 추가 하 여 IDL 파일을 추가 합니다 `HeadingFont` .

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>컨트롤 코드 수정

이제 `HeadingFont` 컨트롤에 속성을 추가 했으므로 새 속성을 완벽 하 게 지원 하도록 컨트롤 헤더 및 구현 파일을 변경 해야 합니다.

컨트롤 헤더 파일 (. H)로 보호 된 멤버 변수의 다음 선언을 추가 합니다.

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

제어 구현 파일 (. CPP)에서 다음을 수행 합니다.

- 컨트롤 생성자의 *m_fontHeading* 를 초기화 합니다.

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 글꼴의 기본 특성을 포함 하는 정적 글꼴의 DESC 구조체를 선언 합니다.

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 컨트롤 `DoPropExchange` 멤버 함수에서 함수에 대 한 호출을 추가 `PX_Font` 합니다. 이렇게 하면 사용자 지정 글꼴 속성의 초기화 및 지 속성이 제공 됩니다.

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 컨트롤 `GetHeadingFont` 멤버 함수 구현을 마칩니다.

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 컨트롤 `SetHeadingFont` 멤버 함수 구현을 마칩니다.

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 컨트롤 `OnDraw` 멤버 함수를 수정 하 여 이전에 선택한 글꼴을 저장할 변수를 정의 합니다.

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- `OnDraw`글꼴을 사용할 위치에 다음 줄을 추가 하 여 컨트롤 멤버 함수를 수정 하 여 장치 컨텍스트에 사용자 지정 글꼴을 선택 합니다.

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- `OnDraw`글꼴이 사용 된 후 다음 줄을 추가 하 여 이전 글꼴을 장치 컨텍스트로 다시 선택 하도록 컨트롤 멤버 함수를 수정 합니다.

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

사용자 지정 글꼴 속성을 구현한 후에는 컨트롤 사용자가 컨트롤의 현재 글꼴을 변경할 수 있도록 표준 글꼴 속성 페이지가 구현 되어야 합니다. 표준 글꼴 속성 페이지의 속성 페이지 ID를 추가 하려면 BEGIN_PROPPAGEIDS 매크로 뒤에 다음 줄을 삽입 합니다.

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

또한 BEGIN_PROPPAGEIDS 매크로의 count 매개 변수를 하나씩 증가 시켜야 합니다. 다음 줄에서는 이 작업을 보여 줍니다.

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

이러한 변경 내용을 적용 한 후에는 전체 프로젝트를 다시 빌드하여 추가 기능을 통합 합니다.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a> 글꼴 알림 처리

대부분의 경우 컨트롤은 글꼴 개체의 특성이 수정 된 시기를 알고 있어야 합니다. 각 글꼴 개체는에서 구현 하는 인터페이스의 멤버 함수를 호출 하 여 변경 될 때 알림을 제공할 수 `IFontNotification` `COleControl` 있습니다.

컨트롤이 스톡 글꼴 속성을 사용 하는 경우 해당 알림은 `OnFontChanged` 의 멤버 함수에 의해 처리 됩니다 `COleControl` . 사용자 지정 글꼴 속성을 추가 하는 경우 동일한 구현을 사용 하도록 설정할 수 있습니다. 이전 섹션의 예제에서는 *m_fontHeading* 멤버 변수를 초기화할 때 &*m_xFontNotification* 를 전달 하 여이를 수행 했습니다.

![여러 글꼴 개체 인터페이스 구현](../mfc/media/vc373q1.gif "여러 글꼴 개체 인터페이스 구현") <br/>
여러 글꼴 개체 인터페이스 구현

위의 그림에서 실선은 두 글꼴 개체가 모두 동일한 구현을 사용 하 고 있음을 보여 줍니다 `IFontNotification` . 이렇게 하면 변경 된 글꼴을 구분 하려고 할 때 문제가 발생할 수 있습니다.

컨트롤의 글꼴 개체 알림을 구분 하는 한 가지 방법은 `IFontNotification` 컨트롤의 각 글꼴 개체에 대해 별도의 인터페이스 구현을 만드는 것입니다. 이 기법을 사용 하면 최근에 수정한 글꼴을 사용 하는 문자열만 업데이트 하 여 그리기 코드를 최적화할 수 있습니다. 다음 섹션에서는 두 번째 Font 속성에 대해 별도의 알림 인터페이스를 구현 하는 데 필요한 단계를 보여 줍니다. 두 번째 font 속성은 `HeadingFont` 이전 섹션에서 추가 된 속성으로 간주 됩니다.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a> 새 글꼴 알림 인터페이스 구현

두 개 이상의 글꼴에 대 한 알림을 구분 하려면 컨트롤에 사용 된 각 글꼴에 대해 새 알림 인터페이스를 구현 해야 합니다. 다음 섹션에서는 컨트롤 헤더 및 구현 파일을 수정 하 여 새 글꼴 알림 인터페이스를 구현 하는 방법을 설명 합니다.

### <a name="additions-to-the-header-file"></a>헤더 파일에 대 한 추가

컨트롤 헤더 파일 (. H), 클래스 선언에 다음 줄을 추가 합니다.

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

그러면 라는 인터페이스의 구현이 만들어집니다 `IPropertyNotifySink` `HeadingFontNotify` . 이 새 인터페이스에는 라는 메서드가 포함 되어 있습니다 `OnChanged` .

### <a name="additions-to-the-implementation-file"></a>구현 파일에 추가

컨트롤 생성자에서 제목 글꼴을 초기화 하는 코드에서 &*m_xFontNotification* 를 &*m_xHeadingFontNotify*로 변경 합니다. 다음 코드를 추가합니다.

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef` `Release` 인터페이스의 및 메서드는 `IPropertyNotifySink` ActiveX 컨트롤 개체에 대 한 참조 횟수를 추적 합니다. 컨트롤에서 인터페이스 포인터에 대 한 액세스 권한을 얻는 경우이 컨트롤은 `AddRef` 를 호출 하 여 참조 횟수를 늘립니다. 컨트롤이 포인터를 사용 하 여 완료 되 면 `Release` `GlobalFree` 전역 메모리 블록을 해제 하기 위해 호출 될 수 있는 것과 동일한 방식으로를 호출 합니다. 이 인터페이스에 대 한 참조 횟수가 0이 되 면 인터페이스 구현을 해제할 수 있습니다. 이 예제에서 함수는 `QueryInterface` `IPropertyNotifySink` 특정 개체의 인터페이스에 대 한 포인터를 반환 합니다. 이 함수를 사용 하면 ActiveX 컨트롤에서 개체를 쿼리하여 개체에서 지 원하는 인터페이스를 확인할 수 있습니다.

프로젝트를 변경한 후에는 프로젝트를 다시 빌드하고 테스트 컨테이너를 사용 하 여 인터페이스를 테스트 합니다. 테스트 컨테이너에 액세스하는 방법은 [테스트 컨테이너로 속성 및 이벤트 테스트](testing-properties-and-events-with-test-container.md) 를 참조하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: ActiveX 컨트롤에서 그림 사용](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 컨트롤: 스톡 속성 페이지 사용](mfc-activex-controls-using-stock-property-pages.md)

---
description: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에서 그림 사용에 대해 자세히 알아보세요.'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에서 그림 사용하기'
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 9c9989be7503eb449b969fbbf37d92f26c165131
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133083"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤에서 그림 사용하기

이 문서에서는 일반적인 그림 유형 및 ActiveX 컨트롤에서 구현하는 방법을 설명합니다. 다룰 주제는 다음과 같습니다.

- [사용자 지정 그림 속성 개요](#_core_overview_of_custom_picture_properties)

- [ActiveX 컨트롤에서 사용자 지정 그림 속성 구현](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [컨트롤 프로젝트에 대한 추가](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a> 사용자 지정 그림 속성 개요

그림 형식은 일부 ActiveX 컨트롤에 공통적으로 적용되는 형식 그룹 중 하나입니다. 그림 형식은 메타 파일, 비트맵 또는 아이콘을 처리하며 사용자가 ActiveX 컨트롤에 표시할 그림을 지정할 수 있게 합니다. 사용자 지정 그림 속성은 그림 개체 및 컨트롤 사용자가 그림 속성에 액세스할 수 있게 하는 Get/Set 함수를 사용하여 구현됩니다. 컨트롤 사용자는 스톡 그림 속성 페이지를 사용하여 사용자 지정 그림 속성에 액세스합니다.

표준 그림 형식뿐 아니라 글꼴 및 색 형식도 사용할 수 있습니다. ActiveX 컨트롤에서 표준 글꼴 형식을 사용하는 방법에 대한 자세한 내용은 [MFC ActiveX 컨트롤: 글꼴 사용](mfc-activex-controls-using-fonts.md)문서를 참조하세요.

ActiveX 컨트롤 클래스는 컨트롤 내에서 그림 속성을 구현하는 데 사용할 수 있는 여러 구성 요소를 제공합니다. 이러한 구성 요소는 다음과 같습니다.

- [CPictureHolder](reference/cpictureholder-class.md) 클래스.

   이 클래스를 사용하면 사용자 지정 그림 속성이 표시하는 항목에 대한 그림 개체 및 기능에 쉽게 액세스할 수 있습니다.

- Get/Set 함수로 구현된 **LPPICTUREDISP** 형식의 속성 지원.

   클래스 뷰를 사용하여 그림 형식을 지원하는 사용자 지정 속성을 빠르게 추가할 수 있습니다. 클래스 뷰를 사용하여 ActiveX 컨트롤 속성을 추가하는 방법에 대한 자세한 내용은 [MFC ActiveX 컨트롤: 속성](mfc-activex-controls-properties.md)문서를 참조하세요.

- 컨트롤의 그림 속성을 조작하는 속성 페이지.

   이 속성 페이지는 ActiveX 컨트롤에서 사용할 수 있는 스톡 속성 페이지 그룹의 일부입니다. ActiveX 컨트롤 속성 페이지에 대한 자세한 내용은 [MFC ActiveX 컨트롤: 스톡 속성 페이지 사용](mfc-activex-controls-using-stock-property-pages.md)을 참조하세요.

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> ActiveX 컨트롤에서 사용자 지정 그림 속성 구현

이 섹션에 설명된 단계를 완료하면 컨트롤이 해당 사용자가 선택한 그림을 표시할 수 있습니다. 사용자는 현재 그림을 표시하며 다른 그림을 선택할 수 있게 해주는 찾아보기 단추가 있는 속성 페이지를 사용하여 표시된 그림을 변경할 수 있습니다.

사용자 지정 그림 속성은 다른 속성의 구현에 사용되는 것과 비슷한 프로세스를 사용하여 구현되며, 주요 차이점은 사용자 지정 속성이 그림 형식을 지원해야 한다는 것입니다. 그림 속성의 항목은 ActiveX 컨트롤로 그려야 하기 때문에 완벽하게 구현하려면 속성을 추가 및 수정하는 여러 작업을 수행해야 합니다.

사용자 지정 그림 속성을 구현하려면 다음을 수행해야 합니다.

- [컨트롤 프로젝트에 코드 추가](#_core_additions_to_your_control_project).

   표준 그림 속성 페이지 ID, `CPictureHolder`형식의 데이터 멤버, Get/Set 구현이 있는 **LPPICTUREDISP** 형식의 사용자 지정 속성을 추가해야 합니다.

- [컨트롤 클래스의 여러 함수 수정](#_core_modifications_to_your_control_project).

   ActiveX 컨트롤 그리기를 담당하는 여러 함수가 수정됩니다.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a> 컨트롤 프로젝트에 추가

표준 그림 속성 페이지의 속성 페이지 ID를 추가 하려면 컨트롤 구현 파일 ()의 BEGIN_PROPPAGEIDS 매크로 뒤에 다음 줄을 삽입 합니다. CPP):

[!code-cpp[NVC_MFC_AxPic#1](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

또한 BEGIN_PROPPAGEIDS 매크로의 count 매개 변수를 하나씩 증가 시켜야 합니다. 다음 줄에서는 이 작업을 보여 줍니다.

[!code-cpp[NVC_MFC_AxPic#2](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

컨트롤 클래스에 `CPictureHolder` 데이터 멤버를 추가하려면 컨트롤 헤더 파일(.H)에서 컨트롤 클래스 선언의 보호된 섹션 아래에 다음 줄을 삽입합니다.

[!code-cpp[NVC_MFC_AxPic#3](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

데이터 멤버의 이름을 *m_pic* 하는 것은 필요 하지 않습니다. 모든 이름에는 충분 합니다.

다음에는 그림 형식을 지원하는 사용자 지정 속성을 추가합니다.

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용하여 사용자 지정 그림 속성을 추가하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 선택한 다음 **속성 추가** 를 선택합니다.

1. **속성 이름** 상자에 속성 이름을 입력합니다. 예제의 경우 이 절차에서 `ControlPicture` 를 사용합니다.

1. **속성 유형** 상자에서 속성 유형에 대해 **IPictureDisp** 를 선택 <strong>\*</strong> 합니다.

1. **구현 형식** 에서 **Get/Set 메서드** 를 클릭합니다.

1. Get 및 Set 함수의 고유 이름을 입력하거나 기본 이름을 적용합니다. 이 예제에서는 기본 이름 `GetControlPicture` 및 `SetControlPicture` 를 사용합니다.

1. **Finish** 를 클릭합니다.

속성 추가 마법사가 컨트롤 헤더(.H) 파일의 디스패치 맵 주석 사이에 다음 코드를 추가합니다.

[!code-cpp[NVC_MFC_AxPic#4](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

또한 컨트롤 구현(.CPP) 파일의 디스패치 맵에 다음 코드가 삽입되었습니다.

[!code-cpp[NVC_MFC_AxPic#5](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

속성 추가 마법사는 컨트롤 구현 파일에 다음 두 개의 스텁 함수도 추가합니다.

[!code-cpp[NVC_MFC_AxPic#6](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> 사용자 컨트롤 클래스 및 함수 이름은 위의 예제와 다를 수 있습니다.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a> 컨트롤 프로젝트 수정

컨트롤 프로젝트에 필요한 항목을 추가한 후 ActiveX 컨트롤의 렌더링에 영향을 주는 여러 함수를 수정해야 합니다. 이러한 함수, `OnResetState`, `OnDraw`및 사용자 지정 그림 속성의 Get/Set 함수는 컨트롤 구현 파일에 있습니다. 이 예제에서 컨트롤 클래스는를 호출 하 고 `CSampleCtrl` , `CPictureHolder` 데이터 멤버를 *m_pic* 이라고 하며, 사용자 지정 그림 속성 이름은 `ControlPicture` 입니다.

컨트롤 `OnResetState` 함수에서 `COleControl::OnResetState`호출 뒤에 다음과 같은 선택적 줄을 추가합니다.

[!code-cpp[NVC_MFC_AxPic#7](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

이렇게 하면 컨트롤의 그림이 빈 그림으로 설정됩니다.

그림을 제대로 그리려면 컨트롤 [함수에서](reference/cpictureholder-class.md#render) CPictureHolder::Render `OnDraw` 를 호출합니다. 다음 예제와 유사하게 함수를 수정합니다.

[!code-cpp[NVC_MFC_AxPic#8](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

컨트롤 사용자 지정 그림 속성의 Get 함수에서 다음 줄을 추가합니다.

[!code-cpp[NVC_MFC_AxPic#9](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

컨트롤 사용자 지정 그림 속성의 Set 함수에서 다음 줄을 추가합니다.

[!code-cpp[NVC_MFC_AxPic#10](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

디자인 타임에 추가한 정보가 런타임에 표시되도록 그림 속성을 영구적으로 설정해야 합니다. `COleControl`파생 클래스의 `DoPropExchange` 함수에 다음 줄을 추가합니다.

[!code-cpp[NVC_MFC_AxPic#11](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> 사용자 클래스 및 함수 이름은 위의 예제와 다를 수 있습니다.

수정 작업을 완료한 후 프로젝트를 다시 빌드하여 사용자 지정 그림 속성의 새 기능을 통합하고 테스트 컨테이너를 사용하여 새 속성을 테스트합니다. 테스트 컨테이너에 액세스하는 방법은 [테스트 컨테이너로 속성 및 이벤트 테스트](testing-properties-and-events-with-test-container.md) 를 참조하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 글꼴 사용](mfc-activex-controls-using-fonts.md)<br/>
[MFC ActiveX 컨트롤: 속성 페이지](mfc-activex-controls-property-pages.md)

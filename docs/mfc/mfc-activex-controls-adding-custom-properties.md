---
title: 'MFC ActiveX 컨트롤: 사용자 지정 속성 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: af1ca2d63abcb112bfe1e7d7538dbf70fb817ae5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503883"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 컨트롤: 사용자 지정 속성 추가

사용자 지정 속성은 클래스에서 아직 구현 되지 않은 사용자 지정 속성은 스톡 속성과 다릅니다 `COleControl` . 사용자 지정 속성은 컨트롤을 사용 하 여 ActiveX 컨트롤의 특정 상태나 모양을 프로그래머에 게 노출 하는 데 사용 됩니다.

이 문서에서는 속성 추가 마법사를 사용 하 여 ActiveX 컨트롤에 사용자 지정 속성을 추가 하 고 결과 코드 수정을 설명 하는 방법을 설명 합니다. 다룰 주제는 다음과 같습니다.

- [속성 추가 마법사를 사용 하 여 사용자 지정 속성 추가](#_core_using_classwizard_to_add_a_custom_property)

- [사용자 지정 속성에 대 한 속성 추가 마법사 변경 내용](#_core_classwizard_changes_for_custom_properties)

사용자 지정 속성은 네 가지 구현으로, 멤버 변수, 알림, Get/Set 메서드 및 매개 변수화 된 멤버 변수를 제공 합니다.

- 멤버 변수 구현

   이 구현은 컨트롤 클래스의 멤버 변수로 서 속성의 상태를 나타냅니다. 속성 값이 변경 되는 시기를 알 필요가 없는 경우 멤버 변수 구현을 사용 합니다. 이 구현에서는 세 가지 형식 중 가장 적은 수의 속성 지원 코드를 만듭니다. 멤버 변수 구현에 대 한 디스패치 맵 항목 매크로를 [DISP_PROPERTY](reference/dispatch-maps.md#disp_property)합니다.

- 알림 구현이 포함 된 멤버 변수

   이 구현은 멤버 변수와 속성 추가 마법사에서 만든 알림 함수로 구성 됩니다. 알림 함수는 속성 값이 변경 된 후 프레임 워크에서 자동으로 호출 됩니다. 속성 값이 변경 된 후 알림을 받아야 할 경우 알림 구현에 멤버 변수를 사용 합니다. 이 구현에는 함수 호출이 필요 하므로 시간이 더 필요 합니다. 이 구현에 대 한 디스패치 맵 항목 매크로가 [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify)되었습니다.

- Get/Set 메서드 구현

   이 구현은 컨트롤 클래스의 멤버 함수 쌍으로 구성 됩니다. Get/Set 메서드 구현은 컨트롤의 사용자가 속성의 현재 값을 요청 하는 경우 Get 멤버 함수를 자동으로 호출 하 고, 컨트롤의 사용자가 해당 속성을 변경 하도록 요청할 때 Set 멤버 함수를 호출 합니다. 런타임에 속성의 값을 계산 하 고, 실제 속성을 변경 하기 전에 컨트롤의 사용자가 전달한 값의 유효성을 검사 하거나, 읽기 또는 쓰기 전용 속성 형식을 구현 해야 할 경우이 구현을 사용 합니다. 이 구현에 대 한 디스패치 맵 항목 매크로가 [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)되었습니다. 다음 섹션에서는 [속성 추가 마법사를 사용 하 여 사용자 지정 속성을 추가](#_core_using_classwizard_to_add_a_custom_property)하 고, CircleOffset 사용자 지정 속성을 사용 하 여이 구현을 보여 줍니다.

- 매개 변수가 있는 구현

   매개 변수가 있는 구현은 속성 추가 마법사에서 지원 됩니다. 매개 변수가 있는 속성 (속성 배열이 라고도 함)을 사용 하 여 컨트롤의 단일 속성을 통해 값 집합에 액세스할 수 있습니다. 이 구현에 대 한 디스패치 맵 항목 매크로가 DISP_PROPERTY_PARAM 되었습니다. 이 형식을 구현 하는 방법에 대 한 자세한 내용은 ActiveX 컨트롤: 고급 토픽 문서에서 [매개 변수화 된 속성 구현](mfc-activex-controls-advanced-topics.md) 을 참조 하세요.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a> 속성 추가 마법사를 사용 하 여 사용자 지정 속성 추가

다음 절차에서는 Get/Set 메서드 구현을 사용 하는 사용자 지정 속성인 CircleOffset를 추가 하는 방법을 보여 줍니다. CircleOffset 사용자 지정 속성을 사용 하면 컨트롤의 경계 사각형 중심에서 원을 오프셋할 수 있습니다. Get/Set 메서드 이외의 구현으로 사용자 지정 속성을 추가 하는 절차는 매우 유사 합니다.

이와 동일한 절차를 사용 하 여 원하는 다른 사용자 지정 속성을 추가할 수도 있습니다. CircleOffset 속성 이름 및 매개 변수를 사용자 지정 속성 이름으로 대체 합니다.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 CircleOffset 사용자 지정 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가**를 클릭 합니다.

   그러면 [속성 추가 마법사](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)가 열립니다.

1. **속성 이름** 상자에 *CircleOffset*을 입력 합니다.

1. **구현 형식**에서 **Get/Set 메서드**를 클릭합니다.

1. **속성 유형** 상자에서를 선택 **`short`** 합니다.

1. Get 및 Set 함수의 고유 이름을 입력 하거나 기본 이름을 적용 합니다.

1. **Finish**를 클릭합니다.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a> 사용자 지정 속성에 대 한 속성 추가 마법사 변경 내용

CircleOffset 사용자 지정 속성을 추가 하면 속성 추가 마법사에서 헤더를 변경 합니다. H) 및 구현 (. CPP) 파일을 관리 합니다.

에 추가 되는 줄은 다음과 같습니다. H 파일은 및 라는 두 개의 함수를 선언 합니다 `GetCircleOffset` `SetCircleOffset` .

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

다음 줄이 컨트롤의에 추가 됩니다. IDL 파일:

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

이 줄은 속성 추가 마법사의 메서드 및 속성 목록에 있는 메서드 위치에서 가져온 특정 ID 번호를 CircleOffset 속성에 할당 합니다.

또한 다음 줄은의 디스패치 맵에 추가 됩니다. CircleOffset 속성을 컨트롤의 두 처리기 함수에 매핑하는 컨트롤 클래스의 CPP 파일):

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

마지막으로 `GetCircleOffset` 및 `SetCircleOffset` 함수의 구현이 컨트롤의 끝에 추가 됩니다. CPP 파일. 대부분의 경우 Get 함수를 수정 하 여 속성의 값을 반환 합니다. Set 함수는 일반적으로 속성을 변경 하기 전이나 후에 실행 해야 하는 코드를 포함 합니다.

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

속성 추가 마법사는 Set 함수의 본문에 [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)에 대 한 호출을 자동으로 추가 합니다. 이 함수를 호출 하면 컨트롤이 수정 된 상태로 표시 됩니다. 컨트롤이 수정 된 경우 컨테이너를 저장할 때 새 상태가 저장 됩니다. 이 함수는 컨트롤의 영구 상태에서 속성이 변경 되 고 값이 변경 될 때마다 호출 됩니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 속성](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)

---
description: '자세한 정보: MFC ActiveX 컨트롤: 사용자 지정 메서드 추가'
title: 'MFC ActiveX 컨트롤: 사용자 지정 메서드 추가'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: a7ac7ad1f1635976b3190c84b02b40bf73551e70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202953"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 컨트롤: 사용자 지정 메서드 추가

사용자 지정 메서드는에서 아직 구현 되지 않은 스톡 메서드와 다릅니다 `COleControl` . 컨트롤에 추가 하는 각 사용자 지정 메서드에 대 한 구현을 제공 해야 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

ActiveX 컨트롤 사용자는 언제 든 지 사용자 지정 메서드를 호출 하 여 컨트롤별 작업을 수행할 수 있습니다. 사용자 지정 메서드의 디스패치 맵 항목은 DISP_FUNCTION 형식입니다.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a> 메서드 추가 마법사를 사용 하 여 사용자 지정 메서드 추가

다음 절차에서는 사용자 지정 메서드 PtInCircle를 ActiveX 컨트롤의 기본 코드에 추가 하는 방법을 보여 줍니다. PtInCircle는 컨트롤에 전달 된 좌표가 원 내부 또는 외부에 있는지 여부를 확인 합니다. 이 동일한 절차를 사용 하 여 다른 사용자 지정 메서드를 추가할 수도 있습니다. PtInCircle 메서드 이름 및 매개 변수에 대 한 사용자 지정 메서드 이름 및 매개 변수를 대체 합니다.

> [!NOTE]
> 이 예에서는 아티클 이벤트의 함수를 사용 합니다 `InCircle` . 이 함수에 대 한 자세한 내용은 [MFC Activex 컨트롤: Activex 컨트롤에 사용자 지정 이벤트 추가](mfc-activex-controls-adding-custom-events.md)문서를 참조 하세요.

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>메서드 추가 마법사를 사용 하 여 PtInCircle 사용자 지정 메서드를 추가 하려면

1. 컨트롤의 프로젝트를 로드 합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **메서드 추가** 를 클릭 합니다.

   그러면 메서드 추가 마법사가 열립니다.

1. **메서드 이름** 상자에 *PtInCircle* 을 입력 합니다.

1. **내부 이름** 상자에 메서드의 내부 함수 이름을 입력 하거나 기본값 (이 경우 *PtInCircle*)을 사용 합니다.

1. **반환 형식** 상자에서 메서드의 반환 형식에 대 한 **VARIANT_BOOL** 를 클릭 합니다.

1. 매개 변수 **형식** 및 **매개 변수 이름** 컨트롤을 사용 하 여 *xCoord* (형식 *OLE_XPOS_PIXELS*) 라는 매개 변수를 추가 합니다.

1. 매개 변수 **형식** 및 **매개 변수 이름** 컨트롤을 사용 하 여 *yCoord* (형식 *OLE_YPOS_PIXELS*) 라는 매개 변수를 추가 합니다.

1. **Finish** 를 클릭합니다.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a> 사용자 지정 메서드에 대 한 메서드 추가 마법사 변경 내용

사용자 지정 메서드를 추가 하면 메서드 추가 마법사에서 컨트롤 클래스 헤더 (. H) 및 구현 (. CPP) 파일. 다음 줄은 컨트롤 클래스 헤더 ()의 디스패치 맵 선언에 추가 됩니다. H) 파일:

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

이 코드는 라는 디스패치 메서드 처리기를 선언 `PtInCircle` 합니다. 외부 이름을 사용 하 여 컨트롤 사용자가이 함수를 호출할 수 있습니다 `PtInCircle` .

다음 줄이 컨트롤의에 추가 됩니다. IDL 파일:

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

이 줄에서는 메서드를 메서드 `PtInCircle` 추가 마법사의 메서드 및 속성 목록에 있는 메서드의 위치인 메서드에 특정 ID 번호를 할당 합니다. 메서드 추가 마법사를 사용 하 여 사용자 지정 메서드를 추가 했으므로 해당 항목이 프로젝트에 자동으로 추가 되었습니다. IDL 파일.

또한 구현에 있는 다음 줄 (. CPP) 컨트롤 클래스의 파일을 컨트롤의 디스패치 맵에 추가 합니다.

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION 매크로는 메서드를 `PtInCircle` 컨트롤의 처리기 함수에 매핑하고,는 `PtInCircle` **VARIANT_BOOL** 반환 형식을 선언 하 고, **VTS_XPOS_PIXELS** 형식의 두 매개 변수와에 전달 되는 **VTS_YPOSPIXELS** 를 선언 `PtInCircle` 합니다.

마지막으로, 메서드 추가 마법사는 `CSampleCtrl::PtInCircle` 컨트롤 구현 ()의 맨 아래에 스텁 함수를 추가 합니다. CPP) 파일입니다. `PtInCircle`가 앞에서 설명한 대로 작동 하려면 다음과 같이 수정 해야 합니다.

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[클래스 뷰 및 개체 브라우저 아이콘](/visualstudio/ide/class-view-and-object-browser-icons)

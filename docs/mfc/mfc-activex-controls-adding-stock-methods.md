---
description: '자세한 정보: MFC ActiveX 컨트롤: 스톡 메서드 추가'
title: 'MFC ActiveX 컨트롤: 스톡 메서드 추가'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 1bd176c81a3c97ad5530a9b1971656e5204fe407
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202875"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 컨트롤: 스톡 메서드 추가

스톡 메서드는 이미 [COleControl](reference/colecontrol-class.md)클래스에서 구현 된다는 점에서 사용자 지정 메서드와 다릅니다. 예를 들어,에는 `COleControl` 컨트롤에 대 한 Refresh 메서드를 지 원하는 미리 정의 된 멤버 함수가 포함 되어 있습니다. 이 스톡 메서드에 대 한 디스패치 맵 항목이 DISP_STOCKFUNC_REFRESH 되었습니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

`COleControl` 에서는 두 가지 스톡 메서드인 DoClick 및 새로 고침을 지원 합니다. 컨트롤의 모양을 즉시 업데이트 하기 위해 컨트롤의 사용자가 새로 고침을 호출 합니다. DoClick을 호출 하 여 컨트롤의 Click 이벤트를 발생 시킵니다.

|메서드|디스패치 맵 항목|의견|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ()**|Click 이벤트를 발생 시킵니다.|
|`Refresh`|**DISP_STOCKPROP_REFRESH ()**|컨트롤의 모양을 즉시 업데이트 합니다.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a> 메서드 추가 마법사를 사용 하 여 스톡 메서드 추가

[메서드 추가 마법사](../ide/adding-a-method-visual-cpp.md#add-method-wizard)를 사용 하 여 스톡 메서드를 간단히 추가할 수 있습니다. 다음 절차에서는 MFC ActiveX 컨트롤 마법사를 사용 하 여 만든 컨트롤에 Refresh 메서드를 추가 하는 방법을 보여 줍니다.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>메서드 추가 마법사를 사용 하 여 스톡 Refresh 메서드를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **메서드 추가** 를 클릭 합니다.

   그러면 메서드 추가 마법사가 열립니다.

1. **메서드 이름** 상자에서 **새로 고침** 을 클릭 합니다.

1. **Finish** 를 클릭합니다.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a> 스톡 메서드에 대 한 메서드 추가 마법사 변경 내용

스톡 Refresh 메서드는 컨트롤의 기본 클래스에서 지원 되기 때문에 **메서드 추가 마법사** 는 컨트롤의 클래스 선언을 어떤 식으로든 변경 하지 않습니다. 컨트롤의 디스패치 맵과에 메서드에 대 한 항목을 추가 합니다. IDL 파일. 다음 줄은 해당 구현 ()에 있는 컨트롤의 디스패치 맵에 추가 됩니다. CPP) 파일:

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

이렇게 하면 컨트롤의 사용자가 새로 고침 메서드를 사용할 수 있습니다.

다음 줄이 컨트롤의에 추가 됩니다. IDL 파일:

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

이 줄은 Refresh 메서드에 특정 ID 번호를 할당 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)

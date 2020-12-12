---
description: '자세한 정보: MFC ActiveX 컨트롤: Windows 컨트롤 서브클래싱'
title: 'MFC ActiveX 컨트롤: Windows 컨트롤 서브클래싱'
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: f3ea0e1af9860ca4585fe31817c689b75241d0f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164109"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 컨트롤: Windows 컨트롤 서브클래싱

이 문서에서는 ActiveX 컨트롤을 만들기 위해 공용 Windows 컨트롤을 서브클래싱하는 프로세스를 설명 합니다. 기존 Windows 컨트롤을 서브클래싱하 면 ActiveX 컨트롤을 신속 하 게 개발할 수 있습니다. 새 컨트롤에는 마우스 클릭에 대 한 그리기 및 응답과 같은 서브클래싱된 Windows 컨트롤의 기능이 있습니다. MFC ActiveX 컨트롤 샘플 [단추](../overview/visual-cpp-samples.md) 는 Windows 컨트롤을 서브클래싱 하는 예제입니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

Windows 컨트롤을 서브 클래스 하려면 다음 작업을 완료 합니다.

- [COleControl의 IsSubclassedControl 및 PreCreateWindow 멤버 함수를 재정의 합니다.](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [OnDraw 멤버 함수 수정](#_core_modifying_the_ondraw_member_function)

- [컨트롤에 반영 된 OCM (ActiveX 컨트롤 메시지)를 처리 합니다.](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > **컨트롤 설정** 페이지의 **부모 창 클래스 선택** 드롭다운 목록을 사용 하 여 서브클래싱된 컨트롤을 선택 하는 경우 ActiveX 컨트롤 마법사에서 대부분의 작업을 수행 합니다.

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> IsSubclassedControl 및 PreCreateWindow 재정의

및를 재정의 하려면 `PreCreateWindow` `IsSubclassedControl` 다음 코드 줄을 **`protected`** 컨트롤 클래스 선언의 섹션에 추가 합니다.

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

제어 구현 파일 (. CPP)에서 다음 코드 줄을 추가 하 여 재정의 된 두 함수를 구현 합니다.

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

이 예제에서는 Windows 단추 컨트롤이에 지정 되어 `PreCreateWindow` 있습니다. 그러나 표준 Windows 컨트롤은 서브클래싱 할 수 있습니다. 표준 Windows 컨트롤에 대 한 자세한 내용은 [컨트롤](controls-mfc.md)을 참조 하세요.

Windows 컨트롤을 서브클래싱 할 때 컨트롤의 창을 만들 때 사용할 특정 창 스타일 (WS_) 또는 WS_EX_ (확장 창 스타일) 플래그를 지정 해야 할 수 있습니다. `PreCreateWindow` `cs.style` 및 구조 필드를 수정 하 여 멤버 함수에서 이러한 매개 변수에 대 한 값을 설정할 수 있습니다 `cs.dwExStyle` . 클래스에 의해 설정 되는 기본 플래그를 유지 하려면 **또는** 작업을 사용 하 여 이러한 필드를 수정 해야 합니다 `COleControl` . 예를 들어 컨트롤이 BUTTON 컨트롤을 서브클래싱 하 고 컨트롤을 확인란으로 표시 하려면 다음 코드 줄을의 구현에서 `CSampleCtrl::PreCreateWindow` return 문 앞에 삽입 합니다.

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

이 작업은 BS_CHECKBOX 스타일 플래그를 추가 하는 반면 클래스의 기본 스타일 플래그 (WS_CHILD)는 `COleControl` 그대로 유지 합니다.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a> OnDraw 멤버 함수 수정

서브클래싱된 컨트롤이 해당 Windows 컨트롤과 동일한 모양을 유지 하도록 하려면 `OnDraw` 다음 예제와 같이 컨트롤의 멤버 함수는 멤버 함수에 대 한 호출만 포함 해야 합니다 `DoSuperclassPaint` .

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint`에 의해 구현 되는 멤버 함수는 `COleControl` Windows 컨트롤의 창 프로시저를 사용 하 여 경계 사각형 내의 지정 된 장치 컨텍스트에서 컨트롤을 그립니다. 이렇게 하면 컨트롤이 활성화 되지 않은 경우에도 표시 됩니다.

> [!NOTE]
> `DoSuperclassPaint`멤버 함수는 장치 컨텍스트가 WM_PAINT 메시지의 *wParam* 로 전달 되도록 허용 하는 컨트롤 형식 에서만 작동 합니다. 여기에는 스크롤 막대 및 단추와 같은 표준 Windows 컨트롤과 모든 공용 컨트롤이 포함 됩니다. 이 동작을 지원 하지 않는 컨트롤의 경우 비활성 컨트롤을 제대로 표시 하기 위해 사용자 고유의 코드를 제공 해야 합니다.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a> 리플렉션된 창 메시지 처리

Windows 컨트롤은 일반적으로 특정 창 메시지를 부모 창으로 보냅니다. WM_COMMAND와 같은 이러한 메시지 중 일부는 사용자의 동작에 대 한 알림을 제공 합니다. WM_CTLCOLOR와 같은 다른 항목은 부모 창에서 정보를 가져오는 데 사용 됩니다. ActiveX 컨트롤은 일반적으로 다른 방법으로 부모 창과 통신 합니다. 알림은 이벤트를 발생 시키는 이벤트를 발생 시켜 전달 되 고, 컨트롤 컨테이너에 대 한 정보는 컨테이너의 앰비언트 속성에 액세스 하 여 얻습니다. 이러한 통신 기술이 존재 하기 때문에 ActiveX 컨트롤 컨테이너는 컨트롤에서 보낸 창 메시지를 처리할 수 없습니다.

컨테이너가 서브클래싱된 Windows 컨트롤에서 보낸 창 메시지를 받지 않도록 하려면 `COleControl` 컨트롤의 부모 역할을 하는 추가 창을 만듭니다. 이러한 추가 창인 "반영자"는 Windows 컨트롤을 서브클래싱하 고 컨트롤 창과 크기 및 위치가 같은 ActiveX 컨트롤에 대해서만 만들어집니다. 리플렉터 창은 특정 창 메시지를 가로채서 컨트롤로 다시 보냅니다. 그러면 해당 창 프로시저의 컨트롤이 ActiveX 컨트롤에 적절 한 작업 (예: 이벤트 실행)을 수행 하 여 이러한 리플렉션된 메시지를 처리할 수 있습니다. 가로채기 된 windows 메시지 및 해당 리플렉션된 메시지의 목록은 [리플렉션된 창 메시지 id](reflected-window-message-ids.md) 를 참조 하십시오.

ActiveX 컨트롤 컨테이너는 메시지 리플렉션 자체를 수행 하도록 디자인 될 수 있으므로,이를 통해 `COleControl` 리플렉터 창을 만들고 서브클래싱된 Windows 컨트롤에 대 한 런타임 오버 헤드를 줄일 필요가 없습니다. `COleControl`**TRUE** 값을 가진 MessageReflect 앰비언트 속성을 확인 하 여 컨테이너에서이 기능을 지원 하는지 여부를 검색 합니다.

리플렉션된 창 메시지를 처리 하려면 컨트롤 메시지 맵에 항목을 추가 하 고 처리기 함수를 구현 합니다. 반영 된 메시지는 Windows에서 정의한 표준 메시지 집합의 일부가 아니므로 클래스 뷰는 이러한 메시지 처리기를 추가 하는 것을 지원 하지 않습니다. 그러나 처리기를 수동으로 추가 하는 것은 어려운 일입니다.

리플렉션된 창 메시지에 대 한 메시지 처리기를 수동으로 추가 하려면 다음을 수행 합니다.

- 컨트롤 클래스에서 H 파일, 처리기 함수를 선언 합니다. 함수는 **LRESULT** 의 반환 형식 및 두 개의 매개 변수를 사용 해야 합니다. 여기에는 **WPARAM** 및 **LPARAM** 형식이 있습니다. 예를 들어:

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- 컨트롤 클래스에서 .CPP 파일에서 메시지 맵에 ON_MESSAGE 항목을 추가 합니다. 이 항목의 매개 변수는 메시지 식별자와 처리기 함수의 이름 이어야 합니다. 예를 들어:

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- 에도 있습니다. CPP 파일 `OnOcmCommand` . 리플렉션 메시지를 처리 하는 멤버 함수를 구현 합니다. *WParam* 및 *lParam* 매개 변수는 원래 창 메시지와 동일 합니다.

반영 된 메시지를 처리 하는 방법에 대 한 예제는 MFC ActiveX 컨트롤 샘플 [단추](../overview/visual-cpp-samples.md)를 참조 하세요. `OnOcmCommand`BN_CLICKED 알림 코드를 검색 하 고 이벤트를 발생 (전송) 하 여 응답 하는 처리기를 보여 줍니다 `Click` .

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)

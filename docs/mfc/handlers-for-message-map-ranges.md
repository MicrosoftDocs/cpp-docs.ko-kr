---
description: '자세한 정보: Message-Map 범위에 대 한 처리기'
title: 메시지 맵 범위에 대한 처리기
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: 1b0f829a4c75aa8ee6148bdf3e96f6886ab07aba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248920"
---
# <a name="handlers-for-message-map-ranges"></a>메시지 맵 범위에 대한 처리기

이 문서에서는 하나의 메시지를 하나의 함수에만 매핑하는 대신 단일 메시지 처리기 함수에 메시지 범위를 매핑하는 방법을 설명 합니다.

정확히 동일한 방법으로 둘 이상의 메시지 또는 컨트롤 알림을 처리 해야 하는 경우가 있습니다. 이러한 시간에는 모든 메시지를 단일 처리기 함수에 매핑할 수 있습니다. 메시지 맵 범위를 사용 하면 연속 된 메시지 범위에 대해이 작업을 수행할 수 있습니다.

- 명령 Id의 범위를 다음에 매핑할 수 있습니다.

  - 명령 처리기 함수입니다.

  - 명령 업데이트 처리기 함수입니다.

- 컨트롤 Id 범위에 대 한 컨트롤 알림 메시지를 메시지 처리기 함수에 매핑할 수 있습니다.

이 문서에서 다루는 항목은 다음과 같습니다.

- [메시지 맵 항목 작성](#_core_writing_the_message.2d.map_entry)

- [처리기 함수 선언](#_core_declaring_the_handler_function)

- [명령 Id 범위에 대 한 예제](#_core_example_for_a_range_of_command_ids)

- [컨트롤 Id 범위에 대 한 예제](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a> Message-Map 항목 작성

안에. 다음 예제와 같이 .CPP 파일에서 메시지 맵 항목을 추가 합니다.

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

메시지 맵 항목은 다음 항목으로 구성 됩니다.

- 메시지 맵 범위 매크로:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 매크로에 대 한 매개 변수:

  처음 두 매크로는 세 개의 매개 변수를 사용 합니다.

  - 범위를 시작 하는 명령 ID입니다.

  - 범위를 종료 하는 명령 ID입니다.

  - 메시지 처리기 함수의 이름입니다.

  명령 Id의 범위는 연속적 이어야 합니다.

  세 번째 매크로 인는 `ON_CONTROL_RANGE` **EN_CHANGE** 와 같은 컨트롤 알림 메시지와 같은 추가 첫 번째 매개 변수를 사용 합니다.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a> 처리기 함수 선언

에 처리기 함수 선언을 추가 합니다. H 파일. 다음 코드는 아래와 같이 표시 되는 모양을 보여 줍니다.

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

단일 명령에 대 한 처리기 함수는 일반적으로 매개 변수를 사용 하지 않습니다. 업데이트 처리기 함수를 제외 하 고, 메시지 맵 범위에 대 한 처리기 함수에는 **UINT** 형식의 추가 매개 변수 *nID* 가 필요 합니다. 이 매개 변수는 첫 번째 매개 변수입니다. 추가 매개 변수는 사용자가 실제로 선택한 명령을 지정 하는 데 필요한 추가 명령 ID를 수용 합니다.

처리기 함수를 업데이트 하기 위한 매개 변수 요구 사항에 대 한 자세한 내용은 [명령 id의 범위 예](#_core_example_for_a_range_of_command_ids)를 참조 하세요.

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a> 명령 Id 범위에 대 한 예제

범위를 사용할 수 있는 경우 한 가지 예로 MFC 샘플 [HIERSVR](../overview/visual-cpp-samples.md)의 Zoom 명령과 같은 명령을 처리 하는 것입니다. 이 명령은 보기를 확대 하 여 보통 크기의 25%와 300% 사이에서 크기를 조정 합니다. HIERSVR의 뷰 클래스는 범위를 사용 하 여 다음과 유사한 메시지 맵 항목으로 확대/축소 명령을 처리 합니다.

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

메시지 맵 항목을 작성 하는 경우 다음을 지정 합니다.

- 연속 범위를 시작 하 고 종료 하는 두 개의 명령 Id입니다.

   여기서는 **ID_VIEW_ZOOM25** 하 고 **ID_VIEW_ZOOM300** 합니다.

- 명령에 대 한 처리기 함수의 이름입니다.

   여기서는 `OnZoom` 입니다.

함수 선언은 다음과 같습니다.

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

업데이트 처리기 함수의 경우에도 매우 유용 하 게 사용할 수 있습니다. `ON_UPDATE_COMMAND_UI`여러 명령에 대 한 처리기를 작성 하 고 동일한 코드를 반복 해 서 작성 하거나 복사 하는 것이 매우 일반적입니다. 해결 방법은 매크로를 사용 하 여 일련의 명령 Id를 하나의 업데이트 처리기 함수에 매핑하는 것입니다 `ON_UPDATE_COMMAND_UI_RANGE` . 명령 Id는 연속 범위를 형성 해야 합니다. 예제는 `OnUpdateZoom` `ON_UPDATE_COMMAND_UI_RANGE` HIERSVR 샘플의 뷰 클래스에서 처리기 및 해당 메시지 맵 항목을 참조 하세요.

단일 명령의 업데이트 처리기 함수는 일반적으로 형식의 단일 매개 변수 *pCmdUI* 을 사용 `CCmdUI*` 합니다. 처리기 함수와 달리 메시지 맵 범위에 대 한 업데이트 처리기 함수에는 **UINT** 형식의 추가 매개 변수 *nID* 가 필요 하지 않습니다. 사용자가 실제로 선택한 명령을 지정 하는 데 필요한 명령 ID는 개체에 있습니다 `CCmdUI` .

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a> 컨트롤 Id 범위에 대 한 예제

또 다른 흥미로운 사례는 컨트롤 Id 범위에 대 한 컨트롤 알림 메시지를 단일 처리기에 매핑하는 것입니다. 사용자가 단추를 10 개 이상 클릭할 수 있다고 가정 합니다. 하나의 처리기에 10 개의 단추를 모두 매핑하려면 메시지 맵 항목은 다음과 같습니다.

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

메시지 맵에 매크로를 작성 하는 경우 `ON_CONTROL_RANGE` 다음을 지정 합니다.

- 특정 컨트롤 알림 메시지입니다.

   **BN_CLICKED** 입니다.

- 연속 된 컨트롤 범위와 연결 된 컨트롤 ID 값입니다.

   여기에는 **IDC_BUTTON1** 및 **IDC_BUTTON10** 있습니다.

- 메시지 처리기 함수의 이름입니다.

   여기서는 `OnButtonClicked` 입니다.

처리기 함수를 작성 하는 경우 다음과 같이 추가 **UINT** 매개 변수를 지정 합니다.

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`단일 **BN_CLICKED** 메시지에 대 한 처리기는 매개 변수를 사용 하지 않습니다. 단추 범위에 대 한 동일한 처리기는 하나의 **UINT** 를 사용 합니다. 추가 매개 변수를 사용 하면 **BN_CLICKED** 메시지 생성을 담당 하는 특정 컨트롤을 식별할 수 있습니다.

예제에 표시 된 코드는 일반적으로 메시지 범위 내에서로 전달 된 값을 변환 하 고이에 대 한 것을 어설션 합니다. **`int`** 그런 다음 클릭 한 단추에 따라 몇 가지 작업을 수행할 수 있습니다.

## <a name="see-also"></a>참고 항목

[메시지 처리기 함수 선언](declaring-message-handler-functions.md)

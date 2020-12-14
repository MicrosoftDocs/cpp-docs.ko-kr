---
description: '자세한 정보: 메시지 맵 (MFC)'
title: 메시지 맵(MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 7647104d62cbbf10271ddb9e7c781da0049985f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219358"
---
# <a name="message-maps-mfc"></a>메시지 맵(MFC)

이 참조 섹션에서는 모든 [메시지 매핑 매크로](../../mfc/reference/message-map-macros-mfc.md) 및 모든 [CWnd](../../mfc/reference/cwnd-class.md) 메시지 맵 항목과 해당 멤버 함수 프로토타입을 나열 합니다.

|범주|설명|
|--------------|-----------------|
|\_명령 메시지 처리기에서|`WM_COMMAND`사용자 메뉴 선택 또는 메뉴 선택 키로 생성 된 메시지를 처리 합니다.|
|[자식 창 알림 메시지 처리기](../../mfc/reference/child-window-notification-message-handlers.md)|자식 창에서 알림 메시지를 처리 합니다.|
|[WM_ 메시지 처리기](../../mfc/reference/handlers-for-wm-messages.md)|`WM_`와 같은 메시지를 처리 `WM_PAINT` 합니다.|
|[사용자 정의 메시지 처리기](../../mfc/reference/user-defined-handlers.md)|사용자 정의 메시지를 처리 합니다.|

이 참조에서 사용 되는 용어 및 규칙에 대 한 설명은 [메시지 맵 상호 참조를 사용 하는 방법](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)을 참조 하세요.

Windows는 메시지 기반 운영 체제 이므로 Windows 환경에 대 한 프로그래밍의 많은 부분에는 메시지 처리가 포함 됩니다. 키 입력 이나 마우스 클릭 등의 이벤트가 발생할 때마다 응용 프로그램으로 메시지가 전송 된 후 이벤트를 처리 해야 합니다.

MFC 라이브러리는 메시지 기반 프로그래밍에 최적화 된 프로그래밍 모델을 제공 합니다. 이 모델에서 "메시지 맵"은 특정 클래스에 대해 다양 한 메시지를 처리할 함수를 지정 하는 데 사용 됩니다. 메시지 맵은 함수에서 처리할 메시지를 지정 하는 하나 이상의 매크로를 포함 합니다. 예를 들어 매크로를 포함 하는 메시지 맵은 `ON_COMMAND` 다음과 같이 표시 될 수 있습니다.

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND`매크로는 메뉴, 단추 및 액셀러레이터 키에 의해 생성 된 명령 메시지를 처리 하는 데 사용 됩니다. [매크로](../../mfc/reference/message-map-macros-mfc.md) 를 사용 하 여 다음을 매핑할 수 있습니다.

## <a name="windows-messages"></a>Windows 메시지

- 컨트롤 알림

- 사용자 정의 메시지

## <a name="command-messages"></a>명령 메시지

- 등록 된 사용자 정의 메시지

- 사용자 인터페이스 업데이트 메시지

## <a name="ranges-of-messages"></a>메시지 범위

- 명령

- 처리기 메시지 업데이트

- 컨트롤 알림

메시지 맵 매크로는 중요 하지만 일반적으로 직접 사용할 필요는 없습니다. 이는 [클래스 마법사](mfc-class-wizard.md) 가 메시지 처리 함수를 메시지에 연결 하는 데 사용할 때 소스 파일에 메시지 맵 항목을 자동으로 만들기 때문입니다. 메시지 맵 항목을 편집 하거나 추가 하려고 할 때마다 클래스 마법사를 사용할 수 있습니다.

> [!NOTE]
> 클래스 마법사는 메시지 맵 범위를 지원 하지 않습니다. 이러한 메시지 맵 항목을 직접 작성 해야 합니다.

그러나 메시지 맵은 MFC 라이브러리의 중요 한 부분입니다. 사용자가 수행 하는 작업을 이해 하 고 설명서가 제공 됩니다.

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

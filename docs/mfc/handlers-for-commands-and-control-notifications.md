---
description: '자세한 정보: 명령 및 컨트롤 알림에 대 한 처리기'
title: 명령 및 컨트롤 알림에 대한 처리기
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 1e5e3284d5898d1e6349765dc7a1bcdc864c80ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189186"
---
# <a name="handlers-for-commands-and-control-notifications"></a>명령 및 컨트롤 알림에 대한 처리기

명령 또는 컨트롤 알림 메시지에 대 한 기본 처리기가 없습니다. 따라서 이러한 종류의 메시지에 대 한 처리기의 이름을 지정 하는 규칙에 의해서만 바인딩됩니다. 명령 또는 컨트롤 알림을 처리기에 매핑하면 [클래스 마법사](reference/mfc-class-wizard.md) 에서 명령 ID 또는 컨트롤 알림 코드를 기반으로 이름을 제안 합니다. 제안 된 이름을 그대로 적용 하거나 변경 하거나 바꿀 수 있습니다.

규칙은 표시 하는 사용자 인터페이스 개체에 대해 두 범주 모두에서 처리기의 이름을 표시 하는 것을 제안 합니다. 따라서 편집 메뉴의 잘라내기 명령에 대 한 처리기의 이름을 지정할 수 있습니다.

[!code-cpp[NVC_MFCMessageHandling#4](codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

잘라내기 명령은 응용 프로그램에서 일반적으로 구현 되기 때문에 프레임 워크는 **ID_EDIT_CUT** 으로 cut 명령의 명령 ID를 기본적으로 합니다. 미리 정의 된 모든 명령 Id 목록은 AFXRES.H 파일을 참조 하세요. 자세한 내용은 [표준 명령](standard-commands.md)을 참조 하세요.

또한 규칙은 "내 단추" 라는 레이블이 지정 된 단추의 **BN_CLICKED** 알림 메시지에 대 한 처리기를 제안 합니다.

[!code-cpp[NVC_MFCMessageHandling#5](codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

응용 프로그램 관련 사용자 인터페이스 개체와 동일 하기 때문에이 명령을 **IDC_MY_BUTTON** ID로 할당할 수 있습니다.

두 메시지 범주 모두 인수를 사용 하지 않으며 값을 반환 하지 않습니다.

## <a name="see-also"></a>참고 항목

[메시지 처리기 함수 선언](declaring-message-handler-functions.md)

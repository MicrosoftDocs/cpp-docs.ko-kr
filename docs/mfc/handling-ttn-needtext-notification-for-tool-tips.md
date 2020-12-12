---
description: '자세한 정보: 도구 설명에 대 한 TTN_NEEDTEXT 알림 처리'
title: 도구 설명에 대한 TTN_NEEDTEXT 알림 처리
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 793f6c42e0e43c341884b999e5e1aed0be448b00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326420"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>도구 설명에 대한 TTN_NEEDTEXT 알림 처리

[도구 설명을 사용 하도록 설정](enabling-tool-tips.md)하는 과정에서 소유자 창의 메시지 맵에 다음 항목을 추가 하 여 **TTN_NEEDTEXT** 메시지를 처리 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
이 단추에 텍스트가 필요할 때 호출 되는 멤버 함수입니다.

도구 설명의 ID는 항상 0입니다.

다음과 같이 클래스 정의에서 처리기 함수를 선언 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

기울임꼴로 된 매개 변수는 다음과 같습니다.

*id*<br/>
알림을 보낸 컨트롤의 식별자입니다. 사용되지 않습니다. **NMHDR** 구조체에서 컨트롤 id를 가져옵니다.

*pNMHDR*<br/>
[NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) 구조체에 대 한 포인터입니다. 이 구조는 [TOOLTIPTEXT 구조](tooltiptext-structure.md)에서도 추가로 설명 합니다.

*pResult*<br/>
반환 하기 전에 설정할 수 있는 결과 코드에 대 한 포인터입니다. **TTN_NEEDTEXT** 처리기는 *pResult* 매개 변수를 무시할 수 있습니다.

다음은 폼 보기 알림 처리기의 예입니다.

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

호출 `EnableToolTips` (이 조각에서 가져온 `OnInitDialog` ):

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>참고 항목

[CFrameWnd에서 파생 되지 않은 Windows의 도구 설명](tool-tips-in-windows-not-derived-from-cframewnd.md)

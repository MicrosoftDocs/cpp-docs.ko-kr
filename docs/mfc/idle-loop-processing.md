---
description: '자세한 정보: 유휴 루프 처리'
title: 유휴 루프 처리
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 8972a2bafe5c9d35af2a5f4452082a7ca82f28dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290156"
---
# <a name="idle-loop-processing"></a>유휴 루프 처리

많은 응용 프로그램에서 "백그라운드에서" 긴 처리를 수행 합니다. 경우에 따라 성능 고려 사항은 이러한 작업에 다중 스레딩을 사용 하는 것입니다. 스레드에는 추가 개발 오버 헤드가 수반 되므로 MFC가 [OnIdle](reference/cwinthread-class.md#onidle) 함수에서 수행 하는 유휴 시간 작업과 같은 간단한 작업에는 사용 하지 않는 것이 좋습니다. 이 문서에서는 유휴 처리에 중점을 둔 문서입니다. 다중 스레딩에 대 한 자세한 내용은 [다중 스레딩 항목](../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조 하세요.

사용자가 응용 프로그램과 상호 작용 하지 않는 간격 중에는 일부 종류의 백그라운드 처리가 적절 하 게 수행 됩니다. Microsoft Windows 운영 체제용으로 개발 된 응용 프로그램에서 응용 프로그램은 시간이 오래 걸리는 프로세스를 많은 작은 조각으로 분할 하 여 유휴 시간 처리를 수행할 수 있습니다. 각 조각을 처리 한 후 응용 프로그램은 [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) 루프를 사용 하 여 Windows에 실행 제어를 생성 합니다.

이 문서에서는 응용 프로그램에서 유휴 처리를 수행 하는 두 가지 방법을 설명 합니다.

- MFC의 주 메시지 루프에서 **PeekMessage** 사용

- 응용 프로그램의 다른 위치에 다른 **PeekMessage** 루프를 포함 합니다.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a> MFC 메시지 루프의 PeekMessage

MFC를 사용 하 여 개발한 응용 프로그램에서 클래스의 주 메시지 루프는 `CWinThread` [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32 API를 호출 하는 메시지 루프를 포함 합니다. 또한이 루프는 `OnIdle` 메시지 간의 멤버 함수를 호출 합니다 `CWinThread` . 응용 프로그램은 함수를 재정의 하 여이 유휴 시간에 메시지를 처리할 수 있습니다 `OnIdle` .

> [!NOTE]
> `Run`, `OnIdle` 및 다른 특정 멤버 함수는 이제 클래스가 아닌 클래스의 멤버입니다 `CWinThread` `CWinApp` . `CWinApp`는 `CWinThread`에서 파생됩니다.

유휴 처리를 수행 하는 방법에 대 한 자세한 내용은 *MFC 참조* 에서 [OnIdle](reference/cwinthread-class.md#onidle) 을 참조 하세요.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a> 응용 프로그램의 다른 위치에서 PeekMessage

응용 프로그램에서 유휴 처리를 수행 하는 또 다른 방법에는 함수 중 하나에 메시지 루프를 포함 하는 작업이 포함 됩니다. 이 메시지 루프는 [CWinThread:: Run](reference/cwinthread-class.md#run)에 있는 MFC의 주 메시지 루프와 매우 비슷합니다. 즉, MFC로 개발한 응용 프로그램의 이러한 루프는 주 메시지 루프와 동일한 많은 기능을 수행 해야 합니다. 다음 코드 조각에서는 MFC와 호환 되는 메시지 루프를 작성 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#8](codesnippet/cpp/idle-loop-processing_1.cpp)]

함수에 포함 된이 코드는 유휴 처리를 수행 하는 동안 루프를 실행 합니다. 루프 내에서 중첩 된 루프는를 반복적으로 호출 `PeekMessage` 합니다. 호출에서 0이 아닌 값을 반환 하는 한 루프는 `CWinThread::PumpMessage` 를 호출 하 여 일반적인 메시지 변환과 디스패치를 수행 합니다. `PumpMessage`가 문서화 되지 않은 경우에도 Visual C++ 설치의 \atlmfc\src\mfc 디렉터리에 있는 ThrdCore .cpp 파일에서 소스 코드를 검사할 수 있습니다.

내부 루프가 끝난 후 외부 루프는 하나 이상의에 대 한 호출을 사용 하 여 유휴 처리를 수행 `OnIdle` 합니다. 첫 번째 호출은 MFC의 용도로 사용 됩니다. 를 추가로 호출 하 여 `OnIdle` 백그라운드 작업을 직접 수행할 수 있습니다.

유휴 처리를 수행 하는 방법에 대 한 자세한 내용은 MFC 라이브러리 참조에서 [OnIdle](reference/cwinthread-class.md#onidle) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)

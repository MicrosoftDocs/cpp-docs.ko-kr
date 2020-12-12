---
description: CAnimateCtrl 사용에 대 한 자세한 정보
title: CAnimateCtrl 사용
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: bb13d23f45b3a19516a688fd9e9857f750196d56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271787"
---
# <a name="using-canimatectrl"></a>CAnimateCtrl 사용

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)클래스로 표시 되는 애니메이션 컨트롤은 표준 Windows 비디오/오디오 형식인 AVI (오디오 비디오 인터리브) 형식으로 클립을 표시 하는 창입니다. AVI 클립은 동영상과 같은 일련의 비트맵 프레임입니다.

AVI 클립이 표시 되는 동안 스레드가 계속 실행 되므로 애니메이션 컨트롤의 일반적인 한 가지 용도는 시간이 오래 걸리는 작업 중에 시스템 작업을 나타내는 것입니다. 예를 들어 Windows 찾기 대화 상자는 시스템에서 파일을 검색할 때 이동 돋보기를 표시 합니다.

애니메이션 컨트롤은 간단한 AVI 클립만 재생할 수 있으며 소리를 지원 하지 않습니다. (제한 사항에 대 한 전체 목록은 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)를 참조 하세요.) 애니메이션 컨트롤의 기능은 심각 하 게 제한 되며 변경 될 수 있으므로 멀티미디어 재생 및/또는 기록 기능을 제공 하는 컨트롤이 필요한 경우에는 MCIWnd 컨트롤과 같은 대안을 사용 해야 합니다. MCIWnd 컨트롤에 대 한 자세한 내용은 멀티미디어 설명서를 참조 하세요.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [애니메이션 컨트롤 사용](../mfc/using-an-animation-control.md)

- [애니메이션 컨트롤에서 보내는 알림](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>참고 항목

[컨트롤](../mfc/controls-mfc.md)

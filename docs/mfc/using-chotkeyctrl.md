---
description: '자세히 알아보기: CHotKeyCtrl 사용'
title: CHotKeyCtrl 사용
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: 7f17063a4fb3732a9b121e2b93f5d55e51d5654a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271683"
---
# <a name="using-chotkeyctrl"></a>CHotKeyCtrl 사용

[Chotkeyctrl](../mfc/reference/chotkeyctrl-class.md)클래스로 표시 되는 바로 가기 키는 CTRL + SHIFT + Q와 같이 사용자 형식에 대 한 키 조합의 텍스트 표현을 표시 하는 창입니다. 또한 가상 키 코드의 형식으로이 키의 내부 표현과 이동 상태를 나타내는 플래그 집합을 유지 관리 합니다. 핫 키 컨트롤은 실제로 바로 가기 키를 설정 하지 않습니다 .이 작업은 프로그램에 해당 합니다. 표준 가상 키 코드 목록은 Winuser.h를 참조 하십시오.

핫 키 컨트롤을 사용 하 여 창 또는 스레드와 연결할 핫 키에 대 한 사용자의 입력을 가져옵니다. 핫 키 컨트롤은 사용자에 게 바로 가기 키를 할당 하도록 요청할 때 표시할 수 있는 대화 상자에서 자주 사용 됩니다. 핫 키 컨트롤에서 바로 가기 키를 설명 하는 값을 검색 하 고 적절 한 함수를 호출 하 여 창 또는 스레드에 핫 키를 연결 하는 것은 프로그램의 책임입니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [바로 가기 키 컨트롤 사용](../mfc/using-a-hot-key-control.md)

- [바로 가기 키 설정](../mfc/setting-a-hot-key.md)

- [전역 바로 가기 키](../mfc/global-hot-keys.md)

- [스레드 관련 바로 가기 키](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>참고 항목

[컨트롤](../mfc/controls-mfc.md)

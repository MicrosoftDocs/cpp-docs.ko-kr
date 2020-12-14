---
description: '자세히 알아보기: 멤버 함수 실행'
title: Run 멤버 함수
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: ae67c6b02344a65735ce06775b1d1788d1dabf2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217824"
---
# <a name="run-member-function"></a>Run 멤버 함수

프레임 워크 응용 프로그램은 [CWinApp](../mfc/reference/cwinapp-class.md)클래스의 [Run](../mfc/reference/cwinapp-class.md#run) 멤버 함수에서 대부분의 시간을 소비 합니다. 초기화 후 `WinMain` 에는 `Run` 를 호출 하 여 메시지 루프를 처리 합니다.

`Run` 메시지 루프를 순환 하 여 사용 가능한 메시지에 대 한 메시지 큐를 확인 합니다. 메시지를 사용할 수 있는 경우 `Run` 작업에 대해 디스패치합니다. 사용할 수 있는 메시지가 없는 경우가 종종 있습니다 .이 경우에는를 호출 하 여 `Run` `OnIdle` 사용자 또는 프레임 워크에서 수행 해야 하는 유휴 시간 처리를 수행 해야 할 수 있습니다. 메시지가 없고 유휴 처리를 수행할 수 없는 경우 응용 프로그램은 문제가 발생할 때까지 기다립니다. 응용 프로그램이 종료 되 면을 `Run` 호출 `ExitInstance` 합니다. [OnIdle 멤버 함수](../mfc/onidle-member-function.md) 에 있는 그림은 메시지 루프의 작업 순서를 보여 줍니다.

메시지 디스패치는 메시지의 종류에 따라 달라 집니다. 자세한 내용은 [프레임 워크의 메시지 및 명령](../mfc/messages-and-commands-in-the-framework.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWinApp: 응용 프로그램 클래스](../mfc/cwinapp-the-application-class.md)

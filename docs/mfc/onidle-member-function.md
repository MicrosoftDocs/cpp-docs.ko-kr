---
description: '다음에 대 한 자세한 정보: OnIdle 멤버 함수'
title: OnIdle 멤버 함수
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: a094b72f78db75d9f0f93ffa840d1d90cc96294c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112260"
---
# <a name="onidle-member-function"></a>OnIdle 멤버 함수

Windows 메시지를 처리 하 고 있지 않은 경우 프레임 워크는 [CWinApp](reference/cwinapp-class.md) 멤버 함수 [OnIdle](reference/cwinapp-class.md#onidle) (MFC 라이브러리 참조에 설명 됨)을 호출 합니다.

`OnIdle`백그라운드 작업을 수행 하려면를 재정의 합니다. 기본 버전은 도구 모음 단추와 같은 사용자 인터페이스 개체의 상태를 업데이트 하 고 해당 작업을 수행 하는 과정에서 프레임 워크에서 만든 임시 개체의 정리를 수행 합니다. 다음 그림은 큐에 메시지가 없을 때 메시지 루프가를 호출 하는 방법을 보여 줍니다 `OnIdle` .

![메시지 루프 프로세스](../mfc/media/vc387c1.gif "메시지 루프 프로세스") <br/>
메시지 루프

유휴 루프에서 수행할 수 있는 작업에 대 한 자세한 내용은 [유휴 루프 처리](idle-loop-processing.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWinApp: 응용 프로그램 클래스](cwinapp-the-application-class.md)

---
description: '자세히 알아보기: OnCmdMsg Handler'
title: OnCmdMsg 처리기
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 69dfbd7ccc52a6d90b57ef9cedf0f896d65057b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243967"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 처리기

명령의 라우팅을 수행 하기 위해 각 명령 대상은 `OnCmdMsg` 시퀀스에서 다음 명령 대상의 멤버 함수를 호출 합니다. 명령 대상은 `OnCmdMsg` 명령을 처리할 수 있는지 여부를 확인 하 고 명령을 처리할 수 없는 경우 다른 명령 대상으로 라우트할 수 있는지 여부를 확인 하는 데 사용 합니다.

각 명령 대상 클래스는 멤버 함수를 재정의할 수 있습니다 `OnCmdMsg` . 재정의를 통해 각 클래스는 명령을 특정 한 다음 대상으로 라우팅할 수 있습니다. 예를 들어 프레임 창은 항상 [표준 명령 경로](command-routing.md)테이블에 표시 된 대로 명령을 현재 자식 창이 나 뷰로 라우팅합니다.

의 기본 `CCmdTarget` 구현은 `OnCmdMsg` 명령 대상 클래스의 메시지 맵을 사용 하 여 표준 메시지를 검색 하는 것과 같은 방식으로 수신 하는 각 명령 메시지에 대 한 처리기 함수를 검색 합니다. 일치 하는 항목을 찾으면 처리기를 호출 합니다. 메시지 맵 검색은 [프레임 워크에서 메시지 맵을 검색 하는 방법](how-the-framework-searches-message-maps.md)에 설명 되어 있습니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)

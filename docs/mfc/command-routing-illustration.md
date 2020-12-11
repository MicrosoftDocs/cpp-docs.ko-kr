---
description: '자세한 정보: 명령 라우팅 그림'
title: 명령 라우팅 설명
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: 51c5182eb1fa2a8b9666e265526e9220a9f3d4a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159962"
---
# <a name="command-routing-illustration"></a>명령 라우팅 설명

이를 설명 하기 위해 MDI 응용 프로그램의 편집 메뉴에서 모두 지우기 메뉴 항목의 명령 메시지를 살펴보세요. 이 명령에 대 한 처리기 함수가 응용 프로그램의 문서 클래스의 멤버 함수 라고 가정 합니다. 사용자가 메뉴 항목을 선택 하면 해당 명령이 처리기에 도달 하는 방법은 다음과 같습니다.

1. 주 프레임 창에는 먼저 명령 메시지가 수신 됩니다.

1. 주 MDI 프레임 창은 현재 활성화 된 MDI 자식 창에 명령을 처리할 수 있는 기회를 제공 합니다.

1. MDI 자식 프레임 창의 표준 라우팅은 자체 메시지 맵을 확인 하기 전에 명령에 대 한 보기를 제공 합니다.

1. 뷰는 먼저 자체 메시지 맵을 확인 하 고, 처리기를 찾지 못하면 다음 명령을 연결 된 문서에 라우팅합니다.

1. 문서에서 메시지 맵을 확인 하 고 처리기를 찾습니다. 이 문서 멤버 함수를 호출 하 고 라우팅이 중지 됩니다.

문서에 처리기가 없는 경우 다음에 명령을 해당 문서 템플릿으로 라우팅합니다. 그런 다음 명령이 뷰로 돌아간 다음 프레임 창으로 돌아갑니다. 마지막으로, 프레임 창에서 메시지 맵을 확인 합니다. 그래도 확인 하지 못한 경우에는 명령이 주 MDI 프레임 창으로 다시 라우팅되고 응용 프로그램 개체 (처리 되지 않은 명령의 최종 대상)로 라우팅됩니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)

---
description: '자세히 알아보기: 메시지 매핑'
title: 메시지 매핑
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 34d100a7ae527acc9f5520474e75b486b2f6276c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280796"
---
# <a name="mapping-messages"></a>메시지 매핑

메시지 또는 명령을 수신할 수 있는 각 프레임 워크 클래스에는 자체의 "메시지 맵"이 있습니다. 프레임 워크는 메시지 맵을 사용 하 여 메시지와 명령을 처리기 함수에 연결 합니다. 클래스에서 파생 된 클래스에는 `CCmdTarget` 메시지 맵이 있을 수 있습니다. 다른 문서에서는 메시지 맵에 대해 자세히 설명 하 고 사용 방법을 설명 합니다.

이름 "메시지 맵"에도 불구 하 고 메시지 맵은 메시지 [범주](message-categories.md)에 나열 된 메시지의 세 가지 범주로 메시지와 명령을 모두 처리 합니다.

## <a name="see-also"></a>참고 항목

[프레임 워크의 메시지 및 명령](messages-and-commands-in-the-framework.md)

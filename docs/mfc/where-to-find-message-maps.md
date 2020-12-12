---
description: '자세한 정보: 메시지 맵을 찾을 수 있는 위치'
title: 메시지 맵을 찾을 장소
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: 4796d358dd3be5455b22e348fbcc9236d1404ce8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284969"
---
# <a name="where-to-find-message-maps"></a>메시지 맵을 찾을 장소

응용 프로그램 마법사를 사용 하 여 새 기본 응용 프로그램을 만드는 경우 응용 프로그램 마법사는 사용자가 만드는 각 명령 대상 클래스에 대 한 메시지 맵을 작성 합니다. 여기에는 파생 된 응용 프로그램, 문서, 뷰 및 프레임 창 클래스가 포함 됩니다. 이러한 메시지 맵에는 특정 메시지 및 미리 정의 된 명령에 대해 응용 프로그램 마법사에서 제공 하는 항목이 이미 있고, 일부는 추가할 처리기의 자리 표시자 일 뿐입니다.

클래스의 메시지 맵은에 있습니다. 클래스에 대 한 CPP 파일입니다. 응용 프로그램 마법사에서 생성 하는 기본 메시지 맵으로 작업 하는 경우 [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 각 클래스에서 처리할 메시지 및 명령에 대 한 항목을 추가 합니다. 일부 항목을 추가한 후 일반적인 메시지 맵은 다음과 같이 표시 될 수 있습니다.

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

메시지 맵은 매크로 컬렉션으로 구성 됩니다. 두 매크로 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) 및 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)는 메시지 맵을 묶습니다. 등의 다른 매크로는 `ON_COMMAND` 메시지 맵 내용을 입력 합니다.

> [!NOTE]
> 메시지 맵 매크로 뒤에 세미콜론이 오지 않습니다.

클래스 추가 마법사를 사용 하 여 새 클래스를 만드는 경우 클래스에 대 한 메시지 맵을 제공 합니다. 또는 소스 코드 편집기를 사용 하 여 수동으로 메시지 맵을 만들 수 있습니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 메시지 맵을 검색 하는 방법](../mfc/how-the-framework-searches-message-maps.md)

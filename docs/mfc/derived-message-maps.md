---
title: 파생된 메시지 맵
description: MFC 메시지 처리에 대해 설명 합니다.
ms.date: 09/23/2020
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 44c2180e441c91d34350c65bc17a53d1b650607c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414219"
---
# <a name="derived-message-maps"></a>파생된 메시지 맵

메시지를 처리 하는 동안 클래스의 자체 메시지 맵을 확인 하는 것은 메시지 맵 스토리가 끝나지 않습니다. 클래스 `CMyView` (에서 파생 `CView` )가 메시지에 대해 일치 하는 항목이 없는 경우 어떻게 되나요?

의 기본 클래스는에서 파생 되는 것을 염두에 두어야 `CView` `CMyView` `CWnd` 합니다. 따라서는 이며은입니다 `CMyView` *is* `CView` *is* `CWnd` . 이러한 각 클래스에는 자체 메시지 맵이 있습니다. 아래 그림은 클래스의 계층 관계를 보여 주지만 `CMyView` 개체는 세 클래스 모두의 특징을 갖는 단일 개체 임을 명심 해야 합니다.

![뷰 계층 구조](../mfc/media/vc38621.gif "뷰 계층 구조") <br/>
뷰 계층 구조

클래스의 메시지 맵에서 메시지를 일치 시킬 수 없는 경우에 `CMyView` 도 프레임 워크는 직접 기본 클래스의 메시지 맵을 검색 합니다. `BEGIN_MESSAGE_MAP`메시지 맵 시작의 매크로는 두 개의 클래스 이름을 인수로 지정 합니다.

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

첫 번째 인수는 메시지 맵이 속한 클래스의 이름을로 합니다. 두 번째 인수는 직접 기본 클래스와의 연결을 제공 `CView` 하 여 프레임 워크에서 메시지 맵을 검색할 수 있도록 합니다.

따라서 기본 클래스에서 제공 하는 메시지 처리기는 파생 클래스에 의해 상속 됩니다. 이는 모든 처리기 멤버 함수를 가상으로 만들 필요 없이 일반적인 가상 멤버 함수와 매우 유사 합니다.

기본 클래스 메시지 맵에 핸들러가 없으면 메시지의 기본 처리가 수행 됩니다. 메시지가 명령이 면 프레임 워크는이를 다음 명령 대상으로 라우팅합니다. 표준 Windows 메시지 인 경우 메시지가 적절 한 기본 창 프로시저에 전달 됩니다.

메시지 맵 일치를 가속화 하기 위해 프레임 워크는 동일한 메시지를 다시 받을 가능성에 대해 최근 일치 항목을 캐시 합니다. 이에 대 한 한 가지 결과는 프레임 워크가 처리 되지 않은 메시지를 매우 효율적으로 처리 한다는 것입니다. 메시지 맵은 가상 함수를 사용 하는 구현 보다 더 많은 공간 효율적입니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 메시지 맵을 검색 하는 방법](how-the-framework-searches-message-maps.md)

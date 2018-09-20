---
title: '방법: 메시지 맵 상호 참조 사용 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fccdf620cbdaeffc7fb201e014edc4c7c1dddc83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434455"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>방법: 메시지 맵 상호 참조 사용

레이블이 지정 된 항목의 \<memberFxn >에서 파생된 된 고유한 멤버 함수가 작성 [CWnd](../../mfc/reference/cwnd-class.md) 클래스. 원하는 어떤 이름도 함수를 제공 합니다. 와 같은 다른 함수 `OnActivate`, 클래스의 멤버 함수는 `CWnd`합니다. 메시지를 전달 하 고 호출 하는 경우는 `DefWindowProc` Windows 함수입니다. Windows 알림 메시지를 처리 하려면 해당 재정의 `CWnd` 파생된 클래스의 함수입니다. 함수는 기본 클래스를 사용 하려면 기본 클래스에서 재정의 된 함수를 호출 해야 하 고 Windows 메시지에 응답 합니다.

모든 경우에는 함수 프로토타입에 배치 된 `CWnd`-파생된 클래스 헤더 및 코드와 같이 메시지 맵 항목입니다.

다음과 같은 용어가 사용 됩니다.

|용어|정의|
|----------|----------------|
|ID|모든 사용자 정의 메뉴 항목 ID (WM_COMMAND 메시지) 또는 컨트롤 ID (자식 창 알림 메시지).|
|"message"와 "wNotifyCode"|WINDOWS에 정의 된 대로 Windows Id의 메시지입니다. 8.|
|nMessageVariable|반환 값이 포함 된 변수의 이름을 `RegisterWindowMessage` Windows 함수입니다.|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)


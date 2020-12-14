---
description: '자세히 알아보기: 방법: 상호 참조 Message-Map 사용'
title: '방법: 메시지 맵 상호 참조 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 4bbc140db59a7df4abd42fdcf68b47273ec3e846
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219657"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>방법: 메시지 맵 상호 참조 사용

레이블이 지정 된 항목에서 \<memberFxn> 파생 된 [CWnd](../../mfc/reference/cwnd-class.md) 클래스에 대해 고유한 멤버 함수를 작성 합니다. 원하는 이름으로 함수를 제공 합니다. 등의 다른 함수 `OnActivate` 는 클래스의 멤버 함수 `CWnd` 입니다. 호출 된 경우 Windows 함수에 메시지를 전달 `DefWindowProc` 합니다. Windows 알림 메시지를 처리 하려면 `CWnd` 파생 클래스에서 해당 함수를 재정의 합니다. 함수는 기본 클래스와 Windows가 메시지에 응답 하도록 기본 클래스에서 재정의 된 함수를 호출 해야 합니다.

모든 경우에 함수 프로토타입을 `CWnd` 파생 클래스 헤더에 배치 하 고 표시 된 대로 메시지 맵 항목을 코딩 합니다.

사용 되는 용어는 다음과 같습니다.

|용어|정의|
|----------|----------------|
|id|사용자 정의 메뉴 항목 ID (WM_COMMAND 메시지) 또는 컨트롤 ID (자식 창 알림 메시지).|
|"message" 및 "wNotifyCode"|Windows에 정의 된 windows 메시지 Id입니다.|
|nMessageVariable|Windows 함수의 반환 값을 포함 하는 변수의 이름입니다 `RegisterWindowMessage` .|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)

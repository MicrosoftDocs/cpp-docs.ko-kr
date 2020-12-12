---
description: '자세한 정보: 메시지 처리기'
title: 메시지 처리기
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: dc3f52956f125542ef0c5d879543f1e8a49e803b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203369"
---
# <a name="message-handlers"></a>메시지 처리기

MFC에서 전용 *처리기* 함수는 각각의 개별 메시지를 처리 합니다. 메시지 처리기 함수는 클래스의 멤버 함수입니다. 이 설명서에서는 *메시지 처리기 멤버 함수*, *메시지 처리기 함수*, *메시지 처리기* 및 *처리기* 를 교대로 사용 하 여 용어를 사용 합니다. 일부 종류의 메시지 처리기를 "명령 처리기" 라고도 합니다.

프레임 워크 응용 프로그램을 작성 하는 데 필요한 작업의 상당 부분에 대 한 메시지 처리기 계정을 작성 합니다. 이 문서 제품군에서는 메시지 처리 메커니즘의 작동 방식을 설명 합니다.

메시지 처리기는 메시지에 대 한 응답으로 수행 하려는 작업을 수행 합니다. 클래스의 [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리기를 만든 다음 소스 코드 편집기를 사용 하 여 처리기의 코드를 채울 수 있습니다.

Microsoft Visual C++ 및 MFC의 모든 기능을 사용 하 여 처리기를 작성할 수 있습니다. 모든 클래스의 목록은 *MFC 참조* 의 [클래스 라이브러리 개요](class-library-overview.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[프레임 워크의 메시지 및 명령](messages-and-commands-in-the-framework.md)

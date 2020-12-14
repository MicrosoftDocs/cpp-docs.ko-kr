---
description: '자세히 알아보기: 인터넷 응용 프로그램 테스트'
title: 인터넷 애플리케이션 테스트
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: ed3dd9819524e156af47da4070c517e3761380ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216264"
---
# <a name="testing-internet-applications"></a>인터넷 애플리케이션 테스트

특히 웹 서버에서 실행 되는 응용 프로그램의 경우 인터넷에 대 한 몇 가지 고유한 테스트 과제가 있습니다. 테스트 서버에 연결 하는 단일 사용자 클라이언트를 사용 하 여 초기 테스트를 수행할 수 있습니다. 이는 코드를 디버깅 하는 데 유용 합니다.

또한 실시간 연결을 통해 여러 클라이언트를 연결 하는 경우와 모뎀 연결을 비롯 한 고속 직렬 회선을 통해 연결 된 여러 클라이언트를 사용 하 여 테스트 합니다. 실제 조건을 시뮬레이션 하는 것은 어려울 수 있지만 가능한 시나리오를 디자인 하 고 실행 하는 데 시간이 많이 소요 될 수 있습니다. 가능 하면 도구를 사용 하 여 용량 및 스트레스 테스트를 수행 하는 것도 좋습니다. 타이밍 버그와 같은 특정 버그 클래스는 찾고 재현 하기 어렵습니다.

인터넷 프로그래밍의 문제 중 하나는 표시 유형입니다. 사이트에 대 한 많은 액세스가 서버 속도를 저하 시킬 수 있습니다. 서버를 정상적으로 저하 시킬 수 있습니다. 응용 프로그램에 오류가 발생 하는 경우 (예: 레지스트리에 쓰는 동안 또는 클라이언트에서 쿠키를 작성 하는 동안 데이터 손상이 발생 하는 경우), 사용자의 컴퓨터에 파괴적인 것을 방지 하려고 합니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](../mfc/mfc-internet-programming-basics.md)

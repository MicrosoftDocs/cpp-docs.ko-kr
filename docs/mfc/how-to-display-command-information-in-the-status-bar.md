---
description: '자세히 알아보기: 방법: 상태 표시줄에 명령 정보 표시'
title: '방법: 상태 표시줄에 명령 정보 표시'
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: 568e8d356659d5267e8c4947f2981cd6243a7056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330226"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>방법: 상태 표시줄에 명령 정보 표시

응용 프로그램 마법사를 실행 하 여 응용 프로그램의 기본 구조를 만들 때 도구 모음과 상태 표시줄을 지원할 수 있습니다. 응용 프로그램 마법사에서 하나의 옵션만 지원 됩니다. 상태 표시줄이 있으면 사용자가 메뉴의 항목 위로 포인터를 이동할 때 응용 프로그램에서 자동으로 유용한 피드백을 제공 합니다. 메뉴 항목이 강조 표시 되 면 응용 프로그램에서 상태 표시줄에 프롬프트 문자열을 자동으로 표시 합니다. 예를 들어 사용자가 포인터를 **편집** 메뉴의 **잘라내기** 명령 위로 움직이면 상태 표시줄에 상태 표시줄의 메시지 영역에 "선택 영역을 잘라내어 클립보드에 넣습니다."가 표시 될 수 있습니다. 이 프롬프트를 통해 사용자는 메뉴 항목의 용도를 이해할 수 있습니다. 사용자가 도구 모음 단추를 클릭 하는 경우에도 작동 합니다.

프로그램에 추가 하는 메뉴 항목에 대 한 프롬프트 문자열을 정의 하 여이 상태 표시줄 도움말에를 추가할 수 있습니다. 이렇게 하려면 메뉴 편집기에서 메뉴 항목의 속성을 편집할 때 프롬프트 문자열을 제공 합니다. 사용자가 정의 하는 문자열은 응용 프로그램 리소스 파일에 저장 됩니다. 설명 하는 명령과 동일한 Id를 가집니다.

기본적으로 응용 프로그램 마법사는 표준 "준비" 메시지에 대 한 ID 인 **AFX_IDS_IDLEMESSAGE** 를 추가 합니다 .이 메시지는 프로그램이 새 메시지를 대기 하 고 있을 때 표시 됩니다. 응용 프로그램 마법사에서 Context-Sensitive 도움말 옵션을 지정 하면 메시지가 "도움말을 보려면 F1 키를 누릅니다."로 변경 됩니다.

## <a name="see-also"></a>참고 항목

[메시지 처리 및 매핑](message-handling-and-mapping.md)

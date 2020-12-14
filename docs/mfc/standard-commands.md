---
description: '자세히 알아보기: 표준 명령'
title: 표준 명령
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
ms.openlocfilehash: 09c0afecf5b34565c3ab14e276c7c43a20189a0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216745"
---
# <a name="standard-commands"></a>표준 명령

프레임 워크는 많은 표준 명령 메시지를 정의 합니다. 이러한 명령의 Id는 일반적으로 다음 형식을 사용 합니다.

**ID_** *소스* _ *항목*

여기서 *Source* 는 일반적으로 메뉴 이름이 고 *항목* 은 메뉴 항목입니다. 예를 들어 파일 메뉴에 있는 새 명령의 명령 ID는 ID_FILE_NEW 됩니다. 표준 명령 Id는 설명서에서 굵게 표시 됩니다. 프로그래머 정의 Id는 주변 텍스트와 다른 글꼴로 표시 됩니다.

다음은 지원 되는 가장 중요 한 몇 가지 명령 목록입니다.

*파일 메뉴 명령*<br/>
새로 만들기, 열기, 닫기, 저장, 다른 이름으로 저장, 페이지 설정, 인쇄 설정, 인쇄, 인쇄 미리 보기, 종료 및 가장 최근에 사용한 파일입니다.

*편집 메뉴 명령*<br/>
지우기, 모두 지우기, 복사, 잘라내기, 찾기, 붙여넣기, 반복, 바꾸기, 모두 선택, 실행 취소 및 다시 실행

*보기 메뉴 명령*<br/>
도구 모음 및 상태 표시줄입니다.

*창 메뉴 명령*<br/>
새로 만들기, 정렬, 계단식 배열, 가로 바둑판식 배열, 세로 바둑판식 배열 및 분할이 있습니다.

*도움말 메뉴 명령*<br/>
Index, Help 및 About를 사용 합니다.

*OLE 명령 (편집 메뉴)*<br/>
새 개체를 삽입 하 고, 링크를 편집 하 고, 링크를 붙여넣고, 붙여넣습니다. 및 *typename* 개체 (verb 명령)를 삽입 합니다.

프레임 워크는 이러한 명령에 대해 다양 한 수준의 지원을 제공 합니다. 일부 명령은 정의 된 명령 Id로만 지원 되 고 다른 명령은 철저 한 구현에서 지원 됩니다. 예를 들어 프레임 워크는 새 문서 개체를 만들고, 열기 대화 상자를 표시 하 고, 파일을 열고 읽는 방법으로 파일 메뉴에서 열기 명령을 구현 합니다. 이와 달리 ID_EDIT_COPY 명령은 복사 하는 데이터의 특성에 따라 달라 지기 때문에 편집 메뉴에서 직접 명령을 구현 해야 합니다.

지원 되는 명령 및 제공 된 구현 수준에 대 한 자세한 내용은 [Technical Note 22](../mfc/tn022-standard-commands-implementation.md)를 참조 하십시오. 표준 명령은 AFXRES.H 파일에 정의 되어 있습니다.

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 개체 및 명령 Id](../mfc/user-interface-objects-and-command-ids.md)

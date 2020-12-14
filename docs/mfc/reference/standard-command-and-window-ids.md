---
description: '자세한 정보: 표준 명령 및 창 Id'
title: 표준 명령 및 창 ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 9f5a6b59d9451d749a48443bddf3560d2702bfe5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218903"
---
# <a name="standard-command-and-window-ids"></a>표준 명령 및 창 ID

Microsoft Foundation Class 라이브러리는 Afxres.h의 여러 표준 명령 및 창 ID를 정의합니다. 이러한 Id는 리소스 편집기와 [클래스 마법사](mfc-class-wizard.md) 에서 메시지를 처리기 함수에 매핑하기 위해 가장 일반적으로 사용 됩니다. 모든 표준 명령에는 **ID_** 접두사가 있습니다. 예를 들어, 메뉴 편집기를 사용 하는 경우 일반적으로 파일 열기 메뉴 항목을 표준 ID_FILE_OPEN 명령 ID에 바인딩합니다.

대부분의 표준 명령에서 프레임 워크 자체는 주 프레임 워크 클래스 ( `CWinThread` ,, `CWinApp` `CView` , `CDocument` 등)의 메시지 맵을 통해 명령을 처리 하기 때문에 응용 프로그램 코드에서 명령 ID를 참조할 필요가 없습니다.

표준 명령 Id 외에도 **AFX_ID** 접두사가 포함 된 다양 한 표준 id가 정의 됩니다. 이러한 Id에는 표준 창 Id (접두사      **AFX_IDW_**), 문자열 id (접두사 **AFX_IDS_**) 및 기타 여러 형식이 포함 됩니다.

프로그래머는 **AFX_ID** 접두사로 시작 하는 id를 거의 사용 하지 않지만 **AFX_ID** s를 참조 하는 프레임 워크 함수를 재정의할 때 이러한 id를 참조 해야 할 수도 있습니다.

ID는 이 참조 설명서에서 개별적으로 설명하지 않습니다. 자세한 내용은 기술 참고 [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), [22](../../mfc/tn022-standard-commands-implementation.md)에서 확인할 수 있습니다.

> [!NOTE]
> 헤더 파일 Afxres.h는 Afxwin.h에 간접적으로 포함됩니다. 애플리케이션의 리소스 스크립트(.rc) 파일에 다음 문을 명시적으로 포함해야 합니다.

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)

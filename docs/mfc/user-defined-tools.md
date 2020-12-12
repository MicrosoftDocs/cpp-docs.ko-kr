---
description: '자세히 알아보기: 사용자 정의 도구'
title: 사용자 정의 형식
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: 4cccd0a68751a2f196c8c2e652088e8939e3f162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263636"
---
# <a name="user-defined-tools"></a>사용자 정의 형식

MFC는 사용자 정의 도구를 지원 합니다. 사용자 정의 도구는 외부의 사용자 지정 프로그램을 실행 하는 특수 명령입니다. 사용자 지정 프로세스를 사용 하 여 사용자 정의 도구를 관리할 수 있습니다. 그러나 응용 프로그램 개체가 [CWinAppEx 클래스](../mfc/reference/cwinappex-class.md)에서 파생 되지 않은 경우에는이 프로세스를 사용할 수 없습니다. 사용자 지정에 대 한 자세한 내용은 [MFC의 사용자 지정](../mfc/customization-for-mfc.md)을 참조 하세요.

사용자 정의 도구 지원을 사용 하도록 설정한 경우 사용자 지정 대화 상자에 **도구** 탭이 자동으로 포함 됩니다. 다음 그림에서는 **도구** 페이지를 보여 줍니다.

![사용자 지정 대화 상자의 도구 탭](../mfc/media/custdialogboxtoolstab.png "사용자 지정 대화 상자의 도구 탭") <br/>
사용자 지정 대화 상자 도구 탭

## <a name="enabling-user-defined-tools-support"></a>사용자 정의 도구 지원 사용

응용 프로그램에서 사용자 정의 도구를 사용 하도록 설정 하려면 [CWinAppEx:: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)를 호출 합니다. 그러나이 호출에 대 한 매개 변수로 사용할 응용 프로그램의 리소스 파일에서 몇 가지 상수를 먼저 정의 해야 합니다.

리소스 편집기에서 적절 한 명령 ID를 사용 하는 더미 명령을 만듭니다. 다음 예제에서는를 `ID_TOOLS_ENTRY` 명령 ID로 사용 합니다. 이 명령 ID는 프레임 워크가 사용자 정의 도구를 삽입 하는 하나 이상의 메뉴에서 위치를 표시 합니다.

사용자 정의 도구를 표시 하려면 문자열 테이블에 일부 연속 Id를 따로 설정 해야 합니다. 따로 설정 하는 문자열 수는 사용자가 정의할 수 있는 최대 사용자 도구 수와 같습니다. 다음 예제에서는 이러한 이름이로 지정 됩니다 `ID_USER_TOOL1` `ID_USER_TOOL10` .

사용자에 게 도구 라고 하는 외부 프로그램에 대 한 디렉터리 및 인수를 선택 하는 데 도움이 되는 제안을 제공할 수 있습니다. 이렇게 하려면 리소스 편집기에서 두 개의 팝업 메뉴를 만듭니다. 다음 예제에서 이러한 이름은 `IDR_MENU_ARGS` 및 `IDR_MENU_DIRS` 입니다. 이러한 메뉴의 각 명령에 대해 응용 프로그램 문자열 테이블에 문자열을 정의 합니다. 문자열의 리소스 ID는 명령 ID와 같아야 합니다.

[Cusertool 클래스](../mfc/reference/cusertool-class.md) 에서 파생 클래스를 만들어 기본 구현을 대체할 수도 있습니다. 이렇게 하려면 파생 클래스에 대 한 런타임 정보를 RUNTIME_CLASS ([Cusertool 클래스](../mfc/reference/cusertool-class.md)) 대신 CWinAppEx:: EnableUserTools의 네 번째 매개 변수로 전달 합니다.

적절 한 상수를 정의한 후에는 [CWinAppEx:: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) 를 호출 하 여 사용자 정의 도구를 사용 하도록 설정 합니다.

다음 메서드 호출은 이러한 상수를 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

이 예제에서 도구 탭은 **사용자 지정** 대화 상자에 포함 됩니다. 사용자가 해당 메뉴를 열 때마다 프레임 워크는 메뉴의 명령 ID와 일치 하는 모든 명령을 `ID_TOOLS_ENTRY` 현재 정의 된 사용자 도구 집합과 바꿉니다. 명령 Id는 `ID_USER_TOOL1` `ID_USER_TOOL10` 사용자 정의 도구에 사용 하도록 예약 되어 있습니다. [Cusertool](../mfc/reference/cusertool-class.md) 클래스 클래스는 사용자 도구에 대 한 호출을 처리 합니다. **사용자 지정** 대화 상자의 도구 탭에서는 인수 및 디렉터리 항목 필드의 오른쪽에 메뉴 **IDR_MENU_ARGS** 및 **IDR_MENU_DIRS** 에 액세스할 수 있는 단추를 제공 합니다. 사용자가 이러한 메뉴 중 하나에서 명령을 선택 하면 프레임 워크는 리소스 ID가 명령 ID와 같은 문자열을 해당 하는 텍스트 상자에 추가 합니다.

### <a name="including-predefined-tools"></a>미리 정의 된 도구 포함

응용 프로그램 시작 시 일부 도구를 미리 정의 하려면 응용 프로그램의 주 창에 있는 [CFrameWnd:: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) 메서드를 재정의 해야 합니다. 이 방법에서는 다음 단계를 수행 해야 합니다.

##### <a name="to-add-new-tools-in-loadframe"></a>LoadFrame에 새 도구를 추가 하려면

1. [CWinAppEx:: GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)를 호출 하 여 [CUserToolsManager 클래스](../mfc/reference/cusertoolsmanager-class.md) 개체에 대 한 포인터를 가져옵니다.

1. 만들려는 모든 도구에 대해 [CUserToolsManager:: CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)를 호출 합니다. 이 메서드는 [Cusertool 클래스](../mfc/reference/cusertool-class.md) 개체에 대 한 포인터를 반환 하 고 새로 만든 사용자 도구를 도구의 내부 컬렉션에 추가 합니다. [CWinAppEx:: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)의 네 번째 매개 변수로 [cusertool 클래스](../mfc/reference/cusertool-class.md) 의 파생 클래스에 대 한 런타임 정보를 제공한 경우 [CUserToolsManager:: CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) 는 대신 해당 클래스의 인스턴스를 인스턴스화하고 반환 합니다.

1. 각 도구에 대해를 설정 하 여 텍스트 레이블을 설정 하 `CUserTool::m_strLabel` 고를 호출 하 여 해당 명령을 설정 `CUserTool::SetCommand` 합니다. [Cusertool 클래스](../mfc/reference/cusertool-class.md) 의 기본 구현에서는에 대 한 호출에 지정 된 프로그램에서 사용 가능한 아이콘을 자동으로 검색 `SetCommand` 합니다.

## <a name="see-also"></a>참고 항목

[MFC에 대한 사용자 지정](../mfc/customization-for-mfc.md)<br/>
[CUserTool 클래스](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager 클래스](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx 클래스](../mfc/reference/cwinappex-class.md)

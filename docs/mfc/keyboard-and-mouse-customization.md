---
description: '자세한 정보: 키보드 및 마우스 사용자 지정'
title: 키보드 및 마우스 사용자 지정
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 2ff54b2092bb6db52d5b780f4e64e51e05d8b402
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336818"
---
# <a name="keyboard-and-mouse-customization"></a>키보드 및 마우스 사용자 지정

MFC를 통해 응용 프로그램 사용자는 키보드 및 마우스 입력을 처리 하는 방법을 사용자 지정할 수 있습니다. 사용자는 명령에 바로 가기 키를 할당 하 여 키보드 입력을 사용자 지정할 수 있습니다. 사용자가 응용 프로그램의 특정 창 내에서 두 번 클릭할 때 실행 되는 명령을 선택 하 여 마우스 입력을 사용자 지정할 수도 있습니다. 이 항목에서는 응용 프로그램에 대 한 입력을 사용자 지정 하는 방법을 설명 합니다.

사용자 **지정** 대화 상자에서 사용자가 마우스 및 키보드의 사용자 지정 컨트롤을 변경할 수 있습니다. 이 대화 상자를 표시 하려면 **보기** 메뉴에서 사용자 **지정** 을 가리키고 **도구 모음 및 도킹** 을 클릭 합니다. 대화 상자에서 사용자가 **키보드** 탭 또는 **마우스** 탭을 클릭 합니다.

## <a name="keyboard-customization"></a>키보드 사용자 지정

다음 그림에서는 **사용자 지정** 대화 상자의 **키보드** 탭을 보여 줍니다.

![사용자 지정 대화 상자의 키보드 탭](../mfc/media/mfcnextkeyboardtab.png "사용자 지정 대화 상자의 키보드 탭") <br/>
키보드 사용자 지정 탭

사용자는 키보드 탭과 상호 작용 하 여 명령에 하나 이상의 바로 가기 키를 할당 합니다. 사용할 수 있는 명령은 탭의 왼쪽에 나열 됩니다. 사용자는 메뉴에서 사용 가능한 명령을 선택할 수 있습니다. 메뉴 명령만 바로 가기 키와 연결할 수 있습니다. 사용자가 새 바로 가기를 입력 하면 **할당** 단추를 사용할 수 있게 됩니다. 사용자가이 단추를 클릭 하면 응용 프로그램에서 선택한 명령을 해당 바로 가기로 연결 합니다.

현재 할당 된 바로 가기 키가 모두 오른쪽 열의 목록 상자에 나열 됩니다. 사용자는 개별 바로 가기를 선택 하 고 제거 하거나 응용 프로그램에 대 한 모든 매핑을 다시 설정할 수도 있습니다.

응용 프로그램에서이 사용자 지정을 지원 하려는 경우 [CKeyboardManager](reference/ckeyboardmanager-class.md) 개체를 만들어야 합니다. 개체를 만들려면 `CKeyboardManager` [CWinAppEx:: InitKeyboardManager](reference/cwinappex-class.md#initkeyboardmanager)함수를 호출 합니다. 이 메서드는 키보드 관리자를 만들고 초기화 합니다. 키보드 관리자를 수동으로 만드는 경우를 호출 `CWinAppEx::InitKeyboardManager` 하 여 초기화 해야 합니다.

마법사를 사용 하 여 응용 프로그램을 만드는 경우 마법사가 키보드 관리자를 초기화 합니다. 응용 프로그램에서 키보드 관리자를 초기화 한 후 프레임 워크는 **사용자 지정** 대화 상자에 **키보드** 탭을 추가 합니다.

## <a name="mouse-customization"></a>마우스 사용자 지정

다음 그림에서는 **사용자 지정** 대화 상자의 **마우스** 탭을 보여 줍니다.

![사용자 지정 대화 상자의 마우스 탭](../mfc/media/mfcnextmousetab.png "사용자 지정 대화 상자의 마우스 탭") <br/>
마우스 사용자 지정 탭

사용자는이 탭을 조작 하 여 마우스 두 번 클릭 작업에 메뉴 명령을 할당 합니다. 사용자는 창의 왼쪽에서 보기를 선택한 다음 오른쪽에 있는 컨트롤을 사용 하 여 명령을 두 번 클릭 동작과 연결 합니다. 사용자가 **닫기** 를 클릭 하면 응용 프로그램은 사용자가 뷰의 아무 곳 이나 두 번 클릭할 때마다 연결 된 명령을 실행 합니다.

기본적으로 마법사를 사용 하 여 응용 프로그램을 만들 때 마우스 사용자 지정은 활성화 되지 않습니다.

#### <a name="to-enable-mouse-customization"></a>마우스 사용자 지정을 사용 하도록 설정 하려면

1. [CWinAppEx:: InitMouseManager](reference/cwinappex-class.md#initmousemanager)를 호출 하 여 [CMouseManager](reference/cmousemanager-class.md) 개체를 초기화 합니다.

1. [CWinAppEx:: GetMouseManager](reference/cwinappex-class.md#getmousemanager)를 사용 하 여 마우스 관리자에 대 한 포인터를 가져옵니다.

1. [CMouseManager:: AddView](reference/cmousemanager-class.md#addview) 메서드를 사용 하 여 마우스 관리자에 뷰를 추가 합니다. 마우스 관리자에 추가 하려는 모든 보기에 대해이 작업을 수행 합니다.

응용 프로그램에서 마우스 관리자를 초기화 한 후 프레임 워크는 **사용자 지정** 대화 상자에 **마우스** 탭을 추가 합니다. 뷰를 추가 하지 않으면 탭에 액세스 하면 처리 되지 않은 예외가 발생 합니다. 보기 목록을 만든 후에는 사용자가 **마우스** 탭을 사용할 수 있습니다.

마우스 관리자에 새 보기를 추가할 때 고유한 ID를 지정 합니다. 창에 대 한 마우스 사용자 지정을 지원 하려는 경우 WM_LBUTTONDBLCLICK 메시지를 처리 하 고 [CWinAppEx:: OnViewDoubleClick](reference/cwinappex-class.md#onviewdoubleclick) 함수를 호출 해야 합니다. 이 함수를 호출 하는 경우 매개 변수 중 하나는 해당 창에 대 한 ID입니다. 프로그래머는 ID 번호와 연관 된 개체를 추적 해야 합니다.

## <a name="security-concerns"></a>보안 고려 사항

사용자 [정의 도구](user-defined-tools.md)에 설명 된 대로 사용자는 두 번 클릭 이벤트에 사용자 정의 도구 ID를 연결할 수 있습니다. 사용자가 뷰를 두 번 클릭 하면 응용 프로그램에서 연결 된 ID와 일치 하는 사용자 도구를 찾습니다. 응용 프로그램에서 일치 하는 도구를 찾으면 도구를 실행 합니다. 응용 프로그램에서 일치 하는 도구를 찾을 수 없는 경우 두 번 클릭 한 뷰에 ID가 포함 된 WM_COMMAND 메시지를 보냅니다.

사용자 지정 된 설정은 레지스트리에 저장 됩니다. 공격자는 레지스트리를 편집 하 여 유효한 사용자 도구 ID를 임의의 명령으로 바꿀 수 있습니다. 사용자가 뷰를 두 번 클릭 하면 보기에서 공격자가 planted 명령을 처리 합니다. 이로 인해 예기치 않은 잠재적으로 위험한 동작이 발생할 수 있습니다.

또한 이러한 종류의 공격은 사용자 인터페이스 보호를 무시할 수 있습니다. 예를 들어 응용 프로그램이 인쇄를 사용 하지 않도록 설정 되어 있다고 가정 합니다. 즉, 사용자 인터페이스에서 **인쇄** 메뉴와 단추를 사용할 수 없습니다. 일반적으로이는 응용 프로그램이 인쇄 되지 않도록 합니다. 그러나 공격자가 레지스트리를 편집한 경우에는 사용자가 사용할 수 없는 사용자 인터페이스 요소를 무시 하 고 뷰를 두 번 클릭 하 여 인쇄 명령을 직접 보낼 수 있습니다.

이러한 종류의 공격 으로부터 보호 하려면 응용 프로그램 명령 처리기에 코드를 추가 하 여 명령이 실행 되기 전에 유효한 지 확인 합니다. 명령이 응용 프로그램으로 전송 되는 것을 방지 하기 위해 사용자 인터페이스에 의존 하지 않습니다.

## <a name="see-also"></a>참고 항목

[MFC에 대한 사용자 지정](customization-for-mfc.md)<br/>
[CKeyboardManager 클래스](reference/ckeyboardmanager-class.md)<br/>
[CMouseManager 클래스](reference/cmousemanager-class.md)<br/>
[사용자 지정의 보안 의미](security-implications-of-customization.md)

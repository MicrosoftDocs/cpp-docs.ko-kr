---
description: '자세히 알아보기: 자동화 서버'
title: 자동화 서버
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: e97bcf524b96e459cd1a3caddec7cdaf0c030962
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339828"
---
# <a name="automation-servers"></a>자동화 서버

자동화를 사용 하면 응용 프로그램에서 다른 응용 프로그램에 구현 된 개체를 조작 하거나 개체를 조작할 수 있도록 노출할 수 있습니다. 자동화 서버는 자동화 된 개체 (자동화 개체 라고 함)를 다른 응용 프로그램 ( [자동화 클라이언트](automation-clients.md))에 노출 하는 응용 프로그램입니다. Automation 서버를 자동화 구성 요소 라고도 합니다.

자동화 개체를 노출 하면 클라이언트가 서버에서 사용할 수 있도록 하는 개체 및 기능에 직접 액세스 하 여 특정 프로시저를 자동화할 수 있습니다. 이러한 방식으로 개체를 노출 하면 응용 프로그램에서 다른 응용 프로그램에 유용한 기능을 제공할 때 유용 합니다. 예를 들어 워드 프로세서는 다른 프로그램에서 사용할 수 있도록 맞춤법 검사 기능을 노출할 수 있습니다. 따라서 개체의 노출을 통해 공급 업체는 다른 응용 프로그램의 미리 만들어진 기능을 사용 하 여 응용 프로그램의 기능을 향상 시킬 수 있습니다.

이러한 자동화 개체는 속성 및 메서드를 외부 인터페이스로 가집니다. 속성은 Automation 개체의 명명 된 특성입니다. 속성은 c + + 클래스의 데이터 멤버와 유사 합니다. 메서드는 자동화 개체에서 작동 하는 함수입니다. 메서드는 c + + 클래스의 public 멤버 함수와 비슷합니다.

> [!NOTE]
> 속성은 c + + 데이터 멤버와 유사 하지만 직접 액세스할 수는 없습니다. 투명 한 액세스를 제공 하려면 액세스 하기 위해 get/set 멤버 함수 쌍을 사용 하 여 자동화 개체에서 내부 변수를 설정 합니다.

자동화를 통해 잘 정의 된 공용 인터페이스를 통해 응용 프로그램 기능을 노출 함으로써 다양 한 응용 프로그램 관련 매크로 언어가 아닌 Microsoft Visual Basic 같은 단일 일반 프로그래밍 언어로 응용 프로그램을 빌드할 수 있습니다.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a> Automation 서버 지원

Visual C++ 및 MFC 프레임 워크는 자동화 서버에 대 한 광범위 한 지원을 제공 합니다. 자동화 서버를 만드는 데 필요한 많은 오버 헤드를 처리 하므로 응용 프로그램의 기능에 대 한 노력을 집중할 수 있습니다.

자동화를 지 원하는 프레임 워크의 주요 메커니즘은 OLE의 메서드 및 속성을 노출 하는 데 필요한 선언 및 호출로 확장 되는 매크로 집합인 디스패치 맵입니다. 일반적인 디스패치 맵은 다음과 같습니다.

[!code-cpp[NVC_MFCAutomation#1](codesnippet/cpp/automation-servers_1.cpp)]

[클래스 마법사](reference/mfc-class-wizard.md) 와 클래스 뷰는 디스패치 맵을 유지 관리 하는 데 도움이 됩니다. 클래스에 새 메서드나 속성을 추가 하는 경우 Visual Studio는 `DISP_FUNCTION` `DISP_PROPERTY` 클래스 이름, 외부 및 내부 이름, 메서드 또는 속성 및 데이터 형식을 나타내는 매개 변수를 사용 하 여 해당 또는 매크로를 추가 합니다.

**클래스 추가** 대화 상자는 자동화 클래스의 선언과 해당 속성 및 작업의 관리를 간소화 하기도 합니다. 클래스 추가 대화 상자를 사용 하 여 클래스를 프로젝트에 추가 하는 경우 해당 기본 클래스를 지정 합니다. 기본 클래스에서 자동화를 허용 하는 경우 클래스 추가 대화 상자에는 새 클래스가 자동화를 지원 해야 하는지 여부를 지정 하는 데 사용 하는 컨트롤이 표시 됩니다 .이 대화 상자에는 "OLE 생성 가능" (즉, COM 클라이언트의 요청에서 클래스의 개체를 만들 수 있는지 여부) 및 사용할 COM 클라이언트의 외부 이름이 표시 됩니다.

그런 다음 **클래스 추가** 대화 상자에서 사용자가 지정한 OLE 기능에 적절 한 매크로를 포함 하 여 클래스 선언을 만듭니다. 또한 클래스의 멤버 함수 구현에 대 한 기본 코드를 추가 합니다.

MFC 응용 프로그램 마법사는 자동화 서버 응용 프로그램을 시작 하는 것과 관련 된 단계를 간소화 합니다. **고급 기능** 페이지에서 **자동화** 확인란을 선택 하는 경우 MFC 응용 프로그램 마법사는 자동화 `InitInstance` 개체를 등록 하 고 응용 프로그램을 자동화 서버로 실행 하는 데 필요한 호출을 응용 프로그램의 함수에 추가 합니다.

### <a name="what-do-you-want-to-do"></a>뭘 하고 싶으세요

- [Automation 클라이언트에 대해 알아보기](automation-clients.md)

- [CCmdTarget 클래스에 대 한 자세한 정보](reference/ccmdtarget-class.md)

- [COleDispatchDriver 클래스에 대 한 자세한 정보](reference/coledispatchdriver-class.md)

## <a name="see-also"></a>참고 항목

[Automation](automation.md)<br/>
[MFC 응용 프로그램 마법사](reference/mfc-application-wizard.md)

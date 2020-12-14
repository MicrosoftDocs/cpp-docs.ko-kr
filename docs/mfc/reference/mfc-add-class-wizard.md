---
description: '자세한 정보: MFC 클래스 추가 마법사'
title: MFC 클래스 추가 마법사
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 3f405b0f5523a183fd546790e0823e7a5e6bbbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219254"
---
# <a name="mfc-add-class-wizard"></a>MFC 클래스 추가 마법사

이 코드 마법사를 사용 하 여 기존 MFC 프로젝트에 클래스를 추가 하거나 MFC를 지 원하는 ATL 프로젝트에 클래스를 추가할 수 있습니다. Mfc를 지 원하는 Win32 프로젝트에 MFC 클래스를 추가할 수도 있습니다. 프로젝트를 만들 때 지정한 기능에 따라이 대화 상자에서 사용할 수 있는 옵션이 결정 됩니다. 마법사에 액세스 하려면 [클래스 마법사](mfc-class-wizard.md)에서 **클래스 추가** 를 클릭 합니다.

![MFC 클래스 추가 마법사](media/add-mfc-class-wizard.png "MFC 클래스 추가 마법사")

## <a name="names"></a>이름

이 페이지에서 클래스 이름, 기본 클래스 및 새 클래스의 파일 이름을 지정 합니다.

- **클래스 이름**

  새 클래스의 이름을 지정 하 고이 페이지의 Id 및 파일 이름에 대 한 기본 기준을 제공 합니다. C + + 클래스는 일반적으로 "C"로 시작 하므로 예를 들어 "CMyClass"는 "MyClass. h"가 됩니다.

- **기본 클래스**

  새 클래스에 대 한 기본 클래스의 이름을 지정 합니다. 기본적으로 기본 클래스는 [CWnd](../../mfc/reference/cwnd-class.md)입니다. 선택한 기본 클래스에 따라이 페이지의 다른 상자가 활성 상태 인지 여부가 결정 됩니다.

  기본 클래스로 설정한 클래스의 형식에 따라 클래스에 대화 상자 ID 또는 리소스 ID가 있는지 여부가 결정 됩니다. 클래스의 일반적인 형식은 다음과 같습니다.

  - [Cbutton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md)또는 [CDocument](../../mfc/reference/cdocument-class.md)와 같은 클래스는 대화 상자 id 또는 리소스 id가 필요 하지 않습니다. 이러한 클래스는 대화 상자 또는 리소스 ID를 사용 하지 않습니다. 기본 클래스에 대해 이러한 클래스 중 하나를 선택 하면 대화 상자 **ID** 상자와 **DHTML 리소스 ID** 상자가 흐리게 표시 됩니다.

  - 대화 상자 ID가 필요한 [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md)또는 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)와 같은 클래스입니다.

  - [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)클래스에는 대화 상자 ID, DHTML 리소스 ID 및 HTML 파일 이름이 필요 합니다.

  대화 상자 ID를 필요로 하는 클래스의 경우 [리소스 편집기](../../windows/resource-editors.md) 를 사용 하 여 대화 상자 리소스를 만들고, [클래스 마법사](mfc-class-wizard.md)에서 해당 id를 할당 하 고, 해당 리소스 ID와 연결 된 클래스를 만드는 것이 더 효율적일 수 있습니다. 표준 Windows 대화 상자를 만드는 방법에 대 한 자세한 내용은 [새 대화 상자 만들기](../../windows/creating-a-new-dialog-box.md) 를 참조 하세요.

  > [!NOTE]
  > 먼저 대화 상자 리소스를 만들고에서 새 클래스를 파생 하는 경우 `CDHtmlDialog` 기본 대화 상자에 표시 되는 표준 Windows **확인** 및 **취소** 단추를 삭제 합니다. 표준 Windows 대화 상자는 자체 **확인** 및 **취소** 단추가 포함 된 DHTML 폼을 호스팅합니다.

  대화 상자에는 Windows 컨트롤과 DHTML 컨트롤이 모두 포함 될 수 있지만 권장 되지는 않습니다.

- **대화 상자 ID**

  `CDialog`,, `CFormView` 또는를 `CPropertyPage` `CDHtmlDialog` **기본 클래스로** 선택한 경우 대화 상자의 ID를 지정 합니다.

- **.h 파일**

  새 개체 클래스에 대한 헤더 파일의 이름을 설정합니다. 기본적으로 이 이름은 **클래스 이름** 에 지정한 이름을 기반으로 합니다. 파일 이름을 선택한 위치에 저장하거나 클래스 선언을 기존 파일에 추가하려면 줄임표 단추를 클릭합니다. 기존 파일을 선택하면 마법사에서 **마침** 을 클릭해야 해당 파일이 선택한 위치에 저장됩니다.

  마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침** 을 클릭할 때 클래스 선언을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예** 를 클릭하여 파일을 추가하거나, **아니요** 를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.

- **.cpp 파일**

  새 개체의 클래스에 대한 구현 파일의 이름을 설정합니다. 기본적으로 이 이름은 **클래스 이름** 에 지정한 이름을 기반으로 합니다. 파일 이름을 선택한 위치에 저장하려면 줄임표 단추를 클릭합니다. 마법사에서 **마침** 을 클릭해야 해당 파일이 선택한 위치에 저장됩니다.

  마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침** 을 클릭할 때 클래스 구현을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예** 를 클릭하여 파일을 추가하거나, **아니요** 를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.

- **Active accessibility**

  생성자에서 [Enableactiveaccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) 를 호출 하 여 MFC에서 Active Accessibility에 대 한 지원을 사용 하도록 설정 합니다. 이 옵션은 [CWnd](../../mfc/reference/cwnd-class.md)에서 파생 된 클래스에 사용할 수 있습니다.

- **Automation**

  [자동화](../../mfc/automation.md)에 대 한 지원 클래스 수준을 설정 합니다. 자동화를 지 원하는 모든 클래스에서 클래스 수준의 자동화를 사용할 수 있습니다. 자동화를 지 원하는 프로젝트에도 사용할 수 있습니다. 즉, [ATL을 지 원하는](../../atl/reference/mfc-support-in-atl-projects.md)mfc 프로젝트 또는 Mfc 응용 프로그램 마법사의 [고급 기능](../../mfc/reference/advanced-features-mfc-application-wizard.md) 페이지에서 **자동화** 확인란을 선택 하는 mfc 프로젝트 중 하나입니다.

   다음 기본 클래스에는 자동화 지원을 사용할 수 없습니다.

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

## <a name="see-also"></a>참고 항목

[MFC 클래스](../../mfc/reference/adding-an-mfc-class.md)<br/>
[클래스 추가](../../ide/adding-a-class-visual-cpp.md)

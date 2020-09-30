---
title: COM 인터페이스 만들기
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 6ad8d50049d34a711937f3d1f73157ce26f69808
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509691"
---
# <a name="create-a-com-interface"></a>COM 인터페이스 만들기

Visual Studio는 COM 개체 및 자동화 클래스에 대한 COM 정의 인터페이스 및 dispinterface를 사용하는 프로젝트를 만드는 마법사와 템플릿을 제공합니다.

이러한 마법사를 사용하여 다음과 같은 세 가지 일반 작업을 수행할 수 있습니다.

- [MFC 프로젝트에 ATL 지원 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

  [MFC 애플리케이션 마법사](../mfc/reference/mfc-application-wizard.md)를 사용한 다음, **MFC에 ATL 지원 추가** 코드 마법사를 실행하여 MFC 프로젝트를 만든 후에 MFC 애플리케이션에 ATL 지원을 추가합니다. 이 지원은 MFC 실행 파일 또는 DLL 프로젝트에 추가된 단순 COM 개체에만 적용됩니다. 이러한 ATL 개체에는 여러 인터페이스가 있을 수 있습니다.

- [MFC ActiveX 컨트롤 만들기](../mfc/reference/creating-an-mfc-activex-control.md)

  [MFC ActiveX 컨트롤 마법사](../mfc/reference/mfc-activex-control-wizard.md)를 열어 .idl 파일과 컨트롤 클래스에 각각 정의된 dispinterface와 이벤트 맵이 포함된 ActiveX 컨트롤을 만듭니다.

- [ATL 컨트롤 추가](../atl/reference/adding-an-atl-control.md)

  [ATL 프로젝트 마법사](../atl/reference/atl-project-wizard.md) 및 [ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md)의 조합을 사용하여 ATL ActiveX 컨트롤을 만듭니다.

  위에서 설명한 것처럼 ATL 지원을 추가한 MFC 프로젝트에 ATL 컨트롤을 추가할 수도 있습니다. 또한 **클래스 추가** 대화 상자에서 **ATL 컨트롤**을 선택하고 MFC 프로젝트에 ATL 지원을 추가하지 않은 경우 Visual Studio는 MFC 프로젝트에 ATL 지원 추가를 확인하는 대화 상자를 표시합니다.

  이 마법사는 프로젝트 클래스에 IDL 소스 및 COM 맵을 생성합니다.

ATL 프로젝트를 열면 [클래스 추가](./adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자에서 프로젝트에 COM 인터페이스를 추가할 추가 마법사 및 템플릿을 선택할 수 있습니다. 다음 마법사를 사용하여 개체에 대한 하나 이상의 인터페이스를 설정할 수 있습니다.

- [ATL COM+ 1.0 구성 요소 마법사](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)
- [ATL Active Server Page 구성 요소 마법사](../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md)

COM 컨트롤에서 새 인터페이스를 구현할 수도 있습니다. 클래스 뷰에서 개체의 컨트롤 클래스를 마우스 오른쪽 단추로 클릭하고 [인터페이스 구현](./implementing-an-interface-visual-cpp.md#implement-interface-wizard)을 선택하기만 하면 됩니다.

> [!NOTE]
> Visual Studio는 프로젝트에 인터페이스를 추가하는 마법사를 제공하지 않습니다. [ATL 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)로 간단한 개체를 추가하여 ATL 프로젝트 또는 [MFC 프로젝트에 ATL 지원을 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)에 인터페이스를 추가할 수 있습니다. 또는 프로젝트의.idl 파일을 열고 다음을 입력하여 인터페이스를 만듭니다.

```
interface IMyInterface {
};
```

자세한 내용은 [인터페이스 구현](../ide/implementing-an-interface-visual-cpp.md) 및 [ATL 프로젝트에 개체 및 컨트롤 추가](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)를 참조하세요.

Visual C++에서는 프로젝트에 정의된 [COM 인터페이스 편집](#edit-a-com-interface) 및 확인을 위한 몇 가지 방법을 제공합니다. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)는 C++ 프로젝트의 .idl 파일에 정의된 모든 인터페이스 또는 dispinterface 아이콘을 표시합니다.

ATL 기반 COM 개체 클래스의 경우, 클래스 뷰는 ATL 클래스의 COM 맵을 읽고 ATL 클래스와 이 클래스가 구현하는 모든 인터페이스 간의 관계를 표시합니다.

클래스 뷰 및 해당 바로 가기 메뉴에서 다음과 같이 인터페이스로 작업할 수 있습니다.

- ATL 개체를 MFC 기반 애플리케이션에 추가합니다.
- 메서드, 속성 및 이벤트를 추가합니다.
- 항목을 두 번 클릭하여 항목의 인터페이스 코드로 직접 이동합니다.

## <a name="in-this-section"></a>섹션 내용

- [COM 인터페이스 편집](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>COM 인터페이스 편집

클래스 뷰 바로 가기 메뉴의 명령을 사용하여 Visual Studio C++ 프로젝트의 COM 인터페이스에 대한 새 메서드와 속성을 정의할 수 있습니다. 도구 상자에서 ActiveX 컨트롤의 이벤트를 정의할 수도 있습니다.

ATL 및 MFC 기반 COM 개체 클래스의 경우, 인터페이스를 편집하는 동시에 클래스 구현을 편집할 수 있습니다.

> [!NOTE]
> **클래스 추가** 대화 상자 외부에 정의한 인터페이스의 경우 Visual C++는 메서드 또는 속성을 .idl 파일에 추가하고, 인터페이스를 수동으로 추가한 경우에도 메서드를 구현하는 클래스에 스텁을 추가합니다.

다음 세 가지 마법사를 사용하여 기존 인터페이스를 사용자 지정할 수 있습니다. 클래스 뷰에서 사용할 수 있습니다.

|마법사|프로젝트 형식|
|------------|------------------|
|[속성 추가 마법사](./adding-a-property-visual-cpp.md#names-add-property-wizard)|ATL을 지원하는 ATL 또는 MFC 프로젝트. 속성을 추가할 인터페이스를 마우스 오른쪽 단추로 클릭합니다.<br /><br />Visual C++에서는 프로젝트 형식을 검색하고 필요에 따라 속성 추가 마법사의 옵션을 수정합니다.<br /><br />- [MFC 애플리케이션 마법사](../mfc/reference/mfc-application-wizard.md)를 사용하여 만든 프로젝트의 dispinterface의 경우 속성 추가 마법사를 호출하면 MFC 관련 옵션이 제공됩니다.<br />- MFC ActiveX 컨트롤 인터페이스의 경우, 속성 추가 마법사는 제공된 대로 사용하거나 컨트롤을 사용자 지정할 수 있는 스톡 메서드 및 속성 목록을 제공합니다.<br />- 다른 모든 인터페이스의 경우, 속성 추가 마법사는 대부분의 상황에서 유용한 옵션을 제공합니다.|
|[메서드 추가 마법사](./adding-a-method-visual-cpp.md#add-method-wizard)|ATL을 지원하는 ATL 또는 MFC 프로젝트. 메서드를 추가할 인터페이스를 마우스 오른쪽 단추로 클릭합니다.<br /><br />Visual C++에서는 프로젝트 형식을 검색하고 필요에 따라 메서드 추가 마법사의 옵션을 수정합니다.<br /><br />- [MFC 애플리케이션 마법사](../mfc/reference/mfc-application-wizard.md)를 사용하여 만든 프로젝트의 dispinterface의 경우 메서드 추가 마법사를 사용하면 MFC 관련 옵션을 제공합니다.<br />- MFC ActiveX 컨트롤 인터페이스의 경우, 메서드 추가 마법사는 제공된 대로 사용하거나 컨트롤을 사용자 지정할 수 있는 스톡 메서드 및 속성 목록을 제공합니다.<br />- 다른 모든 인터페이스의 경우, **메서드 추가** 마법사는 대부분의 상황에서 유용한 옵션을 제공합니다.|

COM 컨트롤에서 새 인터페이스를 구현할 수도 있습니다. 클래스 뷰에서 개체의 컨트롤 클래스를 마우스 오른쪽 단추로 클릭하고 [인터페이스 구현](./implementing-an-interface-visual-cpp.md#implement-interface-wizard)을 선택하기만 하면 됩니다.

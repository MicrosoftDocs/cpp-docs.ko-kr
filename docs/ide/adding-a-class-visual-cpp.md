---
title: 클래스 추가
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: b1c64505a63b8720ed7aee855f2bbbbdb9134e28
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96188837"
---
# <a name="add-a-class"></a>클래스 추가

Visual Studio C++ 프로젝트에서 클래스를 추가하려면 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** 를 선택한 다음, **클래스** 를 선택합니다. 그러면 [클래스 추가 대화 상자](#add-class-dialog-box)가 열립니다.

클래스를 추가할 때 MFC 또는 ATL에 이미 존재하는 클래스와 다른 이름을 지정해야 합니다. 라이브러리에 이미 있는 이름을 지정하면 IDE에는 오류 메시지가 표시됩니다.

프로젝트 명명 규칙에서 기존 이름을 사용해야 하는 경우 C++가 대/소문자를 구분하기 때문에 이름 중 하나 이상의 대/소문자를 변경할 수 있습니다. 예를 들어 클래스를 `CDocument`로 명명할 수 없지만 이름을 `cdocument`로 지정할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

- [어떤 종류의 클래스를 추가하시겠습니까?](#what-kind-of-class-do-you-want-to-add)
- [클래스 추가 대화 상자](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>어떤 종류의 클래스를 추가하시겠습니까?

**클래스 추가** 대화 상자의 왼쪽 창에서 **Visual C++** 노드를 확장하면 설치된 템플릿이 여러 개로 그룹화되어 표시됩니다. 그룹에는 **CLR**, **ATL**, **MFC** 및 **C++** 이 포함됩니다. 그룹을 선택하면 해당 그룹에서 사용 가능한 템플릿 목록이 가운데 창에 표시됩니다. 각 템플릿에는 클래스에 필요한 파일 및 소스 코드가 포함되어 있습니다.

새 클래스를 생성하려면 중간 창에서 템플릿을 선택하고, **이름** 상자에 클래스의 이름을 입력하고, **추가** 를 선택합니다. 그러면 클래스의 옵션을 지정할 수 있도록 **클래스 추가 마법사** 가 열립니다.

- MFC 클래스를 만드는 방법에 대한 자세한 내용은 [MFC 클래스](../mfc/reference/adding-an-mfc-class.md)를 참조하세요.

- ATL 클래스를 만드는 방법에 대한 자세한 내용은 [ATL 단순 개체](../atl/reference/adding-an-atl-simple-object.md)를 참조하세요.

> [!NOTE]
> 템플릿 **MFC에 ATL 지원 추가** 에서는 클래스를 만들지 않지만 대신 ATL을 사용하도록 프로젝트를 구성합니다. 자세한 내용은 [MFC 프로젝트의 ATL 지원](../mfc/reference/adding-atl-support-to-your-mfc-project.md)을 참조하세요.

C++ 클래스가 MFC, ATL 또는 CLR을 사용하지 않도록 하려면 설치된 템플릿의 **C++** 그룹에서 **C++ 클래스** 템플릿을 사용합니다. 자세한 내용은 [일반 C++ 클래스 추가](../ide/adding-a-generic-cpp-class.md)를 참조하세요.

두 종류의 양식 기반 C++클래스가 지원됩니다. 첫 번째 [CFormView 클래스](../mfc/reference/cformview-class.md)는 MFC 클래스를 만듭니다. 두 번째는 Windows Forms CLR 클래스를 만듭니다.

## <a name="add-class-dialog-box"></a>클래스 추가 대화 상자

**클래스 추가** 대화 상자에는 다음을 수행할 수 있는 템플릿이 있습니다.

- 사용 가능한 경우 해당 코드 마법사를 엽니다. 자세한 내용은 [코드 마법사로 기능 추가](../ide/adding-functionality-with-code-wizards-cpp.md)를 참조하세요.

   \- 또는 -

- 프로젝트에 적절한 파일 및 소스 코드를 추가하여 새 클래스를 자동으로 만듭니다.

**클래스 추가** 대화 상자는 **프로젝트** 메뉴, **솔루션 탐색기** 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 액세스할 수 있습니다.

> [!NOTE]
> 현재 프로젝트에 적합하지 않은 클래스를 추가하려고 하면 오류 메시지가 표시됩니다. **확인** 을 선택하여 **클래스 추가** 대화 상자로 돌아갑니다.

### <a name="add-class-templates"></a>클래스 추가 템플릿

NET, ATL, MFC 및 제네릭이라는 네 가지 범주의 **클래스 추가** 템플릿이 있습니다. **템플릿** 창에서 템플릿을 선택하면 선택 항목을 설명하는 텍스트가 **범주** 및 **템플릿** 창 아래에 나타납니다.

#### <a name="net"></a>.NET

|템플릿|마법사|
|--------------|------------|
|ASP.NET 웹 서비스|사용할 수 없음|
|구성 요소 클래스(.NET)|사용할 수 없음|
|설치 관리자 클래스(.NET)|사용할 수 없음|
|사용자 정의 컨트롤(.NET)|사용할 수 없음|
|Windows Form(.NET)|사용할 수 없음|

#### <a name="atl"></a>ATL

|템플릿|마법사|
|--------------|------------|
|MFC에 ATL 지원 추가|사용할 수 없음|
|ATL 컨트롤|[ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md)|
|ATL 대화 상자|[ATL 대화 상자 마법사](../atl/reference/atl-dialog-wizard.md)|
|ATL 단순 개체|[ATL 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)|
|WMI 이벤트 공급자|WMI 이벤트 공급자 마법사|
|WMI 인스턴스 공급자|WMI 인스턴스 공급자 마법사|

#### <a name="mfc"></a>MFC

|템플릿|마법사|
|--------------|------------|
|MFC 클래스|[MFC 클래스 추가 마법사](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>일반 클래스

|템플릿|마법사|
|--------------|------------|
|일반 C++ 클래스|[일반 C++ 클래스 마법사](./adding-a-generic-cpp-class.md#generic-c-class-wizard)|

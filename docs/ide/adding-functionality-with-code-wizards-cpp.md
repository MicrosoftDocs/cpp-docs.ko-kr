---
description: '자세한 정보: 코드 마법사로 기능 추가(C++)'
title: 코드 마법사로 기능 추가(C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: b411f3d36ebfa7af63e59a77ee85968de1dc3d24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240743"
---
# <a name="adding-functionality-with-code-wizards-c"></a>코드 마법사로 기능 추가(C++)

프로젝트가 만들어졌으면 프로젝트의 기능을 변경하거나 추가하려고 합니다. 이러한 작업에는 새 클래스 만들기, 새 멤버 함수 및 변수 추가, 자동화 메서드 및 속성 추가 등이 포함됩니다. 코드 마법사는 이러한 모든 작업을 수행할 수 있도록 설계되었습니다.

> [!NOTE]
> 다음과 같이 거의 사용되지 않는 코드 마법사는 Visual Studio 2019에서 제거되었습니다. ATL 및 MFC에 대한 일반 지원은 이러한 마법사를 제거해도 영향을 받지 않습니다. 이러한 기술에 대한 샘플 코드는 Microsoft Docs 및 VCSamples GitHub 리포지토리에 보관됩니다.

- ATL COM+ 1.0 구성 요소 마법사
- ATL Active Server Pages 구성 요소 마법사
- ATL OLE DB 공급자 마법사
- ATL 속성 페이지 마법사
- ATL OLE DB 소비자 마법사
- MFC ODBC 소비자
- ActiveX 컨트롤의 MFC 클래스
- TypeLib의 MFC 클래스

> [!NOTE]
> 메시지 처리기를 추가하고, 메시지를 이러한 메시지에 매핑하고, [MFC 클래스 마법사](../mfc/reference/mfc-class-wizard.md)를 사용하여 MFC 가상 함수를 재정의할 수 있습니다.

## <a name="accessing-c-code-wizards"></a>C++ 코드 마법사 액세스

C++ 코드 마법사에 액세스할 수 있는 세 가지 위치가 있습니다.

- **프로젝트** 메뉴에서 **새 항목 추가** 명령을 사용하면 프로젝트에 새 파일을 추가하는 데 유용한 `Add New Item` 대화 상자를 표시할 수 있습니다. **클래스 추가** 명령은 프로젝트에 추가할 수 있는 각 클래스 유형에 대한 마법사를 여는 [클래스 추가](./adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자를 표시합니다. MFC 클래스의 경우 [MFC 클래스 마법사](../mfc/reference/mfc-class-wizard.md)를 사용합니다. **리소스 추가** 명령은 프로젝트에 추가할 리소스를 만들거나 선택할 수 있는 [리소스 추가](../windows/how-to-create-a-resource-script-file.md) 대화 상자를 표시합니다.

   [클래스 뷰]에서 프로젝트의 클래스 또는 인터페이스를 강조 표시하는 경우 표시되는 **프로젝트** 메뉴의 명령은 다음과 같습니다.

  - **인터페이스 구현**(컨트롤 클래스에만 해당)

  - **함수 추가**

  - **변수 추가**

  - **연결 지점 추가**(ATL 클래스에만 해당)

  - **메서드 추가**(인터페이스에만 해당)

  - **속성 추가**(인터페이스에만 해당)

  - **이벤트 추가**(컨트롤 클래스에만 해당)

- **솔루션 탐색기** 에서 폴더를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **추가** 를 클릭하면, 새 파일이나 기존 파일, 더 많은 폴더, 항목, 클래스, 리소스 및 웹 참조를 프로젝트에 추가할 수 있습니다.

- [클래스 뷰 창](/visualstudio/ide/viewing-the-structure-of-code)에서 적절한 노드를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **추가** 를 클릭하면, 함수, 변수, 클래스, 속성, 메서드, 이벤트, 인터페이스, 연결 지점 또는 다른 코드를 프로젝트에 추가할 수 있습니다.

   > [!NOTE]
   > Visual Studio는 프로젝트에 인터페이스를 추가하는 마법사를 제공하지 않습니다. [ATL 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)로 간단한 개체를 추가하여 ATL 프로젝트에 인터페이스를 추가하거나 [MFC 프로젝트에 ATL 지원을 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)할 수 있습니다. 또는 프로젝트의.idl 파일을 열고 다음을 입력하여 인터페이스를 만듭니다.

    ```IDL
    interface IMyInterface {
    };
    ```

   자세한 내용은 [인터페이스 구현](../ide/implementing-an-interface-visual-cpp.md) 및 [ATL 프로젝트에 개체 및 컨트롤 추가](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)를 참조하세요.

   |코드 마법사에 액세스하는 위치|Description|
   |-----------------------------|-----------------|
   |새 항목 추가|새 항목 코드 추가 마법사는 소스 파일을 프로젝트에 추가합니다. 필요한 경우 프로젝트 빌드 엔진에서 찾아야 하는 파일이 포함되는 추가 디렉터리가 만들어집니다. [항목 추가] 아이콘에서 사용할 수 있는 코드 마법사는 다음과 같습니다.<br /><br />- C++ 소스 파일 추가(.cpp, .h, .idl, .rc, .srf, .def, .rgs)<br />- 웹 개발 파일 추가(.html, .asp, .css, .xml)<br />- 유틸리티 및 리소스 파일 추가(.bmp, .cur, .ico, .rct, .sql, .txt)<br /><br />이러한 코드 마법사는 일반적으로 정보를 요청하지 않고 개발 트리에 파일을 추가합니다. 속성 창에서 파일의 이름을 바꿀 수 있습니다.|
   |솔루션 탐색기|솔루션 탐색기에서 사용할 수 있는 코드 마법사는 항목을 마우스 오른쪽 단추로 클릭할 때 커서 초점이 있는 위치에 따라 다릅니다. 항목을 마우스 오른쪽 단추로 클릭할 때 **추가** 옵션이 표시되지 않으면 개발 트리에서 커서를 한 수준 위로 이동하고 다시 시도합니다. 커서가 어디에 있든 코드 마법사는 항상 개발 트리의 적절한 위치에 추가 코드를 배치합니다. 솔루션 탐색기에서 사용할 수 있는 코드 마법사는 다음과 같습니다.<br /><br />- 클래스 추가(새 코드 마법사가 포함된 **클래스 추가** 대화 상자 열기)<br />- 리소스 추가(새로 만들기, 가져오기 또는 사용자 지정)<br />- 웹 참조 추가|
   |클래스 뷰|클래스 뷰에서 사용할 수 있는 코드 마법사는 항목을 마우스 오른쪽 단추로 클릭할 때 커서 초점이 있는 위치에 따라 다릅니다. 항목을 마우스 오른쪽 단추로 클릭할 때 **추가** 옵션이 표시되지 않으면 클래스 트리에서 커서를 한 수준 위로 이동하고 다시 시도합니다. 커서가 어디에 있든 코드 마법사는 항상 개발 트리의 적절한 위치에 추가 코드를 배치합니다. 클래스 뷰에서 사용할 수 있는 코드 마법사는 다음과 같습니다.<br /><br />- [멤버 함수 추가](../ide/adding-a-member-function-visual-cpp.md)<br />- [멤버 변수 추가](../ide/adding-a-member-variable-visual-cpp.md)<br />- [클래스 추가](../ide/adding-a-class-visual-cpp.md)<br />- [인터페이스 구현](./implementing-an-interface-visual-cpp.md#implement-interface-wizard)(컨트롤 클래스에만 해당)<br />- [연결 지점 추가](./implementing-a-connection-point-visual-cpp.md#implement-connection-point-wizard)(ATL 클래스에만 해당)<br />- [메서드 추가](./adding-a-method-visual-cpp.md#add-method-wizard)(인터페이스에만 해당)<br />- [속성 추가](./adding-a-property-visual-cpp.md#names-add-property-wizard)(인터페이스에만 해당)<br />- [이벤트 추가](./adding-an-event-visual-cpp.md#add-event-wizard)(컨트롤 클래스에만 해당)<br /><br />[클래스 추가]를 선택하면 모든 새 클래스 추가 코드 마법사에 액세스할 수 있는 **클래스 추가** 대화 상자를 엽니다.|

## <a name="see-also"></a>참고 항목

[가상 함수 재정의](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Visual Studio에서 C++ 코드 베이스 탐색](../ide/navigate-code-cpp.md)<br>
[Visual Studio의 C++ 프로젝트 형식](../build/reference/visual-cpp-project-types.md)<br>
[Visual Studio C++ 프로젝트용으로 만든 파일 형식](../build/reference/file-types-created-for-visual-cpp-projects.md)

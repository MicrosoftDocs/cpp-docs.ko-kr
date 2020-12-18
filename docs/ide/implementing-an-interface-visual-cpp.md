---
description: '자세한 정보: 인터페이스 구현'
title: 인터페이스 구현
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 202471577ec72f4cc28fa5cdceb3566d60e04653
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313218"
---
# <a name="implement-an-interface"></a>인터페이스 구현

인터페이스를 구현하려면 ATL COM 애플리케이션 또는 ATL 지원이 포함된 MFC 애플리케이션으로 프로젝트를 만들어야 합니다. [ATL 프로젝트 마법사](../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들거나 [MFC 애플리케이션에 ATL 개체를 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션에 ATL 지원을 구현할 수 있습니다.

프로젝트를 생성한 후 인터페이스를 구현하려면 먼저 ATL 개체를 추가해야 합니다. ATL 프로젝트에 개체를 추가하는 마법사 목록은 [ATL 프로젝트에 개체 및 컨트롤 추가](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)를 참조하세요.

> [!NOTE]
> 이 마법사는 ATL 대화 상자, ATL을 사용하는 XML Web services, 성능 개체 또는 성능 카운터를 지원하지 않습니다.

[ATL 컨트롤을 추가](../atl/reference/adding-an-atl-control.md)하면 기본 인터페이스를 구현할지 여부를 지정할 수 있습니다. 기본 인터페이스는 해당 마법사의 [인터페이스](../atl/reference/interfaces-atl-control-wizard.md) 페이지에 나열되고 atlcom.h에서 정의됩니다.

개체 또는 컨트롤을 추가하면 인터페이스 구현 마법사를 사용하여 모든 사용 가능한 형식 라이브러리에 있는 다른 인터페이스를 구현할 수 있습니다.

새 인터페이스를 추가하는 경우 프로젝트의 .idl 파일에 수동으로 추가해야 합니다. 자세한 내용은 [ATL 프로젝트에 새 인터페이스 추가](../atl/reference/adding-a-new-interface-in-an-atl-project.md)를 참조하세요.

**인터페이스를 구현하려면:**

1. 클래스 뷰에서 ATL 개체의 클래스 이름을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가** 를 선택한 다음, **인터페이스 구현** 을 선택하여 [인터페이스 구현 마법사](#implement-interface-wizard)를 표시합니다.

1. 적절한 형식 라이브러리에서 구현할 인터페이스를 선택하고 **마침** 을 선택합니다.

1. 클래스 뷰에서 개체의 기본 및 인터페이스 노드를 확장하여 구현한 인터페이스를 확인합니다. 그런 다음, 인터페이스의 노드를 확장하여 사용 가능한 속성, 메서드 및 이벤트를 확인합니다.

   > [!NOTE]
   > [개체 브라우저](/visualstudio/ide/viewing-the-structure-of-code)를 사용하여 인터페이스의 멤버를 검사할 수도 있습니다.

## <a name="in-this-section"></a>섹션 내용

- [인터페이스 구현 마법사](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>인터페이스 구현 마법사

COM 개체의 인터페이스를 구현합니다. 많은 인터페이스의 구현은 Visual Studio 및 Windows와 함께 사용할 수 있는 COM 라이브러리에 포함되어 있습니다. 인터페이스 구현은 해당 개체의 인스턴스를 만드는 경우 개체와 연결됩니다. 또한 개체에서 제공하는 서비스를 제공합니다.

인터페이스 및 구현 설명은 Windows SDK에서 [인터페이스 및 인터페이스 구현](/windows/win32/com/interfaces-and-interface-implementations)을 참조하세요.

- **구현할 인터페이스 위치**

  인터페이스를 만들었으므로 형식 라이브러리의 위치를 지정합니다.

  |옵션|Description|
  |------------|-----------------|
  |**프로젝트**|형식 라이브러리는 프로젝트의 일부입니다.|
  |**레지스트리**|형식 라이브러리가 시스템에 등록되어 있습니다. 등록된 형식 라이브러리는 **사용 가능한 형식 라이브러리** 에 나열됩니다.|
  |**최근에 사용한 파일**|형식 라이브러리가 반드시 시스템에 등록되지는 않지만 파일에는 포함됩니다. **위치** 에 파일 위치를 입력합니다.|

- **사용 가능한 형식 라이브러리**

  구현할 수 있는 인터페이스 정의가 포함된 사용 가능한 형식 라이브러리를 표시합니다. **구현할 인터페이스 위치** 에서 **파일** 을 선택한 경우 이 상자는 변경할 수 없습니다.

- **위치**

  **사용 가능한 형식 라이브러리** 목록에서 현재 선택한 형식 라이브러리의 위치를 표시합니다. **구현할 인터페이스 위치** 에서 **파일** 을 선택한 경우 줄임표 단추를 선택하여 사용할 형식 라이브러리가 포함된 파일을 찾습니다.

- **인터페이스**

  **사용 가능한 형식 라이브러리** 상자에서 현재 선택된 형식 라이브러리에 정의가 포함된 인터페이스를 표시합니다.

  > [!NOTE]
  > 선택한 개체에서 이미 구현된 것과 동일한 이름의 인터페이스는 **인터페이스** 상자에 표시되지 않습니다.

  |전송 단추|설명|
  |---------------------|-----------------|
  |**>**|**인터페이스 구현** 목록에 **인터페이스** 목록에서 현재 선택된 인터페이스 이름을 추가합니다.|
  |**>>**|**인터페이스 구현** 목록에 **인터페이스** 목록에서 사용 가능한 모든 인터페이스 이름을 추가합니다.|
  |**\<**|**인터페이스 구현** 목록에서 현재 선택된 인터페이스 이름을 제거합니다.|
  |**\<\<**|**인터페이스 구현** 목록에서 현재 나열된 모든 인터페이스 이름을 제거합니다.|

- **인터페이스 구현**

  개체에서 구현하기 위해 선택한 인터페이스의 이름을 표시합니다.

  > [!NOTE]
  > `IDispatch`에서 파생된 2개 이상의 인터페이스를 포함하거나 이미 다른 인터페이스에서 파생된 인터페이스를 클래스에서 구현하려고 하는 경우 COM_MAP 항목을 구분해야 합니다. 자세한 내용은 [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)를 참조하세요.

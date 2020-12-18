---
description: '자세한 정보: 연결점 구현'
title: 연결점 구현
ms.date: 05/14/2019
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: bee04d28036ca5a2dfb0f4913adf39f1fdcca565
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281160"
---
# <a name="implement-a-connection-point"></a>연결점 구현

연결 지점 구현 마법사를 사용하여 연결 지점을 구현하려면 ATL COM 애플리케이션 또는 ATL 지원이 포함된 MFC 애플리케이션으로 프로젝트를 만들어야 합니다. [ATL 프로젝트 마법사](../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들거나 [MFC 애플리케이션에 ATL 개체를 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션에 ATL 지원을 구현할 수 있습니다.

> [!NOTE]
> MFC 프로젝트의 연결점 구현에 대한 자세한 내용은 [연결점](../mfc/connection-points.md)을 참조하세요.

프로젝트를 생성한 후 연결 지점을 구현하려면 먼저 ATL 개체를 추가해야 합니다. ATL 프로젝트에 개체를 추가하는 마법사 목록은 [ATL 프로젝트에 개체 및 컨트롤 추가](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)를 참조하세요.

> [!NOTE]
> 이 마법사는 ATL 서버, 성능 개체 또는 성능 카운터를 사용하여 만든 XML Web services, ATL 대화 상자를 지원하지 않습니다.

연결 가능한 개체(즉, 원본)는 각 송신 인터페이스에 대한 연결점을 보여줄 수 있습니다. 각 송신 인터페이스는 클라이언트가 개체(예: 싱크)에 구현할 수 있습니다. 자세한 내용은 [ATL 연결점](../atl/atl-connection-points.md)을 참조하세요.

**연결점을 구현하려면:**

1. 클래스 뷰에서 ATL 개체의 클래스 이름을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가** 를 선택한 다음, **연결점 추가** 를 선택하여 [연결점 구현 마법사](#implement-connection-point-wizard)를 표시합니다.

1. 적절한 형식 라이브러리에서 구현할 연결점 인터페이스를 선택하고 **마침** 을 선택합니다.

1. 클래스 뷰에서 각 연결 지점에 대해 생성된 프록시 클래스를 검사합니다. 클래스는 CProxy *InterfaceName*\<T>로 나타나며 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)에서 파생됩니다.

1. 연결 지점 클래스를 두 번 클릭하여 연결 지점 클래스의 정의를 표시합니다.

   - 사용자 고유의 프로젝트 인터페이스에 대한 연결점을 구현하는 경우 다음 정의가 나타납니다.

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - 로컬 인터페이스를 구현하는 경우 클래스 본문에 메서드 및 속성이 나타납니다.

   - 다른 인터페이스의 연결 지점을 구현하는 경우 각각 이름이 `Fire_`로 시작하는 인터페이스의 메서드가 정의에 포함됩니다.

## <a name="in-this-section"></a>섹션 내용

- [연결점 구현 마법사](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>연결점 구현 마법사

이 마법사는 COM 개체의 연결 지점을 구현합니다. 연결 가능한 개체(즉, 원본)는 자체 인터페이스 또는 모든 송신 인터페이스에 대한 연결점을 보여줄 수 있습니다. MSVC 및 Windows는 모두 송신 인터페이스가 있는 형식 라이브러리를 제공합니다. 각 송신 인터페이스는 클라이언트가 개체(예: 싱크)에 구현할 수 있습니다.

자세한 내용은 [ATL 연결점](../atl/atl-connection-points.md)을 참조하세요.

- **사용 가능한 형식 라이브러리**

  연결점을 구현할 수 있는 인터페이스 정의가 포함된 사용 가능한 형식 라이브러리를 표시합니다. 줄임표 단추를 선택하여 사용할 형식 라이브러리가 포함된 파일을 찾습니다.

- **위치**

  **사용 가능한 형식 라이브러리** 목록에서 현재 선택한 형식 라이브러리의 위치를 표시합니다.

- **인터페이스**

  **사용 가능한 형식 라이브러리** 상자에서 현재 선택된 형식 라이브러리에 정의가 포함된 인터페이스를 표시합니다.

  |전송 단추|설명|
  |---------------------|-----------------|
  |**>**|**인터페이스** 목록에서 현재 선택된 인터페이스 이름을 **연결 지점 구현** 목록에 추가합니다.|
  |**>>**|**인터페이스** 목록에서 사용 가능한 모든 인터페이스 이름을 **연결 지점 구현** 목록에 추가합니다.|
  |**\<**|**연결 지점 구현** 목록에서 현재 선택된 인터페이스 이름을 제거합니다.|
  |**\<\<**|**연결 지점 구현** 목록에서 현재 나열된 모든 인터페이스 이름을 제거합니다.|

- **연결 지점 구현**

  **마침** 을 선택하면 연결점을 구현할 인터페이스의 이름이 표시됩니다.

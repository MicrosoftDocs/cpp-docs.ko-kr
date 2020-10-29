---
title: 속성 페이지 구현
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: c9b1c0c159a15ec7d9a5c99208baa2ed6af2d6d1
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923889"
---
# <a name="implementing-property-pages"></a>속성 페이지 구현

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL 속성 페이지 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

속성 페이지는 `IPropertyPage` 또는 `IPropertyPage2` 인터페이스를 구현하는 COM 개체입니다. ATL은 [ATL 속성 페이지 마법사](../atl/reference/atl-property-page-wizard.md)의 [클래스 추가 대화 상자](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)를 통해 속성 페이지 구현을 지원합니다.

ATL을 사용하여 속성 페이지를 만들려면 다음을 수행합니다.

- ATL DLL(동적 연결 라이브러리) 서버 프로젝트를 만들거나 엽니다.

- [클래스 추가 대화 상자](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)를 열고 **ATL 속성 페이지** 를 선택합니다.

- 사용자 인터페이스가 있기 때문에 속성 페이지가 아파트 스레드인지 확인합니다.

- 페이지에 연결할 제목, 설명(문서 문자열) 및 도움말 파일을 설정합니다.

- 속성 페이지의 사용자 인터페이스 역할을 하는 컨트롤을 생성된 대화 상자 리소스에 추가합니다.

- 페이지 사용자 인터페이스의 변경 내용에 응답하여 유효성 검사를 수행하거나, 페이지 사이트를 업데이트하거나, 페이지와 관련된 개체를 업데이트합니다. 특히, 사용자가 속성 페이지를 변경하면 [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)를 호출합니다.

- 필요에 따라 아래 지침을 사용하여 `IPropertyPageImpl` 메서드를 재정의합니다.

   |IPropertyPageImpl 메서드|재정의가 필요한 작업|참고|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|페이지에 전달되는 개체 수 및 개체가 지원하는 인터페이스에 대한 기본 온전성 검사를 수행합니다.|기본 클래스 구현을 호출하기 전에 사용자 고유의 코드를 실행합니다. 설정되는 개체가 예상과 다르면 최대한 빨리 호출에 실패해야 합니다.|
   |[활성화](../atl/reference/ipropertypageimpl-class.md#activate)|페이지의 사용자 인터페이스를 초기화합니다(예: 개체의 현재 속성 값을 사용하여 대화 상자 컨트롤 설정, 동적으로 컨트롤 만들기 또는 다른 초기화 수행).|업데이트가 시도되기 전에 기본 클래스에서 대화 상자 창과 모든 컨트롤을 만들 수 있도록 고유 코드에 앞서 기본 클래스 구현을 호출합니다.|
   |[적용](../atl/reference/ipropertypageimpl-class.md#apply)|속성 설정의 유효성을 검사하고 개체를 업데이트합니다.|호출 추적밖에 하지 않으므로 기본 클래스 구현을 호출할 필요는 없습니다.|
   |[Deactivate](../atl/reference/ipropertypageimpl-class.md#deactivate)|창 관련 항목을 정리합니다.|기본 클래스 구현에서는 속성 페이지를 나타내는 대화 상자를 제거합니다. 대화 상자가 제거되기 전에 정리 작업이 필요한 경우 기본 클래스를 호출하기 전에 고유 코드를 추가해야 합니다.|

속성 페이지를 구현 하는 예제는 [예제: 속성 페이지 구현](../atl/example-implementing-a-property-page.md)을 참조 하세요.

> [!NOTE]
> 속성 페이지에서 ActiveX 컨트롤을 호스트하려는 경우 마법사 생성 클래스의 파생을 변경해야 합니다. 기본 클래스 목록에서 **Cdialogimpl \<CYourClass>** **caxdialogimpl \<CYourClass>** 되도록 바꿉니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[속성 페이지](../atl/atl-com-property-pages.md)<br/>
[ATLPages 샘플](../overview/visual-cpp-samples.md)

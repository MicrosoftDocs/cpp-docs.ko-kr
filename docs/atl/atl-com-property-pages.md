---
description: '자세한 정보: ATL COM 속성 페이지'
title: ATL COM 속성 페이지
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: 252e8a98f4f34a07a374c77fc48aacd7eee8969f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165981"
---
# <a name="atl-com-property-pages"></a>ATL COM 속성 페이지

COM 속성 페이지는 하나 이상의 COM 개체의 속성을 설정 하거나 메서드를 호출 하는 사용자 인터페이스를 제공 합니다. 속성 페이지는 디자인 타임에 컨트롤 속성을 설정할 수 있도록 하는 다양 한 사용자 인터페이스를 제공 하기 위해 ActiveX 컨트롤에서 광범위 하 게 사용 됩니다.

속성 페이지는 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 또는 [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) 인터페이스를 구현 하는 COM 개체입니다. 이러한 인터페이스는 페이지가 `site` (페이지의 컨테이너를 나타내는 com 개체) 및 여러 *개체* (속성 페이지의 사용자가 변경한 내용에 대 한 응답으로 호출 되는 com 개체)에 연결 될 수 있도록 하는 메서드를 제공 합니다. 속성 페이지 컨테이너는 속성 페이지 인터페이스에서 메서드를 호출 하 여 해당 사용자 인터페이스를 표시 하거나 숨길지 여부 및 사용자가 변경한 내용을 기본 개체에 적용 하는 시기를 페이지에 알리는 역할을 합니다.

각 속성 페이지는 속성을 설정할 수 있는 개체와 완전히 독립적으로 빌드할 수 있습니다. 속성 페이지는 특정 인터페이스 (또는 인터페이스 집합)를 이해 하 고 해당 인터페이스에서 메서드를 호출 하기 위한 사용자 인터페이스를 제공 하는 데 필요 합니다.

자세한 내용은 Windows SDK의 [속성 시트 및 속성 페이지](/windows/win32/com/property-sheets-and-property-pages) 를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[속성 페이지 지정](../atl/specifying-property-pages.md)<br/>
컨트롤에 대 한 속성 페이지를 지정 하는 단계를 나열 하 고 예제 클래스를 표시 합니다.

[속성 페이지 구현](../atl/implementing-property-pages.md)<br/>
재정의할 메서드를 포함 하 여 속성 페이지를 구현 하는 단계를 나열 합니다. 사용자 페이지 샘플 프로그램을 기반으로 하는 전체 예제를 안내 합니다.

## <a name="related-sections"></a>관련 단원

[ATLPages 샘플](../overview/visual-cpp-samples.md)<br/>
를 사용 하 여 속성 페이지를 구현 하는,가 나 페이지 샘플에 대 한 샘플 추상입니다 `IPropertyPageImpl` .

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
액티브 템플릿 라이브러리를 사용하여 프로그래밍하는 방법에 대한 개념 항목의 링크를 제공합니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)

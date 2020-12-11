---
description: '자세히 알아보기: 속성 페이지 지정'
title: 속성 페이지 지정 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
ms.openlocfilehash: 171440dde11178c85d1f636874b0b161691cb9cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157427"
---
# <a name="specifying-property-pages"></a>속성 페이지 지정

ActiveX 컨트롤을 만드는 경우 컨트롤의 속성을 설정 하는 데 사용할 수 있는 속성 페이지와 연결 하는 경우가 많습니다. 컨트롤 컨테이너는 인터페이스를 사용 `ISpecifyPropertyPages` 하 여 컨트롤의 속성을 설정 하는 데 사용할 수 있는 속성 페이지를 확인 합니다. 컨트롤에이 인터페이스를 구현 해야 합니다.

`ISpecifyPropertyPages`ATL을 사용 하 여 구현 하려면 다음 단계를 수행 합니다.

1. [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)에서 클래스를 파생 시킵니다.

1. `ISpecifyPropertyPages`클래스의 COM 맵에 항목을 추가 합니다.

1. 컨트롤과 연결 된 각 페이지에 대 한 속성 맵에 [PROP_PAGE](reference/property-map-macros.md#prop_page) 항목을 추가 합니다.

> [!NOTE]
> [ATL 컨트롤 마법사](../atl/reference/atl-control-wizard.md)를 사용 하 여 표준 컨트롤을 생성 하는 경우에는 속성 맵에 PROP_PAGE 항목만 추가 하면 됩니다. 마법사에서 다른 단계에 필요한 코드를 생성 합니다.

잘 동작 하는 컨테이너는 속성 맵의 PROP_PAGE 항목과 동일한 순서로 지정 된 속성 페이지를 표시 합니다. 일반적으로 사용자가 컨트롤에 대 한 특정 페이지를 먼저 볼 수 있도록 속성 맵의 사용자 지정 페이지에 대 한 항목 뒤에 표준 속성 페이지 항목을 두어야 합니다.

## <a name="example"></a>예제

달력 컨트롤의 다음 클래스는 인터페이스를 사용 하 여 `ISpecifyPropertyPages` 사용자 지정 날짜 페이지와 스톡 색 페이지를 통해 해당 속성을 설정할 수 있음을 컨테이너에 알립니다.

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>참고 항목

[속성 페이지](../atl/atl-com-property-pages.md)<br/>
[ATLPages 샘플](../overview/visual-cpp-samples.md)

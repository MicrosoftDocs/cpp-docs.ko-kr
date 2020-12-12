---
description: '자세한 정보: ATL 컨트롤 추가'
title: ATL 컨트롤 추가
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 91fe393a1e93deb2173ac95a42b7ab9cca339535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165708"
---
# <a name="adding-an-atl-control"></a>ATL 컨트롤 추가

이 마법사를 사용 하 여 모든 잠재적 컨테이너의 인터페이스를 지 원하는 프로젝트에 사용자 인터페이스 개체를 추가할 수 있습니다. 이러한 인터페이스를 지원 하려면 프로젝트가 ATL 응용 프로그램 또는 ATL 지원이 포함 된 MFC 응용 프로그램으로 생성 되어 있어야 합니다. [ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들거나 [MFC 애플리케이션에 ATL 개체를 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션용 ATL 지원을 구현할 수 있습니다.

## <a name="to-add-an-atl-control-to-your-project"></a>ATL 컨트롤을 프로젝트에 추가 하려면

1. **솔루션 탐색기** 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 ATL 단순 개체를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **클래스 추가** 를 클릭 합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 템플릿 창에서 **atl 컨트롤** 을 클릭 한 다음 **추가** 를 클릭 하 여 [atl 컨트롤 마법사](../../atl/reference/atl-control-wizard.md)를 표시 합니다.

**ATL 컨트롤 마법사** 를 사용 하 여 다음 세 가지 형식의 컨트롤 중 하나를 만들 수 있습니다.

- 표준 컨트롤

- 복합 컨트롤

- DHTML 컨트롤

또한 마법사의 **옵션** 페이지에서 **최소 제어** 를 선택 하 여 컨트롤의 크기를 줄이고 대부분의 컨테이너에서 사용 되지 않는 인터페이스를 제거할 수 있습니다.

## <a name="see-also"></a>참고 항목

[복합 컨트롤에 기능 추가](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)

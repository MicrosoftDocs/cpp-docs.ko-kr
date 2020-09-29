---
title: ATL 단순 개체 추가
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 85c19c483ff27bd34431ec163e3baadac1855236
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499350"
---
# <a name="adding-an-atl-simple-object"></a>ATL 단순 개체 추가

ATL (액티브 템플릿 라이브러리) 개체를 프로젝트에 추가 하려면 프로젝트를 atl 응용 프로그램 또는 ATL 지원이 포함 된 MFC 응용 프로그램으로 만들어야 합니다. [ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들거나 [MFC 애플리케이션에 ATL 개체를 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션용 ATL 지원을 구현할 수 있습니다.

새 ATL 개체를 처음 만들 때 해당 개체에 대 한 COM 인터페이스를 정의 하거나, **클래스 뷰** 바로 가기 메뉴의 [인터페이스 구현](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard) 명령을 사용 하 여 나중에 추가할 수 있습니다.

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Atl COM 프로젝트에 ATL 단순 개체를 추가 하려면

1. **솔루션 탐색기** 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 ATL 단순 개체를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 합니다.

1. 바로 가기 메뉴에서 **추가**를 클릭한 다음, **클래스 추가**를 클릭합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 **템플릿** 창에서 **atl simple Object**를 클릭 한 다음 **열기** 를 클릭 하 여 [atl 단순 개체 마법사](../../atl/reference/atl-simple-object-wizard.md)를 표시 합니다.

1. **ATL 단순 개체** 마법사의 [옵션](../../atl/reference/options-atl-simple-object-wizard.md) 페이지에서 프로젝트에 대 한 추가 옵션을 설정 합니다.

1. **마침** 을 클릭 하 여 프로젝트에 개체를 추가 합니다.

## <a name="see-also"></a>참고 항목

[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[ATL 프로젝트에 새 인터페이스 추가](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[개체에 연결 요소 추가](../../atl/adding-connection-points-to-an-object.md)<br/>
[메서드 추가](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC 클래스](../../mfc/reference/adding-an-mfc-class.md)<br/>
[일반 C++ 클래스 추가](../../ide/adding-a-generic-cpp-class.md)

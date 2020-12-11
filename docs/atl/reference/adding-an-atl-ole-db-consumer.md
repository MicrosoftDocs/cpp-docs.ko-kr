---
description: '자세한 정보: ATL OLE DB 소비자 추가'
title: ATL OLE DB 소비자 추가
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: cfd88524e369781b239bb0246ab59fcf0080a144
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159104"
---
# <a name="adding-an-atl-ole-db-consumer"></a>ATL OLE DB 소비자 추가

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](../../data/oledb/creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

::: moniker-end

::: moniker range="<=msvc-150"

이 마법사를 사용하여 프로젝트에 ATL OLE DB 소비자를 추가할 수 있습니다. ATL OLE DB 소비자는 데이터 소스에 액세스하는 데 필요한 데이터 바인딩 및 OLE DB 접근자 클래스로 구성됩니다. 프로젝트는 ATL COM 애플리케이션이나 ATL OLE DB 소비자 마법사에서 자동으로 추가하는 ATL 지원이 포함된 MFC 또는 Win32 애플리케이션으로 만든 것이어야 합니다.

> [!NOTE]
> MFC 프로젝트에 OLE DB 소비자를 추가할 수 있습니다. 소비자를 추가하면 ATL OLE DB 소비자 마법사에서 필요한 COM 지원을 프로젝트에 추가합니다. 이 예제에서는 MFC 프로젝트를 만들 때 MFC 프로젝트 애플리케이션 마법사의 **고급 기능** 페이지에서 **ActiveX 컨트롤** 확인란을 선택했다고 가정합니다. 이 확인란은 기본적으로 선택되어 있습니다. 이 옵션을 선택하면 애플리케이션이 `CoInitialize` 및 `CoUninitialize`를 호출합니다. MFC 프로젝트를 만들 때 **ActiveX 컨트롤** 을 선택하지 않은 경우 주 코드에서 `CoInitialize` 및 `CoUninitialize`를 호출해야 합니다.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>프로젝트에 ATL OLE DB 소비자를 추가하려면 다음을 수행합니다.

1. **클래스 뷰** 에서 프로젝트를 마우스 오른쪽 단추로 클릭합니다. 바로 가기 메뉴에서 **추가** 를 클릭한 다음, **클래스 추가** 를 클릭합니다.

1. Visual C++ 폴더에서 **ATL OLE DB 소비자** 아이콘을 두 번 클릭하거나 아이콘을 선택하고 **열기** 를 클릭합니다.

   ATL OLE DB 소비자 마법사가 열립니다.

1. [ATL OLE DB 소비자 마법사](../../atl/reference/atl-ole-db-consumer-wizard.md)에 설명된 대로 설정을 정의합니다.

1. **마침** 을 클릭 하 여 마법사를 닫습니다. 새로 만든 OLE DB 소비자 코드가 프로젝트에 삽입됩니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)

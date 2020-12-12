---
description: '자세한 정보: ATL 대화 상자 추가'
title: ATL 대화 상자 추가
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: 9d4abcafd5e12c6b8cffd636bf28a9e79f96e5ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165721"
---
# <a name="adding-an-atl-dialog-box"></a>ATL 대화 상자 추가

Atl 대화 상자를 프로젝트에 추가 하려면 프로젝트는 atl 프로젝트 이거나 ATL을 지 원하는 MFC 프로젝트 여야 합니다. [ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)를 사용하여 ATL 애플리케이션을 만들거나 [MFC 애플리케이션에 ATL 개체를 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하여 MFC 애플리케이션용 ATL 지원을 구현할 수 있습니다.

기본적으로 ATL 대화 상자 마법사는 [Caxdialogimpl](../../atl/reference/caxdialogimpl-class.md)에서 파생 된 대화 상자를 구현 합니다. 이 클래스에는 ActiveX 및 Windows 컨트롤 호스팅을 위한 지원이 포함 됩니다. ActiveX 컨트롤 지원의 오버 헤드를 원하지 않는 경우 마법사에서 코드를 생성 한 후에는의 모든 인스턴스를 `CAxDialogImpl` [CSimpleDialog](../../atl/reference/csimpledialog-class.md) 또는 [cdialogimpl](../../atl/reference/cdialogimpl-class.md) 기본 클래스로 바꿉니다.

> [!NOTE]
> `CSimpleDialog` Windows 공용 컨트롤만 지 원하는 모달 대화 상자를 만듭니다. `CDialogImpl` 모달 또는 모덜리스 대화 상자를 만듭니다.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>ATL 대화 상자 리소스를 프로젝트에 추가 하려면

1. [Atl 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)를 사용 하 여 atl 프로젝트를 만듭니다.

1. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **추가** 를 클릭 합니다. **클래스 추가** 를 클릭합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 **템플릿** 창에서 **ATL 대화** 상자를 클릭 합니다. **열기** 를 클릭 하 여 [ATL 대화 상자 마법사](../../atl/reference/atl-dialog-wizard.md)를 표시 합니다.

자세한 내용은 [대화 상자 구현](../../atl/implementing-a-dialog-box.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[창 클래스](../../atl/atl-window-classes.md)<br/>
[메시지 맵](../../atl/message-maps-atl.md)

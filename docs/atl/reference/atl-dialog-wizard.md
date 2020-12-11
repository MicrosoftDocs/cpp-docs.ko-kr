---
description: '자세한 정보: ATL 대화 상자 마법사'
title: ATL 대화 상자 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 2fc110f12399c0c855cb98a9d7e505180bef7b0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158883"
---
# <a name="atl-dialog-wizard"></a>ATL 대화 상자 마법사

이 마법사는 [Caxdialogimpl](../../atl/reference/caxdialogimpl-class.md)파생 된 ATL 대화 상자 개체를 프로젝트에 삽입 합니다. 에서 파생 된 대화 상자는 `CAxDialogImpl` ActiveX 컨트롤을 호스팅할 수 있습니다.

마법사에서 기본 **확인** 및 **취소** 단추가 있는 대화 상자 리소스를 만듭니다. 리소스 뷰에서 [대화 상자 편집기](../../windows/dialog-editor.md) 를 사용 하 여 대화 상자 리소스를 편집 하 고 ActiveX 컨트롤을 추가할 수 있습니다.

마법사는 헤더 파일에 [메시지 맵을](../../atl/message-maps-atl.md) 삽입 하 고 기본 클릭 이벤트를 처리 하기 위한 선언을 삽입 합니다. ATL 대화 상자에 대 한 자세한 내용은 [대화 상자 구현](../../atl/implementing-a-dialog-box.md) 을 참조 하세요.

- **짧은 이름**

   ATL 대화 상자 개체에 대 한 약식 이름을 설정 합니다. 사용자가 제공 하는 이름에 따라 해당 필드를 개별적으로 변경 하지 않는 한 클래스 이름과 파일 (.cpp 및 .h) 이름이 결정 됩니다.

- **클래스**

   만들 클래스의 이름을 설정합니다. 이 이름은 **짧은 이름** 에 지정한 이름을 기반으로 하며, 클래스 이름의 일반적인 접두사인 ‘C’가 앞에 추가됩니다.

- **.h 파일**

   새 개체 클래스에 대한 헤더 파일의 이름을 설정합니다. 기본적으로 이 이름은 **짧은 이름** 에 지정한 이름을 기반으로 합니다. 파일 이름을 선택한 위치에 저장하거나 클래스 선언을 기존 파일에 추가하려면 줄임표 단추를 클릭합니다. 기존 파일을 선택하면 마법사에서 **마침** 을 클릭해야 해당 파일이 선택한 위치에 저장됩니다.

   마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침** 을 클릭할 때 클래스 선언을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예** 를 클릭하여 파일을 추가하거나, **아니요** 를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.

- **.cpp 파일**

   새 개체의 클래스에 대한 구현 파일의 이름을 설정합니다. 기본적으로 이 이름은 **짧은 이름** 에 지정한 이름을 기반으로 합니다. 파일 이름을 선택한 위치에 저장하려면 줄임표 단추를 클릭합니다. 마법사에서 **마침** 을 클릭해야 해당 파일이 선택한 위치에 저장됩니다.

   마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침** 을 클릭할 때 클래스 구현을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예** 를 클릭하여 파일을 추가하거나, **아니요** 를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.

## <a name="see-also"></a>참고 항목

[ATL 대화 상자](../../atl/reference/adding-an-atl-dialog-box.md)

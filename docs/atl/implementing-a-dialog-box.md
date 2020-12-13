---
description: '자세히 알아보기: 대화 상자 구현'
title: 대화 상자 구현
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 736619b39d06cffc28bc9723c94d0c5367dd51d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152912"
---
# <a name="implementing-a-dialog-box"></a>대화 상자 구현

Atl 프로젝트에 대화 상자를 추가 하는 방법에는 다음 두 가지가 있습니다. ATL 대화 상자 마법사를 사용 하거나 수동으로 추가 합니다.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>ATL 대화 상자 마법사를 사용 하 여 대화 상자 추가

[클래스 추가 대화 상자](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)에서 atl 대화 상자 개체를 선택 하 여 atl 프로젝트에 대화 상자를 추가 합니다. ATL 대화 상자 마법사를 적절 하 게 입력 하 고 **마침** 을 클릭 합니다. 마법사는 [Caxdialogimpl](../atl/reference/caxdialogimpl-class.md) 파생 된 클래스를 프로젝트에 추가 합니다. **보기** 메뉴에서 **리소스 뷰** 를 열고 대화 상자를 찾은 다음 두 번 클릭 하 여 리소스 편집기에서 엽니다.

> [!NOTE]
> 에서 파생 된 대화 상자는 `CAxDialogImpl` ActiveX 컨트롤과 Windows 컨트롤을 모두 호스팅할 수 있습니다. 대화 상자 클래스에서 ActiveX 컨트롤 지원의 오버 헤드를 원하지 않는 경우 대신 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 또는 [cdialogimpl](../atl/reference/cdialogimpl-class.md) 사용 됩니다.

클래스 뷰에서 대화 상자 클래스에 메시지 및 이벤트 처리기를 추가할 수 있습니다. 자세한 내용은 [ATL 메시지 처리기 추가](../atl/adding-an-atl-message-handler.md)를 참조 하세요.

## <a name="adding-a-dialog-box-manually"></a>수동으로 대화 상자 추가

대화 상자를 구현 하는 것은 창을 구현 하는 것과 비슷합니다. [Caxdialogimpl](../atl/reference/caxdialogimpl-class.md)나 [Cdialogimpl](../atl/reference/cdialogimpl-class.md)나 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 에서 클래스를 파생 시키고 메시지 [맵을](../atl/message-maps-atl.md) 선언 하 여 메시지를 처리 합니다. 그러나 파생 클래스에서 대화 상자 템플릿 리소스 ID도 지정 해야 합니다. 클래스에는 `IDD` 이 값을 보유 하기 위해 라는 데이터 멤버가 있어야 합니다.

> [!NOTE]
> ATL 대화 상자 마법사를 사용 하 여 대화 상자를 만들면 마법사에서 자동으로 `IDD` 멤버를 형식으로 추가 합니다 **`enum`** .

`CDialogImpl` Windows 컨트롤을 호스트 하는 모달 또는 모덜리스 대화 상자를 구현할 수 있습니다. `CAxDialogImpl` ActiveX 및 Windows 컨트롤을 모두 호스팅하는 모달 또는 모덜리스 대화 상자를 구현할 수 있습니다.

모달 대화 상자를 만들려면 `CDialogImpl` 파생 된 (또는 파생) 클래스의 인스턴스를 만든 `CAxDialogImpl` 다음 [DoModal](../atl/reference/cdialogimpl-class.md#domodal) 메서드를 호출 합니다. 모달 대화 상자를 닫으려면 메시지 처리기에서 [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) 메서드를 호출 합니다. 모덜리스 대화 상자를 만들려면 대신 [create](../atl/reference/cdialogimpl-class.md#create) 메서드를 호출 `DoModal` 합니다. 모덜리스 대화 상자를 제거 하려면 [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)를 호출 합니다.

이벤트 싱크는 [Caxdialogimpl](../atl/reference/caxdialogimpl-class.md)자동으로 수행 됩니다. 파생 클래스의 처리기와 마찬가지로 대화 상자의 메시지 처리기를 구현 `CWindowImpl` 합니다. 메시지 관련 반환 값이 있는 경우로 반환 `LRESULT` 합니다. 반환 된 `LRESULT` 값은 Windows 대화 상자 관리자에서 적절 하 게 처리 하기 위해 ATL에서 매핑됩니다. 자세한 내용은 [CDialogImplBaseT::D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) 의 소스 코드를 참조 하세요.

## <a name="example"></a>예제

다음 클래스는 대화 상자를 구현 합니다.

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>참고 항목

[창 클래스](../atl/atl-window-classes.md)

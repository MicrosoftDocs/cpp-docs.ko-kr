---
description: '자세히 알아보기: 탭 컨트롤 만들기'
title: 탭 컨트롤 만들기
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 38b50931f6ea922bb1166759a97dc676c604319a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309500"
---
# <a name="creating-the-tab-control"></a>탭 컨트롤 만들기

탭 컨트롤을 만드는 방법은 대화 상자에서 컨트롤을 사용 하는지 아니면 비 모달 창에서 컨트롤을 만드는 지에 따라 달라 집니다.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>대화 상자에서 직접 CTabCtrl를 사용 하려면

1. 대화 상자 편집기에서 대화 상자 템플릿 리소스에 탭 컨트롤을 추가 합니다. 해당 컨트롤 ID를 지정합니다.

1. [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md) 를 사용 하 여 컨트롤 속성으로 [ctabctrl](reference/ctabctrl-class.md) 형식의 멤버 변수를 추가 합니다. 이 멤버를 사용하여 `CTabCtrl` 멤버 함수를 호출할 수 있습니다.

1. 처리 해야 하는 모든 탭 컨트롤 알림 메시지에 대 한 대화 상자 클래스의 매핑 처리기 함수입니다. 자세한 내용은 [함수에 메시지 매핑](reference/mapping-messages-to-functions.md)을 참조 하세요.

1. [OnInitDialog](reference/cdialog-class.md#oninitdialog)에서에 대 한 스타일을 설정 합니다 `CTabCtrl` .

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>비 모달 창에서 CTabCtrl를 사용 하려면

1. 뷰 또는 창 클래스에서 컨트롤을 정의합니다.

1. 부모 창의 [OnCreate](reference/cwnd-class.md#oncreate) handler 함수 (컨트롤을 서브클래싱 하는 경우)의 초기에는 [oninitialupdate](reference/cview-class.md#oninitialupdate)에서 컨트롤의 [Create](reference/ctabctrl-class.md#create) 멤버 함수를 호출 합니다. 컨트롤의 스타일을 설정합니다.

개체를 `CTabCtrl` 만든 후에는 다음과 같은 확장 스타일을 설정 하거나 해제할 수 있습니다.

- **TCS_EX_FLATSEPARATORS** 탭 컨트롤은 탭 항목 사이에 구분 기호를 그립니다. 이 확장 스타일은 **TCS_BUTTONS** 및 **TCS_FLATBUTTONS** 스타일을 포함 하는 탭 컨트롤에만 영향을 줍니다. 기본적으로 **TCS_FLATBUTTONS** 스타일을 사용 하 여 탭 컨트롤을 만들면이 확장 스타일을 설정 합니다.

- **TCS_EX_REGISTERDROP** 탭 컨트롤은 개체를 컨트롤의 탭 항목 위로 끌 때 놓기 대상 개체를 요청 하는 **TCN_GETOBJECT** 알림 메시지를 생성 합니다.

    > [!NOTE]
    >  **TCN_GETOBJECT** 알림을 받으려면 [AfxOleInit](reference/ole-initialization.md#afxoleinit)를 호출 하 여 OLE 라이브러리를 초기화 해야 합니다.

이러한 스타일은 [Getextendedstyle](reference/ctabctrl-class.md#getextendedstyle) 및 [SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle) 멤버 함수를 각각 호출 하 여 컨트롤을 만든 후에 검색 하 고 설정할 수 있습니다.

예를 들어 다음 코드 줄을 사용 하 여 **TCS_EX_FLATSEPARATORS** 스타일을 설정 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

다음 코드 줄을 사용 하 여 개체에서 **TCS_EX_FLATSEPARATORS** 스타일을 지웁니다 `CTabCtrl` .

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

그러면 개체의 단추 사이에 표시 되는 구분 기호가 제거 됩니다 `CTabCtrl` .

## <a name="see-also"></a>참고 항목

[CTabCtrl 사용](using-ctabctrl.md)<br/>
[컨트롤](controls-mfc.md)

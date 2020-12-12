---
description: '자세히 알아보기: 모양, ATL 컨트롤 마법사'
title: 모양, ATL 컨트롤 마법사
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: f8ae2951249d7093eef7a32a7cde167aa359aa02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165565"
---
# <a name="appearance-atl-control-wizard"></a>모양, ATL 컨트롤 마법사

마법사의이 페이지를 사용 하 여 컨트롤의 추가 사용자 요소 옵션을 식별할 수 있습니다. 이 페이지는 [옵션, ATL 컨트롤 마법사](../../atl/reference/options-atl-control-wizard.md) 페이지의 **컨트롤 형식** 에서 **표준 컨트롤로** 식별 되는 컨트롤에 사용할 수 있습니다.

## <a name="uielement-list"></a>UI 요소 목록

- **상태 보기**

   컨테이너 내에서 컨트롤의 모양을 설정 합니다.

  - **불투명**: [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) 열거형의 VIEWSTATUS_OPAQUE 비트를 설정 하 고 [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) 메서드에 전달 된 전체 컨트롤 사각형을 그립니다. 컨트롤은 완전히 불투명 하 게 나타나고 컨테이너는 컨트롤 경계 뒤에 표시 되지 않습니다.

      이 설정을 사용 하면 컨테이너에서 컨트롤을 보다 신속 하 게 그릴 수 있습니다. 이 옵션을 선택 하지 않으면 컨트롤은 투명 한 부분을 포함할 수 있습니다.

      불투명 된 컨트롤에만 단색 배경을 사용할 수 있습니다.

  - **Solid Background**: VIEWSTATUS 열거에서 VIEWSTATUS_SOLIDBKGND 비트를 설정 합니다. 컨트롤의 배경은 패턴이 없는 단색으로 표시 됩니다.

      이 옵션은 **불투명** 옵션을 선택한 경우에만 사용할 수 있습니다.

- **컨트롤 추가 기준**

   컨트롤을 구현 하는 클래스에 [CContainedWindow](ccontainedwindowt-class.md) 데이터 멤버를 추가 하 여 Windows 컨트롤 형식을 기반으로 하는 컨트롤을 설정 합니다. 또한 컨트롤의 Windows 메시지를 처리 하는 메시지 맵과 메시지 처리기 함수도 추가 합니다. 목록에서 만들려는 Windows 컨트롤의 형식 (있는 경우)을 선택 합니다.

  - **단추**

  - **ListBox**

  - **SysAnimate32**

  - **SysListView32**

  - **ComboBox**

  - **RichEdit**

  - **SysDateTimePick32**

  - **SysMonthCal32**

  - **ComboBoxEx32**

  - **스크롤 막대**

  - **SysHeader32**

  - **SysTabControl32**

  - **편집**

  - **정적**

  - **SysIPAddress32**

  - **SysTreeView32**

- **기타 상태**

   컨트롤의 추가 모양 및 동작 옵션을 설정 합니다.

  - 런타임에 **숨김**: 런타임에 컨트롤이 표시 되지 않도록 설정 합니다. 표시 되지 않는 컨트롤을 사용 하 여 일정 한 간격으로 이벤트를 발생 시키는 것과 같이 백그라운드에서 작업을 수행할 수 있습니다.

  - **단추 처럼 동작**: [olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc) 열거형의 OLEMISC_ACTSLIKEBUTTON 비트를 설정 하 여 컨트롤이 단추 처럼 동작 하도록 합니다. 컨테이너에서 컨트롤의 클라이언트 사이트를 기본 단추로 표시 한 경우이 옵션을 선택 하면 단추 컨트롤이 자신을 더 굵은 프레임으로 그리기 때문에 기본 단추로 표시 됩니다. 자세한 내용은 [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) 를 참조 하세요.

  - **Label 처럼 동작**: OLEMISC 열거형의 OLEMISC_ACTSLIKELABEL 비트를 설정 하 여 컨트롤에서 컨테이너의 네이티브 레이블을 바꿀 수 있도록 합니다. 컨테이너는이 플래그를 사용 하 여 수행할 작업 (있는 경우)을 결정 합니다.

- **기타**

   컨트롤의 추가 동작 옵션을 설정 합니다.

  - **정규화 된 DC**: 자신을 그리기 위해 호출 될 때 정규화 된 장치 컨텍스트를 만들도록 컨트롤을 설정 합니다. 이 작업을 수행 하면 컨트롤의 모양이 표준화 되지만 그리기 효율성이 떨어집니다.

  - **창만**: 컨트롤을 창 없는으로 지정할 수 없도록 지정 합니다. 이 옵션을 선택 하지 않으면 컨트롤이 창 없는 개체를 지 원하는 컨테이너에서 자동으로 창이 표시 되지 않으며 창 없는 개체를 지원 하지 않는 컨테이너에서 자동으로 창이 표시 됩니다. 이 옵션을 선택 하면 창 없는 개체를 지 원하는 컨테이너에도 컨트롤이 창에 포함 됩니다.

  - **삽입 가능: Word** 및 Excel과 같은 응용 프로그램의 **개체 삽입** 대화 상자에 컨트롤을 표시 하려면이 옵션을 선택 합니다. 그러면이 대화 상자를 통해 포함 된 개체를 지 원하는 모든 응용 프로그램에서 컨트롤을 삽입할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ATL 컨트롤 마법사](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 샘플: 표준 Windows 컨트롤의 슈퍼](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

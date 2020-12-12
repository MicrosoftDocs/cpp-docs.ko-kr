---
description: '자세한 정보: 대화 상자 컨트롤 (c + +)'
title: 대화 상자 컨트롤 (c + +) | Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: e68547ebd550797d4ad195c6bef4c3f2a71e769e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327150"
---
# <a name="dialog-box-controls-c"></a>대화 상자 컨트롤 (c + +)

[도구 상자 창의](/visualstudio/ide/reference/toolbox) **대화 상자 편집기** 탭을 사용 하 여 대화 상자에 컨트롤을 추가 하 여 원하는 컨트롤을 선택 하 고 대화 상자에 끌어 놓을 수 있습니다. 기본적으로 **도구 상자** 창은 자동 숨기기로 설정 됩니다. **대화 상자 편집기** 가 열릴 때 솔루션의 왼쪽 여백에 탭으로 나타납니다. 그러나 창의 오른쪽 위 모퉁이에 있는 **자동 숨기기** 단추를 선택 하 여 **도구 상자** 창을 위치에 고정할 수 있습니다. 이 창의 동작을 제어 하는 방법에 대 한 자세한 내용은 [창 관리](/visualstudio/ide/customizing-window-layouts-in-visual-studio)를 참조 하세요.

대화 상자에 컨트롤을 추가 하거나, 기존 컨트롤의 위치를 변경 하거나, 컨트롤을 한 대화 상자에서 다른 대화 상자로 이동 하는 가장 빠른 방법은 끌어서 놓기 메서드를 사용 하는 것입니다. 컨트롤의 위치는 대화 상자에 놓을 때까지 점선으로 표시 됩니다. 끌어서 놓기 메서드를 사용 하 여 대화 상자에 컨트롤을 추가 하는 경우 컨트롤에는 해당 컨트롤 형식에 적합 한 표준 높이가 지정 됩니다.

대화 상자에 컨트롤을 추가 하거나 위치를 변경 하는 경우 최종 배치가 안내선 또는 여백에 따라 결정 되거나 레이아웃 눈금이 설정 되어 있는지 여부에 따라 결정 될 수 있습니다.

대화 상자에 컨트롤을 추가한 후에는 [속성 창](/visualstudio/ide/reference/properties-window)에서 해당 캡션과 같은 속성을 변경할 수 있습니다. 여러 개의 컨트롤을 선택 하 고 해당 속성을 한 번에 변경할 수도 있습니다.

**대화 상자 편집기** 에 대 한 자세한 내용은 컨트롤 [추가, 편집 또는 삭제](adding-editing-or-deleting-controls.md)방법, [레이아웃 컨트롤](../windows/arrangement-of-controls-on-dialog-boxes.md)및 [컨트롤 액세스 및 값 정의](../windows/defining-mnemonics-access-keys.md)를 참조 하세요.

컨트롤 및 대화 상자에 대 한 자세한 내용은 [컨트롤 클래스](../mfc/control-classes.md), [대화 상자 클래스](../mfc/dialog-box-classes.md)및 [스크롤 막대 스타일](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)을 참조 하세요.

기본 이벤트를 사용 하 여 **도구 상자** 에서 사용할 수 있는 표준 컨트롤은 다음과 같습니다.

|컨트롤 이름|기본 이벤트|
|---|---|
|[Button 컨트롤](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[확인란 컨트롤](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[콤보 상자 컨트롤](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[편집 컨트롤](../mfc/reference/cedit-class.md)|EN_CHANGE|
|그룹 상자|(해당 사항 없음)|
|[목록 상자 컨트롤](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[라디오 단추 컨트롤](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[정적 텍스트 컨트롤](../mfc/reference/cstatic-class.md)|(해당 사항 없음)|
|[그림 컨트롤](../mfc/reference/cpictureholder-class.md)|(해당 사항 없음)|
|[Rich Edit 2.0 컨트롤](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[스크롤 막대 컨트롤](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> MFC에서 **RichEdit 1.0** 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 Mfc 및 [Rich Edit 컨트롤 예제](../mfc/rich-edit-control-examples.md) [에 RichEdit 1.0 컨트롤 사용](./adding-editing-or-deleting-controls.md) 을 참조 하세요.

향상 된 기능을 제공 하기 위해 **도구 상자** 에서 사용할 수 있는 [Windows 공용 컨트롤](../mfc/controls-mfc.md) 은 다음과 같습니다.

|컨트롤 이름|기본 이벤트|
|---|---|
|[Slider 컨트롤](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Spin 컨트롤](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Progress 컨트롤](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Hot Key 컨트롤](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[목록 컨트롤](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[트리 컨트롤](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[탭 컨트롤](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[애니메이션 컨트롤](../mfc/using-an-animation-control.md)|ACN_START|
|[날짜 시간 선택 컨트롤](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[MonthCalendar 컨트롤](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP 주소 제어](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[확장된 콤보 상자 컨트롤](../mfc/creating-an-extended-combo-box-control.md)||
|사용자 지정 컨트롤|TTN_GETDISPINFO|

## <a name="custom-controls"></a>사용자 지정 컨트롤

**대화 상자 편집기** 를 사용 하 여 대화 상자 템플릿에서 기존 사용자 지정 컨트롤 또는 사용자 정의 컨트롤을 사용할 수 있습니다.

> [!NOTE]
> 이 의미의 사용자 지정 컨트롤은 ActiveX 컨트롤과 혼동 하지 않습니다. ActiveX 컨트롤을 OLE 사용자 지정 컨트롤 이라고 합니다. 또한 이러한 컨트롤을 Windows의 소유자가 그린 컨트롤과 혼동 하지 마세요.

이 기능은 Windows에서 제공 하는 컨트롤 이외의 컨트롤을 사용할 수 있도록 하기 위한 것입니다. 런타임에 컨트롤이 창 클래스와 연결 됩니다 (c + + 클래스와 동일 하지 않음). 동일한 작업을 수행 하는 일반적인 방법은 대화 상자에 정적 컨트롤과 같은 컨트롤을 설치 하는 것입니다. 그런 다음 런타임에 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 함수에서 해당 컨트롤을 제거 하 고 사용자 지정 컨트롤로 바꿉니다.

> [!NOTE]
> 이것은 이전 기술입니다. 현재 대부분의 경우 ActiveX 컨트롤을 작성 하거나 Windows 공용 컨트롤의 서브 클래스를 작성 하는 것이 좋습니다.

이러한 사용자 지정 컨트롤의 경우 다음으로 제한 됩니다.

- 대화 상자에서 위치를 설정 합니다.

- 캡션 입력.

- 응용 프로그램 코드가이 이름으로 컨트롤을 등록 해야 하므로 컨트롤의 Windows 클래스 이름을 식별 합니다.

- 컨트롤의 스타일을 설정 하는 32 비트 16 진수 값을 입력 합니다.

- 확장 스타일 설정

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 편집기](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](./adding-editing-or-deleting-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
